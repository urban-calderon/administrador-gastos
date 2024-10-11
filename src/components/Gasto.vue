<template>
  <div class="gasto sombra">
    <div class="contenido">
      <img
        :src="diccionarioIconos[gasto.categoria]"
        alt="Icono gasto"
        class="icono"
      />
      <div class="detalles">
        <p class="categoria">{{ gasto.categoria }}</p>
        <p class="nombre" @click="$emit('seleccionar-gasto', gasto.id)">
          {{ gasto.nombre }}
        </p>
        <p class="fecha">
          Fecha:
          <span>{{ formatearFecha(gasto.fecha) }}</span>
        </p>
      </div>
    </div>

    <p class="cantidad">{{ formatearCantidad(gasto.cantidad) }}</p>
    <button class="btn-delete" @click="$emit('eliminar-gasto', gasto.id)">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="icon icon-tabler icon-tabler-trash"
        width="28"
        height="28"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="#ffffff"
        fill="none"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path stroke="none" d="M0 0h24v24H0z" fill="none" />
        <path d="M4 7l16 0" />
        <path d="M10 11l0 6" />
        <path d="M14 11l0 6" />
        <path d="M5 7l1 12a2 2 0 0 0 2 2h8a2 2 0 0 0 2 -2l1 -12" />
        <path d="M9 7v-3a1 1 0 0 1 1 -1h4a1 1 0 0 1 1 1v3" />
      </svg>
    </button>
  </div>
</template>

<script setup>
import { formatearCantidad, formatearFecha } from "../helpers";
import IconoAhorro from "../assets/img/icono_ahorro.svg";
import IconoCasa from "../assets/img/icono_casa.svg";
import IconoComida from "../assets/img/icono_comida.svg";
import IconoGastos from "../assets/img/icono_gastos.svg";
import IconoOcio from "../assets/img/icono_ocio.svg";
import IconoSalud from "../assets/img/icono_salud.svg";
import IconoSuscripciones from "../assets/img/icono_suscripciones.svg";

const diccionarioIconos = {
  ahorro: IconoAhorro,
  comida: IconoComida,
  casa: IconoCasa,
  gastos: IconoGastos,
  ocio: IconoOcio,
  salud: IconoSalud,
  suscripciones: IconoSuscripciones,
};

defineEmits(["seleccionar-gasto", "eliminar-gasto"]);

const props = defineProps({
  gasto: {
    type: Object,
    required: true,
  },
});
</script>

<style scoped>
.gasto {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 2rem;
  flex-wrap: wrap;
}
.contenido {
  display: flex;
  align-items: center;
  gap: 2rem;
}
.icono {
  width: 5rem;
}
.detalles p {
  margin: 0 0 1rem 0;
}
.categoria {
  color: gray;
  font-size: 1.2rem;
  text-transform: uppercase;
  font-weight: 900;
}
.nombre {
  color: var(--gris-oscuro);
  font-size: 2.4rem;
  font-weight: 700;
  cursor: pointer;
}
.fecha {
  color: var(--gris-oscuro);
  font-size: 1.6rem;
  font-weight: 900;
}
.fecha span {
  font-weight: 400;
}
.cantidad {
  font-size: 3rem;
  font-weight: 900;
  margin: 0;
}

.btn-delete {
  background-color: red;
  border-radius: 0.8rem;
  border: none;
  padding: 8px;
  cursor: pointer;
}

.btn-delete:hover {
  background-color: #e74c3c;
  transition: background-color 300ms ease;
}
</style>

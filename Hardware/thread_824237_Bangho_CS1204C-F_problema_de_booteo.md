---
title: "Bangho CS1204C-F problema de booteo"
date: 2008-06-09
forum: Hardware
---

### Post by meliascosta on 2008-06-09
Hola! Instale ubuntu 8.04 en esta laptop bang ho pero la unica manera de acerlo andar es agregando noapic nolapic acpi=off irqpoll en el booteo, con lo cual no hace correctamente el manejo de energia (no se ve la bateria y no apaga) trate de cambiar de ACPI a APM como sugerian en algunos foros sin exito... El BIOS es phoenix 1.004 aparenemente este bios es bastante poco amigable con linux... a alguno le paso esto o se le ocurre alguna manera de solucionarlo? El resto parece andar bien wifi, USB, audio, etc... lo unico que no logro configurar es la placa de video sis 671/771 encontre los drivers para 8.04 pero no le gustan no se por que... En fin, muchas gracias!

---

### Post by faktorqm on 2008-06-10
Hola, yo probaria con combinaciones alternas, por ejemplo noapic irqpoll, o nolapic irqpoll. No se para que sirve el irqpoll, pero tambien podes probar de ir poniendo de a uno a ver que pasa, hasta encontrar la mejor combinacion. Salu2!

---

### Post by atari130xe on 2008-06-10
> **faktorqm said:**
> Hola, yo probaria con combinaciones alternas, por ejemplo noapic irqpoll, o nolapic irqpoll. No se para que sirve el irqpoll, pero tambien podes probar de ir poniendo de a uno a ver que pasa, hasta encontrar la mejor combinacion. Salu2!

la opción irqpoll sirve para que si una interrupción no es manejada por nadie le encuentre algun lugar en la vida. Básicamente arregla algunos problemas de firmware. acpi=force, es bastante autoexplicativo.

fuente: [http://www.nictuku.com.ar/blog/es/2007/09/04/instalando-ubuntu-en-una-thinkpad-1161/]("http://www.nictuku.com.ar/blog/es/2007/09/04/instalando-ubuntu-en-una-thinkpad-1161/")
:)

---


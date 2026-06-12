---
title: "problema rtl 8185"
date: 2009-11-11
forum: Hardware
---

### Post by totolinux on 2009-11-11
Hola a todos: Tengo un problema con una placa encore wifi rtl8185 que dejo de funcionar desde ubuntu 8.10 el problema concreto es que no arranca ni el sistema instaldo y ningun livecd  de otras distros desde supongo el kernel que traen por defecto. Se cuelgan en el inicio. 
No tube más remedio que quitarla desde la ranura pci para poder instalar 9.04 y luego actualizar a 9.10 pero si la vuelvo a conectar se cuelga, aclaro que mi pc arranca con la opción noapic.
datos.
amd sempron 1400 mhs
ram 512
nvidia 128 fx5500
dos placas eth
me gustaría poder usarla para compartir internet en una red ad hoc.
desde ya muchas gracias..

---

### Post by luks911 on 2009-11-11
No sé si servirá, pero instalando el paquete linux-backports-modules-karmic se van a instalar algunos módulos para el kernel, creo que uno de ellos es para ese chip. Podés probar de instalarlo, a ver qué pasa.

---

### Post by totolinux on 2009-11-12
pruebo y te cuento gracias

---

### Post by totolinux on 2009-11-12
No funciona, esperaré alguna otra ayuda. Gracias igual.

---

### Post by luks911 on 2009-11-12
Estaba viendo que la placa, bah ese chip realtek, está soportada. Además me llama la atención el hecho de que el problema se repita con otras distros (lo que implica distintos kernels), no soy un experto pero ¿no habrá alguna clase de conflicto con el slot pci que usa? ¿Tenés posibilidad de probarla en otro? ¿Pudiste ver si da algún mensaje cuando se cuelga?

---

### Post by totolinux on 2009-11-12
si, Es igual si cambio de slot.
Cuando prendo la pc pasa el grub luego queda la pantalla en negro.
Cuando uso livecd viejos como ubuntu 8.04 arranca luego hay que instalar el driver de win y anda joya.
Para mi debe andar el tema por algun módulo que habrá que poner en lista negra. Por ese lado.

---

### Post by totolinux on 2009-11-14
bueno. pude hacer arrancar el sistemna así

$sudo gedit /etc/modprobe.d/blacklist.conf
 
luego agregar 

# pasa a lista negra los sig. módulos rtl
blacklist r818x
blacklist r8187

luego apagar el pc colocar la placa y iniciar.
 
bueno ahora tengo que hacerla andar, luego comento como lo hice.

---

### Post by chulelinux on 2009-11-14
Hola que tal.... 
te anduvo así con blacklist???? Yo le dí veinte mil vueltas y el único modo estable que logré fue con ndiswrapper cargando el controlador para xp bajado de la página de realtek... 
Te lo comento por las dudas que te sirva porque el tema me hizo dar muchas vueltas.

Saludos

---

### Post by totolinux on 2009-11-15
de esta manera pudo arrancar el sistema. pero no la he podido hacer andar. Antes si la usaba con el driver de xp. estoy pensando seriamente en tirarla a la basura jajaja. no vale la pena.

---


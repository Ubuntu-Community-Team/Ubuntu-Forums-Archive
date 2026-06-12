---
title: "imposible instalar ubuntu 9.04 (hasta probar lo contrario)"
date: 2009-10-19
forum: Instalación y Actualización
---

### Post by danny.woodstock on 2009-10-19
hola amigos del foro,
tiempo sin entrar al foro, pero me veo necesitado, ayer mi hno,
adquirio un toshiba satellite L305-sp6944c
y me pidio que le instalace ubuntu, probe con mi cd de ubunut 9.04 primero como live cd, tan solo para probar y ver que hardware no reconocia, y me paso algo muy extraño, 
la session Live User carga bien, y bueno llego y en el escritorio lo unico que puedo hacer es mover el mouse, nada mas...
cuando hago click en Aplicaciones, o Sistema, o Lugares no pasa nada,
si quiero cambiar de Area de trabajo tampoco, si quiero abrir la papelera tampoco, solo puedo mover el mouse y entretenerme moviendo el mouse hasta que me de un ataque de epilepsia por moverlo tan rapido, bueno la cosa esque dije: aolomejor fue un un simple error, no pasara nuevamente, y decidi ahora darle a la opcion Instalar Ubuntu en el equipo, saltandome la opcion probar sin alterar, y resulta que neuvamente carga todo bien, y llego a la primera opcion de instalacion donde debemos elegir el idioma, y darle clicka Siguiente para pasar a localidad y etc, ect
la cosa esque nuevamente me encuentro con que solo puedo mover el mouse! y nada mas!!! no toma nada de nada.. hago click en SIguiente y no pasa nada!...
no c que hacer :s y tampoco s eme ocurre porque sucedera ese problema, no creo que sea por el driver de video o si? alguna idea de porque? alguien ha podido instalar ubuntu en este modelod e portatil? he buscado info en la internet, pero todo en ingles :S
y yo soy ñurdo pal pikinikli!.

el modelo del portatil como les dije es un: toshiba satellite L305-sp6944c

Se agradece su ayuda!

---

### Post by maxmoraga on 2009-10-21
porque no intentas ver si te ocurre lo mismo con los liveCD de otras distros ([Linux Mint]("http://www.linuxmint.com/download.php"), [openSuse]("http://software.opensuse.org/"), o kizas [Kubuntu]("http://www.kubuntu.org/getkubuntu/download") y muchas más)?

Saludos:P

---

### Post by moreback on 2009-10-21
¿probaste cambiando el mouse por otro de diferente modelo?

---

### Post by pornee on 2009-10-21
verificaste haber si la version es de 32 bit o 64bit?

---

### Post by danny.woodstock on 2009-10-21
hola gracias por sus respuestas, 
bueno probé con el live cd de debian lenny y me ocurrio lo mismo, en realidad no exacatamente porke pude hacer click en algun menu, pero despues de esom que de en la misma situacion anterior, solo podia mover el mouse, 
. segundo, no e sproblema d emouse, probe, y ninguno esta fallado.

el cd de ubuntu es el original que envian a la casa, de ubuntu 9.04
y esd e 32 bits-

---

### Post by moreback on 2009-10-21
Si no es el mouse debe ser algo con el X.org, pero ni idea que cosa sería, habría que revisar el /var/log/Xorg.0.log

Lo otro es seleccionar al inicio el modo seguro de video (hay que pulsar F4 cuando salen las opciones del livecd).

Saludos.

---

### Post by danny.woodstock on 2009-10-22
bueno, logre instalar ubuntu, pero fue despues de varios intentos, ya que seguia con el mismo problema, la cosa es que una vez instalado me paso lo mismo, me funciono un par de horas el ekipo con el SO instalado, ya que despues volvi a lo mismo, solo podia mover el mouse y no podia hacer clik en nada...
insisto... no creo que sea el mouse, he probado con el mismo tpouchpad del portatil y he probado con 3 mouses mas via usb! :s

---


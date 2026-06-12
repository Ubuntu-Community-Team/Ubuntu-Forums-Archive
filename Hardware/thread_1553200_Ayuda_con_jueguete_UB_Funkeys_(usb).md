---
title: "Ayuda con jueguete UB Funkeys (usb)"
date: 2010-08-14
forum: Hardware
---

### Post by mvp.libre on 2010-08-14
Estimad@s,

¿Por casualidad algun@ ha tratado de instala un UB Funkeys en linux (ubuntu 10.04)?

Son unos juguetes que vienen con un conector usb, al parecer tienen una llave.

El  asunto es que hay que instalar un programa o driver de win$. Lo intenté  con wine y cossover (game), pero no he logrado instalar "el mono".

En un foro mencionaban que se podía instalar en una máquina  virtual... pero para eso tendría que tener un win$, que no es el caso...

Escribí a Mattel (España), por lo menos para dejar constancia... pero no han respondido...

Espero que alguien pueda dar alguna luz al respecto.

Saludos y gracias.

---

### Post by Carlos C on 2010-08-15
Al parecer no es posible hacerlo funcionar mediante Wine,  por lo tanto la única posibilidad que queda es Virtualbox.

Saludos.

---

### Post by rjmb on 2010-09-20
Yo no he logrado hacer que WINE reconozca el archivo de SETUP.EXE

Tambien trate de activarlo en una maquina virtual usando VirtualBox 3.2, sobre una instancia de Linux Mint Isidora (Ubuntu Karmic Koala)

Aun cuando el proceso de instalación arranca bien...  en el proceso solicita se instale la consola del Juego....  y como diria Cantiflas "alli esta el detalle", ya que no logro que la maquina virtual de XP reconozca el uso del USB...  No solo la consola, tampoco logro que pueda montar un USB de almacanamiento.

---

### Post by themasterdark on 2010-09-20
Hola! 

No se si les será de ayuda, pero puedes hacer algo para que reconozca tu dispositivo usb la maquina virtual.

Antes de echarla a andar (iniciar) el sistema que tienes en virtualbox, puedes entrar a configuració -> usb -> agregar filtro de dispositivo (tienes que tener ya conectado el dispositivo usb).

Y bueno luego de esto correr el sistema de la maquina virtual (virtual box en este caso).

Espero te ayude =)

PD: de esta forma yo conecte para probar porque windows ya no lo uso una webcam, y un celular jajaja y si funciona.

---


---
title: "Problemas de Video"
date: 2010-10-01
forum: Hardware
---

### Post by jawifi01 on 2010-10-01
Buenas noches, no se si es correcto el asunto de este correo. Les explico: tengo un Pentium III al que le instalé Ubuntu Lucid Linx Alternate 10.04.1, con la opción de instalar un sistema de consola.

Es un equipo que voy a usar para pruebas y no me sirve tener entono grafico. El problema está en que no solo no tengo entorno de las X, sino que no tengo ¡nada!, es decir prendo la pc, hace todo el booteo pero no aparece nada en pantalla. Toda la instalación la hice viendo todo, pero despues del reinicio no se ve mas nada.

Si puedo entrar por ssh, por lo que deduzco que debe ser un problema de drivers.

La salida de lspci es:

~# lspci |grep VGA
00:0f.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200 AGP (rev 03)

El asunto es que tiene dos placas, ya que una es integrada y la otra (la nvidia) es la que quiero usar. No encuentro la forma de hacerla andar.

creo que puse todos los datos necesarios, si alguien me pueda dar algo de luz, le agradezco.

Saludos

Juan

---

### Post by KistIndigo on 2010-10-02
Hola amigo, te cuento que yo tambien tengo la GeForce 2 MX400. En mi caso funcionó perfectamente. Es probable que tu problema sea el hecho de que no desactivaste la placa onboard desde la BIOS. (Cuando presionas *supr* al iniciar la PC).
En mi caso, yo ya la habia desactivado al instalar Ubuntu Lucid, el cual instalé booteando desde un pendrive. Al entrar a Linux tenia instalado los drivers "predeterminados" y le instale los nuevos a traves de el programa **envy**.
Espero haberte ayudado.

---

### Post by jawifi01 on 2010-10-03
Gracias por tu respuesta, pero no, no es ese el problema, ya que esta desactivada en el BIOS la opcion de la placa integrada y puesta como primera opcion de placa de video la conectada al PCI, que es la placa nvidia. Lo que hice fue instalar KArmic y anduvo, despues vere de actualizar o no la distro.

Gracias

---

### Post by jawifi01 on 2010-10-03
Gracias por tu respuesta, pero no, no es ese el problema, ya que esta desactivada en el BIOS la opcion de la placa integrada y puesta como primera opcion de placa de video la conectada al PCI, que es la placa nvidia. Lo que hice fue instalar KArmic y anduvo, despues vere de actualizar o no la distro.

Gracias

---


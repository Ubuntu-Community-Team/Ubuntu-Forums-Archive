---
title: "hardware"
date: 2009-02-01
forum: Hardware
---

### Post by filtro_tuc on 2009-02-01
Hola a todos
Quiero compartir mi experiencia en cuanto al hardware que he adquirido y que funciona perfectamente con Ubuntu 8.04

Por empezar tengo una PC HP pavilion a1700n que viene con:
- procesador AMD Athlon 64 X2 3800+ 2.0 GHz Dual Core
- Video NVIDIA GeForce 6150 LE
- Motherboard ASUS A8M2N-LA
- Placa de sonido integrada Realtek ALC 888 chipset
- 250 GB SATA que expandi con otro disco de 500 GB
- 4 GB memoria ram Kington
- Teclado y mouse inalambricos Microsoft wireless optical desktop 1000
- Parlantes Creative Inspire P7800
- Webcam Genius Look 312p (el perrito)
- Placa sintonizadora Kozumi KTV-01C

Todo funciona excelente, sin necesidad de instalar algo especial.
Los parlantes tuve que cambiar el archivo /etc/pulse/daemon.conf segun el instructivo [http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/]("http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/")
y para probar que los parlantes funcionaran correctamente use el comando
***speaker-test -Dplug:surround71 -c8 -l1 -twav***

Para el teclado elegi en el modelo "Microsoft Wireless Multimedia Kayboard 1.0A y en Layouts Latin American.

La placa sintonizadora hice el archivo kozumi.sh que contiene
[I]rmmod bt878
rmmod bttv
rmmod tuner
modprobe bttv pll=1 radio=1 bttv_verbose=1 card=51 tuner=38 gbuffers=4
[/I]
Este archivo lo grabe en /etc/init.d
Luego ejecute en el terminal
*sudo cp -s /etc/init.d/Kozumi.sh /etc/rcS.d/S42Kozumi*
La radio no me funciona, pero es cuestion de buscar cual es el parametro adecuado para el sintonizador.

Bueno espero les sirva para cuando quieran adquirir alguno de los periféricos que he nombrado.
Saludos

---


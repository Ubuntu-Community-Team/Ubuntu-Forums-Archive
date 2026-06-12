---
title: "Sonido que desaparece en mi ubuntu"
date: 2009-09-08
forum: Hardware
---

### Post by Skoll on 2009-09-08
Pues eso, mi sonido iba genial pero de un dia para otro a desaparecido, y no logro encontrar el motivo, e googleado hasta el infinito pero ninguna solucion me vale. 
He comprobado que ningun valor en el alsamixer este en mute, pero nada >_< 

Mis datos 

#### javi@javi-desktop:~$ alsamixer 
&#9474; Card: HDA VIA VT82xx &#9474; 
&#9474; Chip: VIA VIA VT1708 &#9474; 
&#9474; View: [Playback] Capture All &#9474; 
&#9474; Item: Master Front [dB gain=14.00, 14.00] 




#### javi@javi-desktop:~$ aplay -l 
**** Lista de PLAYBACK Dispositivos Hardware **** 
tarjeta 0: VT82xx [HDA VIA VT82xx], dispositivo 0: VT1708 Analog [VT1708 Analog] 
Subdispositivos: 1/1 
Subdispositivo #0: subdevice #0 
tarjeta 0: VT82xx [HDA VIA VT82xx], dispositivo 1: VT1708 Digital [VT1708 Digital] 
Subdispositivos: 1/1 
Subdispositivo #0: subdevice # 


Espero que alguien pueda ayudarme, esto desesperadooo  =(

---

### Post by AlexDDR on 2009-09-08
primero en alsamixer prueba subiendo todos los volumenes y probando

luego si eso no funciona en el contro de sonido que esta al lado del reloj en las pestañas conmutadores y opciones anda probando las opciones y cambiando el independient HP(on/OFF) y esos del IEC

te dejo un pantallazo para que veas

saludos

---

### Post by Skoll on 2009-09-09
Todo comprobado, y todo correcto, pero sigue sin sonar =(

---

### Post by themasterdark on 2009-09-22
Podrias intentar que alsa la detecte nuevamente y probar si eso funciona, utiliza en un terminal
 
------------------------------
sudo alsaconf 
------------------------------

y sigues los pasos. Si estas en jaunty (que no viene por defecto en el paquete alsa-utils, el ejecutable de alsaconf, no se si alguna otra version no lo trae)

aqui esta el link de donde bajarlo.

[http://www.box.net/shared/apx8nme80s](http://www.box.net/shared/apx8nme80s)

desde ahi solo resta ir a la carpeta donde lo bajaste en un terminal y escribir:

---------------------------
chmod +x alsaconf 
---------------------------

y luego:

-------------------------
sudo ./alsaconf
--------------------------


saludos espero se soluciones tu problema

---


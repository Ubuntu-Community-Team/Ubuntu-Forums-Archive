---
title: "Ubuntu Sobrecalienta Microprocesador"
date: 2010-10-10
forum: Hardware
---

### Post by krlos07 on 2010-10-10
Hola amigos del foro yo instale ubuntu ubuntu-10.04.1-desktop-i386 en una laptop toshiba u505. Pasa que despues de cierto tiempo el microprocesador se sobrecalienta de una manera impresionante como si el abanico no funcionara. Sin embargo con windows 7 el micro no se calienta y el abanico anda bien. 

Yo ya actualice las BIOS y tambien actualice el kernel [http://new.taringa.net/posts/linux/5522069/Actualiza-al-Kernel-2_6_34-Ubuntu-10_04.html](http://new.taringa.net/posts/linux/5522069/Actualiza-al-Kernel-2_6_34-Ubuntu-10_04.html) pero nada de eso me funciona si alguien conoce de este problema les agradeceria me ayudaran muchas gracias.

---

### Post by Dark_Stang on 2010-10-10
Parece que el procesador no es downclocking. Trate de instalar el paquete "powernowd" y reiniciar, a ver si eso ayuda.

Lo sentimos, utilizando Google Translate. No pude aprender español en la escuela secundaria.

---

### Post by krlos07 on 2010-10-11
> **Dark_Stang said:**
> Parece que el procesador no es downclocking. Trate de instalar el paquete "powernowd" y reiniciar, a ver si eso ayuda.


Hola hice la instalacion del paquete powernowd con apt-get install powernowd reinicie el computador y aun sigue calentandose el microprocesador.
 Que otra cosa puedo hacer.

---

### Post by krlos07 on 2010-10-11
> **krlos07 said:**
> Hola hice la instalacion del paquete powernowd con apt-get install powernowd reinicie el computador y aun sigue calentandose el microprocesador.
 Que otra cosa puedo hacer.

Ya logre arreglar el problema aqui la respuesta para el que tenga el mismo problema 

  	 	 	 	 	 	  Fan Issues  The first thing you may notice about the machine is that the wrist rest gets really hot and the fan doesn't seem to be running. Apparently, there are issues with this particular  BIOS and version of ACPI, which doesn't turn the fan on. There supposedly is a thermocouple that will force the fan on at a critical temperature,  but you will not want to test that feature very often.  None of the fixes given in various forum threads ( 1, 2, 3, 4, 5, 6) seemed to work for me and it looks like this is something that will just  have to wait for another release. The sensors-detect program finds the "EDID EEPROM" with a Intel Core family thermal sensor, but installing  the suggested coretemp driver didn't do anything for me.  The nasty workaround is to simply suspend and reawaken the machine once it starts getting warm:  	sudo pm-suspend The BIOS apparently feels the heat on reawakening and turns the fan on. It stays on, but that allows you to continue to stay cool.  You can check the temperature with the "sensors" command, with the -f option giving readouts in Farenheit for Americans who haven't  caught up with the rest of the planet.  	sensors -f  	acpitz-virtual-0 	Adapter: Virtual device 	temp1:      +109.4°F  (crit = +226.4°F)                    	coretemp-isa-0000 	Adapter: ISA adapter 	Core 0:      +84.2°F  (high = +185.0°F, crit = +185.0°F)    	coretemp-isa-0001 	Adapter: ISA adapter 	Core 1:      +84.2°F  (high = +185.0°F, crit = +185.0°F)  

saludos y muchas gracias

---


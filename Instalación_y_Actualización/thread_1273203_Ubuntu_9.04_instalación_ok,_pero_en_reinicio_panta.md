---
title: "Ubuntu 9.04 instalación ok, pero en reinicio pantalla negra"
date: 2009-09-23
forum: Instalación y Actualización
---

### Post by soscomo on 2009-09-23
hOLA, tengo un portatil packardbell buterefly, es el mismo modelo que el acer timeline 3810, solo cambia la carcasa, he instalado ubuntu 9.04 y se instala ok, reinicio y ya no carga el so, sale el icono de buntu y luego pantallazo negro, funciona el control + alt + su, osea que pienso que es problema de la gráfica, pero tampoco entiendo mucho.
 
Con el live cd funciona perfectamente, he conseguido arrancarlo en modo recovery pero en mitad de la carga tengo que salirmo con el comando exit, reinicia la carga y al rato tengo que insertar starx y después sale una pantalla de recuperación le doy a normal root y ya arranca, pero no consigo que arranque en modo normla, siempre la pantalla negra, he probado a actualizar y sigue el mismo problema, 
 
la carga en modo recovery se para siempre en un comando de sd(1.0.0.0) o algo así
 
 
Mi equipo:
Ficha Técnica[IMG]http://www.elcorteingles.es/informatica/elementos/transparente.gif[/IMG]**Marca: **Packard Bell 
**Procesador: **Intel Core 2 Duo SU9400 
**Velocidad del Procesador: **1,4 GHz. 
**Memoria RAM: **4096 MB.
**Tipo de memoria RAM: **DDR3 
**Disco Duro: **500 GB.
**Controladora Disco Duro: **SATA 
**Unidad Óptica: **Externa DVD Supermulti SATA 
**Tarjeta Gráfica: **ATI Mobility Radeon HD4330, 512 MB de memoria dedicada y hasta 1791 MB Turbocache de memoria máxima 
**Audio: **
- Tarjeta Realtek ALC269X-GR 
- Altavoces Stereo / Dolby Sound Room 
- Micrófono 
**Tarjeta de Red: **LAN Ethernet 10/100/1000 
**Conexiones inalámbricas: **
- WLAN 802.11 a/g/n
- Bluetooth 
**Tipo de Batería: **Li-Ion 6 celdas 
**Dispositivos Entrada / Salida: **
- 3 x USB 2.0 
- Salida VGA D-Sub 
- Salida Video HDMI (HDCP) 
- Salida Stereo/SPDIF 
- Entrada Micrófono 
- Lector de Tarjetas 5 in 1 (SD/MMC/MS/MS-Pro/xD) 
**Tamaño de Pantalla: **13,3" 
**Tipo de Pantalla: **WXGA LED GLARE, Full HD 1080p, via HDMI 
**Resolución máxima: **1366 x 768 ppp 
**Tipo de Teclado: **Standard 
**Tipo de Ratón: **Touchpad Multitouch 
**Dimensiones: **322 x 228 x 27,8 mm
**Peso: **1,8 KG
**Alimentación: **Adaptador 65 W 

 
 
¿alguna solución? gracias

---

### Post by Carlos C on 2009-09-23
> después sale una pantalla de recuperación le doy a normal root y ya arranca ¿Eso sognifica que finalmente consigues que parta el entorno gráfico? Puede ser un problema con el control de energía del equipo. Prueba desde el LiveCd apretando F6 (Otras opciones), y agregas los parámetros siguientes para que el kernel los considere durante la instalación:
```
noapic nolapic
```Con eso desactivas el controlador de interrupciones. Si no se arregla puedes agregar:
```
acpi=off
```Tendrás que olvidarte de cosas como hibernar, pero nada que sea tan terrible, creo yo. Por último si ambas no funcionan puedes probarlas juntas:
```
noapic nolapic acpi=off
```No aseguro que se resuelva, pero no pierdes nada con probar.
Saludos.

---

### Post by soscomo on 2009-09-23
> **Carlos C said:**
> ¿Eso sognifica que finalmente consigues que parta el entorno gráfico? Puede ser un problema con el control de energía del equipo. Prueba desde el LiveCd apretando F6 (Otras opciones), y agregas los parámetros siguientes para que el kernel los considere durante la instalación:
```
noapic nolapic
```Con eso desactivas el controlador de interrupciones. Si no se arregla puedes agregar:
```
acpi=off
```Tendrás que olvidarte de cosas como hibernar, pero nada que sea tan terrible, creo yo. Por último si ambas no funcionan puedes probarlas juntas:
```
noapic nolapic acpi=off
```No aseguro que se resuelva, pero no pierdes nada con probar.
Saludos.
  efectivamente ahora te contesto desde el entorno gráfico, es decir en el live cd arranca sin problemas, pero en el instalado me da los problemas que he comentado, en concreto he apuntado y al iniciar en modo rcovery se para en el punto 150.305696 sd 1.0.0.0 y dice doesn support DPO or FUA, ahi le doy a exit, sigue el proceso y en el punto 182.305675 sd 1.0.0.0 y dice lo mismo, ahí le doy a startx y sigue el proceso hasta que aparece el login y entro sin ningún problema, ahora intento lo que me comentas, si no entiendo mal reinstalo desde  el live cd poniendo prviamente los comandos que me dices, ¿cierto?

---

### Post by Carlos C on 2009-09-23
Entonces no va por ahí la cosa.
DPO: Disable Page Out. Indica al disco duro que el dato que se escribe no se volverá a leer pronto y no es necesario guardarlo en caché.
 FUA: Force Unit Access. Obliga a escribir directamente, no almacenar el dato en caché.

Creo que el problema es con el controlador sata.

---

### Post by soscomo on 2009-09-23
> **Carlos C said:**
> Entonces no va por ahí la cosa.
DPO: Disable Page Out. Indica al disco duro que el dato que se escribe no se volverá a leer pronto y no es necesario guardarlo en caché.
 FUA: Force Unit Access. Obliga a escribir directamente, no almacenar el dato en caché.

Creo que el problema es con el controlador sata.

Y eso como lo cambio?????
más datos, cuando se para la primera vez el modo seguro, al darle a exit sale: cargando /scrips/ini-bottom, comienza otro proceso medianamente largo y al final sle done, y después le doy a startx y sale el modo recovery y dandole a la primera opción ya inicia correctamente al login, me estoy volviendo loco, gracias por la ayuda que me puedan prestar, ciao

---

### Post by moreback on 2009-09-24
Me huele a disco pronto a morir.

---

### Post by soscomo on 2009-09-24
> **moreback said:**
> Me huele a disco pronto a morir.
 No me digas eso¡¡¡¡ el portatil tiene 2 meses.
 
Es logico que sea algo de incompatibilidad con el disco duro porque el live cd funciona la primera a la perfección, ayer busque un buen rato a ver como podía cambair el controlador a ver si así lo solucionaba pero no encontré nada, alguna solución?

---

### Post by Carlos C on 2009-09-24
Esas cosas se modifican a nivel de BIOS. En el BIOS encuentras la opción para configurar ese tipo de controladores. En general se entra al BIOS apretando F2 o Supr. cuando enciendes la máquina, antes de que empiece la carga del sistema operativo.

---

### Post by soscomo on 2009-09-24
> **Carlos C said:**
> Esas cosas se modifican a nivel de BIOS. En el BIOS encuentras la opción para configurar ese tipo de controladores. En general se entra al BIOS apretando F2 o Supr. cuando enciendes la máquina, antes de que empiece la carga del sistema operativo.
ok, en la bios, ayer entré pero no vi opción de controlador miraré detenidamente, gracias otra vez, ciao

---

### Post by soscomo on 2009-09-24
Si señor, eso era, he cambiado a IDE el controlador SATA y arranca en 30 segundos y todo ok en Ubuntu.
 
Pero ahora no me carga el vista, si dejo IDE arranca bien ubuntu pero no Vista, si vuelvo a AHCI no arranca Ubuntu, hay manera de que cada vez se elija una o de que se hagan compatible alguno de lso dos sistemas operativos con el otro controlador??? gracias
Hay manera de meter en ubuntu las ordenes adecuadas para que arranque en ahci?? he leido que si soporta ese controlador, pero no he visto como hacer que funcione en mi portatil.
 
Resumo lo que tengo por verdad:
Mi portatil venia con vista instalado en controlador ahci, si lo cambio, pierdo el arranque en vista.
Ubuntu en teoria si soporta ahci, pero no me deja arrancar con este controlador.
 
¿alguna idea?

---

### Post by moreback on 2009-09-25
No creo que sea lo de AHCI, tiene que ser alguna opción dentro de esas que habilitan IDE y cosas raras lo que esté causando los problemas.

Me pasó ayer en la oficina que había una opción de esas que parecen inocentes y que hacía que el GRUB me diera un error 25.

Sigue buscando en la BIOS, creo que por ahí va la cosa.

Saludos.

---

### Post by soscomo on 2009-09-25
> **moreback said:**
> No creo que sea lo de AHCI, tiene que ser alguna opción dentro de esas que habilitan IDE y cosas raras lo que esté causando los problemas.
 
Me pasó ayer en la oficina que había una opción de esas que parecen inocentes y que hacía que el GRUB me diera un error 25.
 
Sigue buscando en la BIOS, creo que por ahí va la cosa.
 
Saludos.
 Si, está claro, porque cambiando el controlador a IDE arranca perfectamente ubuntu, el problema es que el meu d emi bios es muy sencillo y tan solo hay esa opción relativa al controlador, el resto son de la gestión de wake on lan y del boot, no da más opciones, he leido qeu otras bios dejan una tercera opción "RAID" pero la mia no lo trae he estado buscando posibles actualizaciones de bios, para ver si traen más opciones y no la hay, el de julio de este año, asi que nada seguiré trasteando a ver que saco n claro, a malas me cargo el vista, que creo que no voy a volver a usarlo y lo uso desde vware, o directamente instalo w7.
¿sabéis si w7 necesita obligatoriamente AHCI?? es por poner w7 y así dejar el controlador IDE fijo, de mommento cuando entro a vista cambio el controlador y cuando entro a UBUNtu vuelvo a IDE, de todos modos si alguein sabe algo concreto de como permitir a UBUNtu arrancar en AHCI.
 
Ayer tambien probé a reinstalar ubutu en lugar de hacerlo con el controlador AHCI, cambiandolo a IDE e instalandolo desde el live usb, y hoy probaré a instalarlo desde una imagen que no sea live cd, es decir solo instalador cargandolo desde el boot inicial dese  el usb(es que mi portatil no tiene lector de cd...
 
Gracias por todos los comentarios y serán bien recibidas nuevas propuestas de soluciones, ciao

---


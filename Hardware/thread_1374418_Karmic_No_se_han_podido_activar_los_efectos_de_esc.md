---
title: "Karmic No se han podido activar los efectos de escritorio"
date: 2010-01-06
forum: Hardware
---

### Post by Arabela on 2010-01-06
Hola linuxeros, como estan? Les cuento que sigo el foro hace un tiempo, desde que decidi instalar el Jaunty y me ha venido siempre muy bien con todas las soluciones que he encontrado por eso infinitamente agradecida!


 Hoy me he tomado el dia en busca de soluciones para el problema en la activacion de la apariencia de mi Ubuntu, llevo varias, muchas, horas paseando de foro en foro, de blog en blog, pero ninguna de las soluciones que he encontrado me ha llevado a resolver la personalización de mi escritorio. 



 Comento: Tengo el compiz correctamente actualizado, mi placa de video correctamente instalada y con el rendering en Yes, pero evidentemente algo falla.
Lejos de ser una experta en el tema pero bastante cerca de lo intuitivo, puedo darme cuenta que hay algo que no esta conectando una cosa con la otra y ahi es donde pido Socorro!!
 

Sugerencias?
 

Gracias y buen año para tod@s!
 

Arabela
 
*Casi casi un Koala feliz*

---

### Post by luks911 on 2010-01-06
Pasanos el resultado del comando lspci para ver qué placa de video es, a ver si con esos datos aparece alguna idea.
En principio, es raro que teniendo la aceleración activada compiz no funcione. Pero también sucedía que tenía algunas placas intel en un blacklist, aunque creo que eso se arregló. En fin, pasá los datos esos para seguir.

---

### Post by Lovecraft99 on 2010-03-17
Hola, tengo el mismo problema de Arabela. Más indicaciones: al seleccionar efectos normal / extras empieza a buscar complementos y después la frase 'no se han podido activar los efectos de escritorio'. 

El resultado de mi lspci,

00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 11)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

---

### Post by guillermolisi on 2010-03-17
Lamento decirte que con placas de video VIA no hay como activar los efectos. Lo maximo que podras conseguir es una resolucion aceptable con el driver VESA ya que los drivers de VIA no funcionan bien (desde hace mucho tiempo).

---


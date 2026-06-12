---
title: "problemas al actualizar xubuntu a la versión 9.04"
date: 2009-07-15
forum: Instalación y Actualización
---

### Post by ciriaco on 2009-07-15
Saludos,

Tengo instalado xubuntu en un antiguo Compaq presario, P. III.  La versión 8.10 funcionaba sin mayores inconvenientes, pero se me ocurrió actualizar a la 9.04 y ahora tengo el problema que no puedo entrar al escritorio porque el sistema se sale de la sesión y me vuelve a dejar en la pantalla de logueo.

¿Será un problema del kernel, el gdm u otro?  La cosa es que no logro hacer mucho porque me bota la sesión y vuelta otra vez a pedir logueo.

Cualquier luz se agradece.

---

### Post by AlvaroV on 2009-07-15
¿Probo reinstalando el sistema?

---

### Post by ciriaco on 2009-07-15
Haciendo memoria, porque he estado instalando otros linux en otros equipos, creo haber instalado de 0 con xubuntu alternate con el mismo resultado.

Pero no pierdo nada probando nuevamente, la única lata que me da es tener que volver a configurar el vsftpd, que no es tan trivial como parece.

Gracias por responder.

---

### Post by moreback on 2009-07-16
Me tinca problema de las X, ¿qué tarjeta de video tienes? ¿lspci?

---

### Post by ciriaco on 2009-07-16
Posteo lo que muestra lspci:

00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 22)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:03.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax Modem (rev 08)
00:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0a.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller
00:14.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 13)
00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
00:14.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
00:14.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 10)
01:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)    <--------------  Esta es.

Detallo un poco más lo que sucede.

La sesión en estos momentos logra entrar con xfce, abro ventanas, pude abrir el terminal y obtener este listado, etc.

El problema aparece cuando quiero, por ejemplo, mover una ventana hacia el centro de la pantalla.  Con una ventana como la calculadora, ni un problema, pero si abro el panel de configuración de xfce y quiero moverlo o abro thunar y quiero hacer lo mismo, se oculta el puntero del mouse y me resetea la sesión.

Probé maximizando thunar, lo hizo, lo volví a su tamaño inicial y nuevamente me resetea la sesión y me deja en la ventana de logueo.

Por lo visto si es un problema de las X, pero no logro ver qué puede ser, si en el 8.10 funcionaba sin dificultades.

---


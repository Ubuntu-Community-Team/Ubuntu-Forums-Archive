---
title: "problemas para conectar modem usb"
date: 2009-10-20
forum: Hardware
---

### Post by elissss on 2009-10-20
Buenos dias. Quisiera saber si me podrian ayudar. Instale el ubuntu sin inconvenientes, pero no puedo conectar a internet, tengo un modem usb que no me lo reconoce, y cuando quiero instalar los driver desde cd tampoco me lo lee ](*,) . De todos modos puedo conseguir un modem que se conecte a la placa de red, el inconveniente que tengo en este caso es que no consigo los driver de la placa de red, me dijeron que cuando instalas el ubunto instala los drivers, puede ser??
Desde ya agradezco sus ayudas!
:P

---

### Post by guidito73 on 2009-10-20
Vamos por partes:

1-Marca y modelo del modem usb? Compañía prestadora del servicio? (Asumo que NO estamos hablando de un modem 3G no?)

2-Sí, generalmente la placa de red te la reconoce automáticamente. Para asegurarnos, abrí una terminal (Aplicaciones ----> Accesorios ---> Terminal) y escribí el siguiente comando:

> lspci

Y posteá qué te devuelve la consola.

Cualquier cosa, chiflá que seguimos ayudando.

---

### Post by elissss on 2009-10-20
buenas noches. EL modem es un SpeedTouch(tm) USB ADSL RFC148 330, (no es 3g), y tengo speedy.
Con respecto a la placa de red tengo que volver a instalar el ubuntu porque ahora estoy solo con el xp.
Puedo verificar si me reconece la placa instalando el ubuntu, sin desintalar el xp, es decir con los dos sistemas??asi no formateo a cada rato la maquina....:P

Muchas gracias!!

---

### Post by josecuervo86 on 2009-10-20
[quote=elissss]Puedo verificar si me reconece la placa instalando el ubuntu, sin desintalar el xp, es decir con los dos sistemas??asi no formateo a cada rato la maquina....[/quote]

Mira, justamente el otro dia colgue un tutorial de como hacer una instalación manteniendo los dos sistemas: [http://ubuntuforums.org/showthread.php?t=1280260](http://ubuntuforums.org/showthread.php?t=1280260)

---

### Post by elissss on 2009-10-21
Buenos dias! hice lo que me dijiste y me aparece esto 

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
**[SIZE=3][COLOR=black]00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)[/COLOR][/SIZE]**
02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)


si no entendi mal, reconocio la placa??:confused:

gracias!!!!

---

### Post by guidito73 on 2009-10-21
Sí sí, estaría perfecto.

Si tenés la posibilidad de conseguir un Router con conexión Ethernet es muy recomendable, funcionan mucho mejor que los USB. Además de las obvios problemas de compatibilidad de drivers!

Avisá cualquier cosa.

---

### Post by gmunioz on 2009-10-21
Hola gui....:

Prueba seguir este tutorial:

[http://www.foroz.org/instalar-alcatel-speedtouch-330-en-linuxubuntu.html](http://www.foroz.org/instalar-alcatel-speedtouch-330-en-linuxubuntu.html)

---

### Post by elissss on 2009-10-22
Buenisimo!!!
muchas gracias, cuando consiga el modem lo pruebo y aviso!!!!!

GRacias!!!

):P

---

### Post by elissss on 2009-10-25
muchas gracias ya estoy usando ubuntu e internet....

gracias!!=D>

---


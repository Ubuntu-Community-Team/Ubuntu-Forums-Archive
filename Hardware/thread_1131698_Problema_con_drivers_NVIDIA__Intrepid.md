---
title: "Problema con drivers NVIDIA / Intrepid"
date: 2009-04-21
forum: Hardware
---

### Post by benjamin_linux on 2009-04-21
Después de mucho vuelvo a molestar...

De un día para el otro, sin que recuerde haber hecho algo, los gráficos me empezaron a fallar, los paneles desaparecían, cosas raras... Como quería "hacer lío" con las particiones (dar más espacio a la partición /home y varias cosas más) aproveché y quise reinstalar de 0 Intrepid.

Y ahora ni siquiera puedo instalar mi placa nVidia, que ustedes mismos me ayudaron a configurar... Cuando quiero hacerlo desde Sistema > Administración > Controladores... o desde Envy, se me cuelga el sistema o, si lo dejo, unos buenos minutos, "termina" pero no cambia absolutamente nada, no instala nada; y si intento, directamente, poner los efectos de escritorio, me dice que "No se han podido activar".

Cuando pongo lspci me da de resultado:

```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

Al poner glxinfo

```
seretur@dendro:~$ glxinfo | grep rendering
direct rendering: Yes
```

(Y con glxgears me aparecen los engranajes). Pero si pongo compiz --replace,

```
seretur@dendro:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

Y también se me cuelga, hasta me deja de funcionar el teclado!

Por último, mi xorg.conf
```

# xorg.conf (X.Org X Window System server configuration file)
#
# 

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Espero ayudar con toda la información que puse, ya estoy medio nervioso a estas alturas, ¿me temo que pueda ser algo de la placa?

---

### Post by benjamin_linux on 2009-04-21
Lo "solucioné" volviéndome a Hardy, instalando los drivers de EnvyNG (que no podía instalar desde Intrepid. La verdad... cualquiera, no sé qué se habrá descuajeringado. De todos modos, si ven algo que estuviera mal en lo que puse arriba, avísenme que no es mi intención seguir mucho tiempo en HH y quiero saber, de todos modos, qué puede haber pasado!

---

### Post by luks911 on 2009-04-21
A mí también me estuvo dando problemas "Controladores de Hardware" con el driver para esa placa. Se quedaba colgado o saltaba un error. Solución: instalarlo con aptitude

```
sudo aptitude install nvidia-glx-180
```

le respondés que sí a lo que pregunte, reiniciás y ya. Ese driver me funciona bien en 9.04. En Intrepid me iba mejor el 177. O sea:

```
sudo aptitude install nvidia-glx-177
```

---

### Post by benjamin_linux on 2009-04-21
Gracias por la respuesta!

Igualmente, me está llamando mucho la atención la diferencia de rendimiento en mi laptop entre HH y II, me funciona -muchísimo- mejor Hardy, así que por ahora me voy a quedar acá.

---


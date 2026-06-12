---
title: "Problermas de Sonido ubuntu 10.04"
date: 2010-09-27
forum: Hardware
---

### Post by teko83 on 2010-09-27
Hola amigos del foro: tengo el siguiente problema, instalé ubuntu 10.04 en mi máquina y hasta el momento funciona muy bien, el único detalle es que no puedo escuchar dos cosas al mismo tiempo, por ejemplo no puedo ver videos de youtube y tener emesene, pues cuando alguien me habla se superpone el mensaje y se pierde el sonido del video.

Ojalá puedan ayudarme
saludos

---

### Post by RafaelG on 2010-09-28
Teko83,

Falta informacion, tienes dos opciones una es probar [FUCH]("http://ubuntuforums.org/showthread.php?t=1211568") o la otra opcion es correr el siguiente codigo en un terminal y pegar aca lo que te arroje:

```

lspci

```Ademas podrias indicar que version de **Flash** tienes intalado, puedes escribir **about: plugins** (sin el espacio entre los dos puntos y la P) en la barra de direcciones en firefox y pegar aca lo que te arroja.

Saludos!

---

### Post by teko83 on 2010-09-29
Gracias por la respuesta
mira esto tengo de resultado de lspci


00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control


y de firefox tengo lo siguiente 

    Versión: 
    Shockwave Flash 10.1 r53

ojalá puedas ayudarme

---

### Post by Carlos C on 2010-09-30
> **teko83 said:**
> 
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)


Por favor verifica que no exista algún controlador de hardware disponible para esa tarjeta. Lo puedes ver en el panel superior, entrando a Sistema>Administración>Controladores de Hardware.

Saludos.

---

### Post by RafaelG on 2010-09-30
Teko83,

Podrias revisar en los repositorios si tienes instalado:

- flashplugin-nonfree 
- flashplugin-nonfree-extrasound

Si no los tienes entonces instalalos y revisa si se soluciono el inconveniente

Saludos!

---

### Post by teko83 on 2010-09-30
Rafael, instalé los drivers, pero me sigo con el mismo problema...
será algún error de emesene???

Saludos y muchas gracias

---

### Post by Carlos C on 2010-10-03
> **teko83 said:**
> Rafael, instalé los drivers, pero me sigo con el mismo problema...
será algún error de emesene???

Saludos y muchas gracias

¿Esto ocurre con otras aplicaciones o sólo ocurre con emesene?

---

### Post by teko83 on 2010-10-04
ocurre con todas las aplicaciones
si tengo firefox y me tira un sonido me silencia la música y así con todas las palicaciones

---

### Post by Carlos C on 2010-10-04
¿El equipo es un laptop? Por favor escribe en el terminal:
```
aplay -l
```

Saludos.

---

### Post by teko83 on 2010-10-31
Hola amigos:
disculpen, pero estube sin internet en mi pc y no pude conectarme hasta ahora

escribí aplay -l y esto es que me aparece


fparra@fparra-desktop:~$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: VT1708S Analog [VT1708S Analog]
  Subdispositivos: 1/2
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1

Ojalá puedan ayudarme
Saludos

---

### Post by RafaelG on 2010-11-01
Bueno yo hace tiempo atras cuando utilizaba la version 8.04 tuve un problema muy parecido al que tienes en este momento, despues de haber buscado en muchos post termine desintalando ALSA para instalarlo nuevamente pero esta maniobra seria como ultima opcion aunque para mi funciono a la perfeccion. 

Saludos!

---

### Post by teko83 on 2010-11-18
Muchachos, resolví el problema...
Resulta que tenía pulseaudio y alsamixer instalado y eso al parecer me generaba conflictos....
desinstalé pulseaudio y ahora no tengo el problema
Muchas gracias por su ayuda
Saludos

---

### Post by moreback on 2010-11-18
Que extraño que no te funcione pulseaudio, yo nunca he tenido problemas con él y de hecho tu problema se me daba con Ubuntu 8.04 pero todo se arregló cuando actualizaron la versión del plugin de flash.

Saludos.

---

### Post by RafaelG on 2010-11-18
Perfecto!

---


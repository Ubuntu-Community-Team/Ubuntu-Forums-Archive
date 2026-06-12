---
title: "Ati Radeon 9550 Guru en Kubuntu 9.04"
date: 2009-10-16
forum: Hardware
---

### Post by Blackaiser on 2009-10-16
Mi problema es que tengo una Ati Radeon 9550 Guru, esa que se cambia el jumper y queda en 9600, pues la tengo instalada pero los gráficos andan ahí no más, intenté instalalos manualmente y lo logré, almenos por un día, al apagar el sistema al día siguiente quedo todo con rayas para todos lados sin poder ver algo.... reinicie el sistema con el modo solucionar problemas graficos (bendito linux) y se solucionó, pero volvió al modo VGA.

adjunto el reporte de FUCH:
```

Escritorio:    KDE

```


```

$lspci|grep -i vga
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]

```


```

$cat /var/log/Xorg.0.log|grep EE
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

```


```

$cat /var/log/messages |grep error

```


```

$cat /var/log/syslog |grep error

```


```

$lsmod |grep drm

```


```

$lsmod |grep agp
sis_agp                15360  1 
agpgart                42696  1 sis_agp

```


```

$glxinfo |grep direct
direct rendering: Yes

```


La pregunta, alguien sabe si esto tiene solución o debo cambiar la tarjeta? (es mi regalona y ya me da lata cambiarla, prefiero comprarme un equipo nuevo jaja)

---

### Post by Blackaiser on 2009-10-16
instale la aplicación lshw y este es el informe arrojado en cuanto a mi tarjeta
VGA compatible controller
/0/100/1/0


product: RV350 AR [Radeon 9600] [1002:4152]
vendor: ATI Technologies Inc [1002]
bus info: pci@0000:01:00.0
version: 00
width: 32 bits
clock: 66MHz
capabilities:
    AGP,
    AGP 3.0,
    Power Management,
    bus mastering,
    PCI capabilities listing
configuration:
    latency: 64
    mingnt: 8
this device hasn't been claimed

Alguien sabe que puedo hacer?

---

### Post by moreback on 2009-10-16
> **Blackaiser said:**
> Alguien sabe que puedo hacer?

¿Buscaste en los foros? estoy seguro que por ahí hay algún post donde ya lo resolvieron...

---

### Post by Blackaiser on 2009-10-16
sip... pero solo encontre para tarjetas Nvidia y Radeon hasta la 7000, pero de esta nop...

---

### Post by Blackaiser on 2009-10-27
Bueno señores, encontre la solución, el problema no estaba en los drivers sino en el termino de la configuración de la pantalla.

Primero instale los drivers de Ati con el Synaptic (solo pon ati e instala los drivers libres), luego segui la configuracion para corregir el problema con los Mhz... post de staar en el foro argentino

el archivo donde se encuentran las configuraciones del servidor grafico es el /etc/X11/xorg.conf, tendrías que modificarlo para agregarle los rangos que soporta tu monitor...

logueate en una consola (Ctrl+Alt+F1) y poné  	Code:
 	sudo nano /etc/X11/xorg.conf 
 se te va a abrir el archivo con el editor de textos nano, andá hasta la sección 'Monitor' y agregale dos líneas con los valores de HorizSync y VertRefresh de TU monitor (buscalos en el manual), te quedaría así:  	Code:
 	Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection 
 OJO este es un ejemplo de MI xorg.conf, seguramente vos vas a tener un Identifier diferente y no vas a tener ni VendorName ni ModelName...

saludos
 		                   		  		  		 		 			 				__________________


Bueno con esto hasta ahora esta funcionando impecable... espero le sirva a algunos otros que tengan esta tarjetita y estan en ubuntu... 


Saludos.

Problema Solucionado

---


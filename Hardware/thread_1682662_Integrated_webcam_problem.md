---
title: "Integrated webcam problem"
date: 2011-02-06
forum: Hardware
---

### Post by fedekiller on 2011-02-06
Hi all, I'm having problems with my webcam, it doesn't work on ubuntu, I know the hardware works, so it's not broken.
Also, I cant even get the model I've searched on google about this, but when i do 'lsusb' it only shows my mouse...

---

### Post by realzippy on 2011-02-06
Install guvcview ,check if device is listed there..

---

### Post by fedekiller on 2011-02-06
I installed it but It cant start, it says it can't find the drivers.

---

### Post by realzippy on 2011-02-06
have you run
```
gstreamer-properties
``` 
Video TAB,change plugin V4L2,test..

---

### Post by ajgreeny on 2011-02-06
You can also try ```
sudo lshw -html > $(date +%T)hardware.html && firefox *hardware.html
```and search the firefox page that opens for the camera.

Simpler still just ```
sudo lshw
``` and search the terminal output, or ```
lspci
```which might show it.

---

### Post by fedekiller on 2011-02-06
@realzippy: I changed it but still it didnt work :( it says 

"gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': No se puede identificar el dispositivo «/dev/video0». [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline3/GstV4l2Src:v4l2src2:
system error: No existe el fichero o el directorio]"

@ajgreeny: I run the first command and had the html page generated, some boxes are red which i think means the drivers could not be installed?

```
id:	
display:1
description: 	Display controller
product: 	N10 Family Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2.1
bus info: 	
pci@0000:00:02.1
version: 	00
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
latency	=	0
resources:	
memory	:	fea00000-fea7ffff
```

and

```
id:	
serial
description: 	SMBus
product: 	N10/ICH 7 Family SMBus Controller
vendor: 	Intel Corporation
physical id: 	
1f.3
bus info: 	
pci@0000:00:1f.3
version: 	02
width: 	32 bits
clock: 	33MHz
configuration:	
latency	=	0
resources:	
ioport	:	f000(size=32)
```

Are red

---

### Post by fedekiller on 2011-02-06
Fixed, sorry, it was a stupid mistake of mine. Looks like when i press F6 the camera is disabled, i tohught this was resetted when you reset your pc.
:P Thanks all

---


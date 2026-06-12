---
title: "Aumentar memoria de video"
date: 2010-04-20
forum: Hardware
---

### Post by __H__ on 2010-04-20
Hola,
 



Les comento que tengo instalado Ubuntu Karmic Koala en una notebook **"lenovo G450"**. Tengo entendido que para incrementar memoria, la placa integrada de video puede tomar un poco de memoria ram. Leí en algunos foros que esto **se configura desde el BIOS**, pero desde allí no encontré nada que me permita determinar la cantidad de memoria de video o de ram para usar.
Me gustaría saber si existe algún software para poder incrementar la memoria de video.
 Estos son los datos del hardware que muestra el programa "Hardinfo":
 
[B]Display
[/B]
Resolution    1366x768 pixels
OpenGL Renderer    Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
X11 Vendor    The X.Org Foundation
 
**Memory**
 

Total Memory    3029252 kB
Free Memory    2380824 kB
Buffers    49568 kB
Cached    388272 kB
Cached Swap    0 kB
Active    427152 kB
Inactive    179716 kB
 
**PCI Devices**

 VGA compatible controller    Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller
Display controller    Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller
 
**BIOS**
 

Date    09/18/2009
Vendor    LENOVO
Version    18CN37WW(V2.10)
 



*** Esto es parte de los datos de la placa que muestra el comando  **lspci -vv**:
> 

VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
Subsystem: Lenovo Device 3a02

Region 0: Memory at f4000000 (64-bit, non-prefetchable) (size=4M)
Region 2: Memory at d0000000 (64-bit, prefetchable) (size=256M)
Region 4: I/O ports at 1800 (size=8)
 Aclaro que el archivo xorg.conf para esta laptop, no existe en Karmic Koala
 
**Gracias!**

---


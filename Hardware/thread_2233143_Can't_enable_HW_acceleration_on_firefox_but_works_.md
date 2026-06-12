---
title: "Can't enable HW acceleration on firefox but works in chrome with radeon driver."
date: 2014-07-06
forum: Hardware
---

### Post by telefrancisco on 2014-07-06
Hello.

I'm using a Radeon HD8670D graphics card with open source radeon driver. When running Firefox I can't enable Hardware acceleration no matter what I do:



> Gráficos
Descripción del adaptador	X.Org -- Gallium 0.4 on AMD ARUBA
ID del dispositivo	Gallium 0.4 on AMD ARUBA
ID del fabricante	X.Org
Renderizador WebGL	X.Org -- Gallium 0.4 on AMD ARUBA
Ventanas aceleradas mediante GPU	0/1 Basic
Versión del controlador	3.0 Mesa 10.1.3
windowLayerManagerRemote	false
AzureCanvasBackend	cairo
AzureContentBackend	cairo
AzureFallbackCanvasBackend	none
AzureSkiaAccelerated


However, I can get hardware acceleration working on Chromium as you can see:

> **Graphics Feature Status**


[LIST]
[*]Canvas: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]3D CSS: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Compositing: [COLOR=#008000]Hardware accelerated on all pages and threaded[/COLOR]
[*]CSS Animation: [COLOR=#008000]Accelerated and threaded[/COLOR]
[*]Flash 3D: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D Baseline profile: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Video: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Video Decode: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Video Encode: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]WebGL: [COLOR=#008000]Hardware accelerated[/COLOR]
[/LIST]


How can I debug this error so I can get HW accel in Firefox, too?

Thanks.

---

### Post by Mark Phelps on 2014-07-06
Evidently, the two apps have different views on what constitutes "hardware acceleration".  Although the open-source Radeon drivers (the ones you are using) do provide some hardware acceleration, when folks use that term in relation to Radeon drivers, they more commonly mean the AMD fglrx drivers -- which you do NOT have installed.  Perhaps Firefox is only looking for the fglrx drivers.

---


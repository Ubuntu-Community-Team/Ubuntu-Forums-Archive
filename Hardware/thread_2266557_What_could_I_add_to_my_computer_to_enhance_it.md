---
title: "What could I add to my computer to enhance it"
date: 2015-02-23
forum: Hardware
---

### Post by michael-piziak on 2015-02-23
I have 4 PCI expansion slots inside.   I already have 4 gigs of ram.   Just wondering.  I play a LOT of emulation games - maybe a graphic card would fit in there ?

I really don't know much about the internals of computers.  I did read that I can only use low profile cards.

My computer: [http://deit.desales.edu/deit/assets/dc5800_data_sheet.pdf](http://deit.desales.edu/deit/assets/dc5800_data_sheet.pdf)

More info on my system:


[LIST]
[*][INDENT]I get this in Firefox:

Adapter Description    Intel Open Source Technology Center -- Mesa DRI Intel(R) Q33
Device ID    Mesa DRI Intel(R) Q33
Driver Version    1.4 Mesa 10.1.3
GPU Accelerated Windows    0/1 Basic Blocked for your graphics card because of unresolved driver issues.
Vendor ID    Intel Open Source Technology Center
WebGL Renderer    Blocked for your graphics card because of unresolved driver issues.
windowLayerManagerRemote    false
AzureCanvasBackend    cairo
AzureContentBackend    cairo
AzureFallbackCanvasBackend    none
AzureSkiaAccelerated    0


Which I'm told tells me that I have an Intel GMA3100 GPU, which only has support for the relatively ancient OpenGL 1.4 version.  Perhaps I could add something to the PCI slot to give me a better OpenGL version - ?

[/INDENT]
[/LIST]
Screenshot of expansion slots below:

---

### Post by CantankRus on 2015-02-23
Search your motherboard model for a compatible nvidia card maybe.
Maybe a cheap card like this ... [http://www.geforce.com/hardware/desktop-gpus/geforce-gt-610](http://www.geforce.com/hardware/desktop-gpus/geforce-gt-610)

The program **inxi** is good for getting computer details.
```
sudo apt-get install inxi
```

Then run ...
```
inxi -b
```

or try **dmidecode** for info....
```
sudo dmidecode -s baseboard-manufacturer && sudo dmidecode -s baseboard-product-name
```

[**_[COLOR="#B22222"]Ubuntu Hardware Support Nvidia[/COLOR]_**]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia")

---

### Post by michael-piziak on 2015-02-23
I see documentation that says this Nvidia card is compatible with my system.   I'm not sure if it's low profile though.   Your thoughts?

CompatibilityThe NVIDIA Quadro NVS 295 256MB PCIe x16 is supported on the HP Compaq dc7900 Convertible Minitower,HP Compaq dc7900 Small Form Factor, HP Compaq dc5800 Microtower, HP Compaq dc5800 Small Form Factor BusinessDesktop PCs and HP Compaq 6000 Pro Microtower, HP Compaq 6000 Pro Small Form Factor, HP Compaq 6005 Pro Microtower,HP Compaq 6005 Pro Small Form Factor, HP Compaq 6200 Pro Microtower, HP Compaq 6200 Pro Small Form Factor, HPCompaq 8000 Elite Small Form Factor, HP Compaq 8000 Elite Convertible Minitower, HP Compaq 8100 Elite Small Form Factor,and HP Compaq 8100 Elite Convertible Minitower.

Perhaps this one?:  [http://www.amazon.com/Dell-NVIDIA-Quadro-Profile-Graphics/dp/B00MC8GLBK/ref=sr_1_2?ie=UTF8&qid=1424751392&sr=8-2&keywords=NVIDIA+Quadro+NVS+295+256MB+PCIe+x16](http://www.amazon.com/Dell-NVIDIA-Quadro-Profile-Graphics/dp/B00MC8GLBK/ref=sr_1_2?ie=UTF8&qid=1424751392&sr=8-2&keywords=NVIDIA+Quadro+NVS+295+256MB+PCIe+x16)


Update:  I also see that this one will work:  ATI Radeon HD 4550 DH PCIe x16 Graphics Card

Please someone comment on which card is better and how it will enhance my system (like openGL, etc...).

Links to both card specs:
  
[http://www8.hp.com/h20195/v2/getpdf.aspx/c04287873.pdf?ver=5](http://www8.hp.com/h20195/v2/getpdf.aspx/c04287873.pdf?ver=5)
and
[http://www8.hp.com/h20195/v2/GetPDF.aspx%2Fc04128513.pdf](http://www8.hp.com/h20195/v2/GetPDF.aspx%2Fc04128513.pdf)

---

### Post by michael-piziak on 2015-02-24
Update:  After posting on the HP forum, I've decided to go with the AMD Radeon HD 6450 or the nVidia GT 610.

Which one would probably work best for me with my Ubuntu 12.04 LTS ?  I know there have been issues with nVidia in the past. [COLOR=#000000][FONT=HPRegular]
[/FONT][/COLOR]

---

### Post by michael-piziak on 2015-02-24
[COLOR=#000000]I ordered the nVidia GT 610.[/COLOR]

---


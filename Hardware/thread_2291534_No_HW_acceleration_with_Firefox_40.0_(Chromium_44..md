---
title: "No HW acceleration with Firefox 40.0 (Chromium 44.0 works fine | AMD binary driver)"
date: 2015-08-20
forum: Hardware
---

### Post by pubalapoub on 2015-08-20
Hi,

I face an apparent lack of GPU acceleration with Firefox while it seems to be working fine with Chromium. Note: I'm using the latest AMD binary driver (15.200).

I made a comparison between both Web browsers with this demo page: [https://developer.mozilla.org/media/uploads/demos/p/a/paulrouget/8bfba7f0b6c62d877a2b82dd5e10931e/hacksmozillaorg-achi_1334270447_demo_package/HWACCEL/](https://developer.mozilla.org/media/uploads/demos/p/a/paulrouget/8bfba7f0b6c62d877a2b82dd5e10931e/hacksmozillaorg-achi_1334270447_demo_package/HWACCEL/)

Firefox: [COLOR=#ff0000]15 fps[/COLOR]
Chromium: [COLOR=#008000]60+ fps[/COLOR]

What could go wrong with Firefox?... Is there some Firefox parameter to enable that wouldn't be set by default?

Here are troubleshooting information provided by Firefox (sorry this is a French localized installation of Kubuntu 14.04 64bit):

Accélération graphique
----------------------

Description de la carte: [COLOR=#0000ff]ATI Technologies Inc. -- AMD Radeon (TM) R7 300 Series[/COLOR]
Fenêtres avec accélération graphique: [COLOR=#0000ff]0/1 Basic (OMTC)[/COLOR]
ID du périphérique: [COLOR=#0000ff]AMD Radeon (TM) R7 300 Series[/COLOR]
ID du vendeur: [COLOR=#0000ff]ATI Technologies Inc.[/COLOR]
Prise en charge matérielle pour le décodage H264: [COLOR=#0000ff]false[/COLOR]
Rendu WebGL: [COLOR=#0000ff]ATI Technologies Inc. -- AMD Radeon (TM) R7 300 Series[/COLOR]
Version du pilote: [COLOR=#0000ff]4.4.13374 Compatibility Profile Context 15.20.1013[/COLOR]
windowLayerManagerRemote: [COLOR=#0000ff]true[/COLOR]
Zoom/Panoramique asynchrones: [COLOR=#0000ff]none[/COLOR]
AzureCanvasBackend: [COLOR=#0000ff]cairo[/COLOR]
AzureContentBackend: [COLOR=#0000ff]cairo[/COLOR]
AzureFallbackCanvasBackend: [COLOR=#0000ff]none[/COLOR]
AzureSkiaAccelerated: [COLOR=#0000ff]0[/COLOR]


Thank you in advance for your opinion.

---

### Post by monkeybrain20122 on 2015-08-20
I don't know. This is strange. I ran the experiment on my netbook. FF 6 fps, Chrome 60+fps. But if I disable hardware acceleration in FF (Edited > Preferences > Advanced > GenerL and uncheck use hardware acceleration if available) then fps shoots up to 15 fps. This is AMD card with open driver.

On my intel machine unchecking use hardware acceleration when available in FF fps shoots up to 60+ fps the same as Chrome but with hardware acceleration enabled it was just 20 fps.

Firefox 40 on Ubuntu 15.04 64 bit.

Edited: however unchecking use jardware acceleration results in lower fps for webgl. e.g [http://webglsamples.org/aquarium/aquarium.html](http://webglsamples.org/aquarium/aquarium.html) On my intel machine with use hardware acceleration checked it gives 20 fps for 4000 fish same as Chrome, with it unchecked fps drops to 11fps.

---

### Post by monkeybrain20122 on 2015-08-20
BTW enter about:support in FF's url bar and scroll to graphics > GPU accelerated Windows. If it is 0/1 Basic (instead of 1/1 OpenGL (OMTC)) then hardware acceleration is disabled because your driver for some reason is blacklisted. In that case enter about:config in url bar and set layers.acceleration.force-enabled and layers.offmainthreadcomposition.enabled to be true. If FF crashes or something then just revert them, though offmaintreadcomposition is enabled by default for FF40 I think.

Edited: to clarify unchecking use hardware acceleration when available from Preferences  would result in 0/1 Basic. This post is about what happen before that, maybe hardware acceleration was never working in your case so check it first. This post should have been posted before the previous one.

---

### Post by pubalapoub on 2015-08-23
> **monkeybrain20122 said:**
> BTW enter about:support in FF's url bar and scroll to graphics > GPU accelerated Windows. If it is 0/1 Basic (instead of 1/1 OpenGL (OMTC)) then hardware acceleration is disabled because your driver for some reason is blacklisted.

Hi monkeybrain20122,

thanks a lot for your research. To answer you briefly:

- checking or unchecking option "use hardware acceleration if available" doesn't make any difference in my case (same fps). Except that when  this option is unchecked, I read "0/2 Basic (OMTC)" ("0/1 Basic (OMTC)" when checked).

- I tested "layers.acceleration.force-enabled" = true + setting environment variable MOZ_USE_OMTC=1 (as indicated in [http://askubuntu.com/questions/491750/force-enable-hardware-acceleration-in-firefox](http://askubuntu.com/questions/491750/force-enable-hardware-acceleration-in-firefox)) but it didn't change anything.

- WebGL ([http://webglsamples.org/aquarium/aquarium.html](http://webglsamples.org/aquarium/aquarium.html)): I get 16-18 fps with FF for 4000 fishes ("use hardware acceleration if available" being checked). The funny thing is that I get the following message with Chromium: "It does not appear your computer supports WebGL. Status: Web page was not allowed to create a WebGL context." :)

Ok. I won't fight too long for this, maybe challenge Mozilla a bit if I find time to contact them to get their opinion. Maybe the conclusion is that 2 Web browsers on a computer is better than 1 ;)

Thanks again for your time.

---


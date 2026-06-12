---
title: "Succesfully installation of Ubuntu 5.1 on Asus Z92U"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by Eversmann on 2005-12-11
Recently i've installed Ubuntu 5.10 on my brand new Asus Z92U. Here's the hardware it has:

* AMD Sempron Mobile 3000
* 512 Mb RAM DDR
* Sis 760GX (memory shared)
* 40Gb HD
* 15.4 WXGA Screen
* Integrated sound card Sis AC'97
* Synaptic mouse pad
* Integrated wifi from Broadcom
* Camera and mic
* DVD Matshita DVD-RW double-layer

Costed me 699 € (excellent price)

After install ubuntu, everything worked out of the box, except wifi and camera (didn't tried to put it on yet).

About the sis video card, i've installed the drivers from the "not official" but main site for SIS (don't remember what it is, but i found it searching on this forum).

The sound card works perfectly, just had to use the instructions to make it alsa only (to have full duplex support for using teamspeak).

The wifi worked with no problem using ndiswrapper and the drivers that comes with the Asus CD for windows.

I'm even using composite and xcompmgr.

To sum it all, i can recommend this notebook to the people who wants to buy a cheap one to install linux (and ubuntu) on it. Until now, i'm very happy and i'm the envy of all my friends ;-)

---

### Post by Zelut on 2005-12-11
Any chance you can add that to the supported listing in the [LaptopTestingTeam]("http://https://wiki.ubuntu.com/LaptopTestingTeam") Wiki or allow me to add it?  I may want to ask you a few additional questions if I were to do it.  Let me know, thanks.

---

### Post by Eversmann on 2005-12-12
Of course, if you need any other information, please ask. I can add this there but i don't mind at all that you do.

---

### Post by brallan on 2006-04-23
[wiki.ubuntu.com/LaptopTestingTeam/AsusZ92U]("https://wiki.ubuntu.com/LaptopTestingTeam/AsusZ92U") is the wiki.

[QUOTE=Eversmann]After install ubuntu, everything worked out of the box, except wifi and camera (didn't tried to put it on yet). [/QUOTE]

Nor does the microphone in the camera, or the Ricoh SD flash card reader work. Or suspend on closing the cover. These I can live without.

[QUOTE=Eversmann]About the sis video card, i've installed the drivers from the "not official" but main site for SIS (don't remember what it is, but i found it searching on this forum).[/QUOTE]

The SiS driver does NOT offer DRI support/allow OpenGL apps (Stellarium,  Compiz) to work, so they will crawl and hang...

I do NOT recommend this laptop for this reason, though I own one and can live without it, I wish I'd known before I bought it... 

The other thing is that external monitors may have flicker problems, see the [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/AsusZ92U")...

If anyone has experience with a Dapper install or using the new broadband drivers instead of ndiswrapper, please [document]("https://wiki.ubuntu.com/LaptopTestingTeam/AsusZ92U") it.

---


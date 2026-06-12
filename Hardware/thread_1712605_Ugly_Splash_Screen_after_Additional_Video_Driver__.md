---
title: "Ugly Splash Screen after Additional Video Driver  Activated,"
date: 2011-03-22
forum: Hardware
---

### Post by Zanderist on 2011-03-22
I normally have the nice ubuntu boot splash when I have this driver deactivated. 

I'm talking of course about the the starting up part with the red dots and the nice 'Ubuntu Graphic'.

When I Activate my ATI/AMD proprietary FGLRX graphics driver, however; I end up will this generic splash screen which is basically the same red dots, but the nice ubuntu graphic is replaced with a boring font. [FONT=Arial]As shown below.[/FONT]

> [FONT=System]Ubuntu 10.10[/FONT] Mind you I'm not asking you how to change the splash screen, I'm asking how do I get the default one to work under the new video driver.

I'm currently attempting this at the moment.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Well the above worked but the logo is HUGE!

---

### Post by dave2001 on 2011-03-23
Sorry I don't recall exactly where I heard/read this; I believe the fglrx driver no longer works properly.

If a broken splash screen is the only problem you've got, you may be lucky. Look into the fglrx driver bugs/problems in lucid and maverick and you might get some leads.

---

### Post by Myoh on 2011-03-23
I did exactly the same steps (followed that tutorial too) when I installed Fglrx. What resolution do you use for the splash screen? When you try a resolution that isn't supported by the video card (well, actually it's framebuffer I think), it reverts to a default resolution.

Run this in a terminal to see what resolutions your framebuffer supports
```
sudo hwinfo --framebuffer
```
You'll probably need to install it with apt-get, it isn't by default.

---

### Post by Zanderist on 2011-03-28
> **Myoh said:**
> I did exactly the same steps (followed that tutorial too) when I installed Fglrx. What resolution do you use for the splash screen? When you try a resolution that isn't supported by the video card (well, actually it's framebuffer I think), it reverts to a default resolution.

Run this in a terminal to see what resolutions your framebuffer supports
```
sudo hwinfo --framebuffer
```You'll probably need to install it with apt-get, it isn't by default.
```
Unique ID: rdCR.io8JTV5CzmD
  Hardware Class: framebuffer
  Model: "(C) 1988-2005, ATI Technologies Inc.  RS880M"
  Vendor: "(C) 1988-2005, ATI Technologies Inc. "
  Device: "RS880M"
  SubVendor: "ATI ATOMBIOS"
  SubDevice: 
  Revision: "01.00"
**  Memory Size: 16 MB**
  Memory Range: 0xe0000000-0xe0ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Mode 0x0367: 1366x768 (+1408), 8 bits
  Mode 0x0368: 1366x768 (+2752), 16 bits
  Mode 0x0369: 1366x768 (+5504), 24 bits
```I'm concerned about that memory size...16mbs, Is that normal?

I've also changed the resolution to the the highest one (or the last one on this list) and it has worked perfectly.

---

### Post by Fabled One on 2011-04-22
> **dave2001 said:**
> Sorry I don't recall exactly where I heard/read this; I believe the fglrx driver no longer works properly.

Wait, if fglrx doesn't work, then what do we use? I only installed that because Administration->Additional Drivers had it listed.

---

### Post by marin123 on 2011-04-22
dont worry. the fglrx driver works, the only problem is that plymouth doesnt like it :)

there's nothing wrong with your computer, its just the way it is...

i have ati radeon with proprietary drivers and have the same "problem"... maybe new ubuntus will have a fix for this :)

---

### Post by dave2001 on 2011-04-29
I remembered what the problem with fglrx was: my card is no longer supported. So it's not an option for me anymore. Sorry to give bad information there.

---

### Post by FishboyFive on 2012-04-28
its still a problem with Ubuntu 12.04 and AMD HD6790 and HD6870

plymouth is so ugly and has errors

---


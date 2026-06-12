---
title: "Ubuntu doesn't recognize widescreen display"
date: 2012-08-08
forum: Hardware
---

### Post by Buntu Bunny on 2012-08-08
I installed Ubuntu 12.04 (dual with Win7) on my new desktop today and my display is wonky. I have a widescreen monitor, but the only resolution options in display settings are 1024x768, or 800x600. In addition, it seems to think I'm on a laptop. Launcher placement offers "all displays" or "laptop", but neither option changes anything. The "detect displays" button yields nothing. 

Some particulars:

Desktop: Asus Essentio CM1470-02
Processor: AMD E2-3200 APU with Radeon HD Graphics
Monitor: Acer G185H; max resolution supported, 1366x768

After doing all the updates, I tried to install the proprietary driver (ATI/AMD proprietary FGLRX graphics driver), but got a fail message. The details in jockey.log were outrageously long, so I didn't include them here. If they'd be useful, I will.

Also, during Ubuntu installation I had problems (black screen), and had to set nomodeset in my kernel boot options. Not sure if that's relevant.

Any suggestions? This stretched view of everything on my monitor is giving me a headache.

---

### Post by Buntu Bunny on 2012-08-08
While waiting to see if anyone had any suggestions, I've been doing some searching around the internet. Apparently this isn't that uncommon. Quite a few folks have asked this question since Lucid, and for a variety of processors, graphics cards, drivers, and monitors, but I haven't found a solution yet.

I have found fixes for splash screen resolutions, VirtualBox resolutions, and dirty fixes with the disclaimer that they cause other problems. I'll keep looking but also hope someone has some suggestions to my problem.

---

### Post by Vakman on 2012-08-08
Could you please post the output of: ```
fglrxinfo
```
If your drivers are installed correctly, I think you can force the resolution yourself, look here: [https://wiki.ubuntu.com/X/Config/Resolution/](https://wiki.ubuntu.com/X/Config/Resolution/)

---

### Post by QIII on 2012-08-08
See the ATI driver wiki in my signature.

Use the table of contents to go to the section "Using the Ubuntu repositories (alternate command line method, including hardware acceleration)".

You can skip step 8 and do it later.

You may have what AMD calls "dual graphics", so take care to read the specific instructions for that.  Catalyst Control Center will allow you to choose between integrated and dedicated graphics, but it requires a logout/login.  If it doesn't, no harm in giving the commands to initialize multiple graphics.

---

### Post by Buntu Bunny on 2012-08-08
Thisislaw and Qlll, I very much appreciate your responses. I'm not sure what happened, but somehow Ubuntu now recognizes my monitor make and resolution. All I did was shut the computer down when a severe thunderstorm passed overhead. When I rebooted, everything looked as it should. What is odd is that I restarted my computer several times in the meantime. I'm puzzled but pleased.

---


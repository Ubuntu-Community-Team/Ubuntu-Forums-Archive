---
title: "ATI video cards still unusable?"
date: 2009-07-26
forum: Hardware
---

### Post by RaptorZX3 on 2009-07-26
i have a media center with Ubuntu installed, and i want to know something about the video cards....

i have a Radeon HD3450 256mb here waiting to be installed, and i wanted to know if the new Ubuntu 9.04 is more friendly with ATI video cards now?

i remember Ubuntu wasn't working at all with proper ATI drivers installed on it.

---

### Post by lukjad on 2009-07-26
I'm using an ATI card and it's working fine. I don't have Compiz enabled, so that might help with stability.

---

### Post by RaptorZX3 on 2009-07-26
which drivers did you installed?

---

### Post by SamZebian on 2009-07-26
I tried using ubuntu x64 with my laptop, it has an ATI Radeon HD 4650, and I had no luck with drivers. Kept getting a black screen after reboot after the drivers were installed. I tried ubuntu's restricted drivers and then I reinstalled and tried ATI's driver from the website. Both failed for me. I went back to windows 7 for now. IDK how to fix it though.

---

### Post by LemurApocalypse on 2009-07-26
HD3200 integrated works fine with Compiz.

---

### Post by SamZebian on 2009-07-26
> **LemurApocalypse said:**
> HD3200 integrated works fine with Compiz.

How did you install your drivers? Restricted drivers form ubuntu or ATI's drivers from their website?

---

### Post by LemurApocalypse on 2009-07-26
Restricted driver manager worked completely fine.

---

### Post by RaptorZX3 on 2009-07-27
ATI video cards are still more-or-less compatible with Ubuntu.

Take any NVidia cards, it will work fine! try it with an ATI video card, you have a chance it might work or not. Ubuntu is a really bad choice for ATI video cards users. They still need to work on the drivers for them to work fine.

---

### Post by SamZebian on 2009-07-27
OK I don't know how this happened but when I installed my ATI drivers last week on ubuntu, I left grub with default settings. Even though my drivers didn't work after rebooting after I installed them, they suddenly worked today when my little brother just turned it on and forgot to select windows! Thanks to him I don't have to reinstall ubuntu again and attempt to install gpu drivers!

---

### Post by RaptorZX3 on 2009-07-27
i wonder why Ubuntu is still so ATI-unfriendly...

---

### Post by ZaHACKieL on 2009-07-27
Well, I have a Dell Studio with an ATI Mobility Radeon HD3650  and it works fine. The only problem I'm having now with Ubuntu 9.04 is a delay when maximizing, alt-tabing and restoring windows. Besides that, everything is OK.

You just go to: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

and look for your model. Actually, if you are using the Mobility Radeon don't look in the Mobility Radeon submenu, just go to Linux > Radeon > Your model..probably the 3xxx Series.

Install those drivers with admin privileges and you will get a GUI. After that, your ATI card should work fine.

If you have the correct drivers you should have an ATI Control Center in you Applications menu. Also you should see the model in your terminal with the lspci.
And another thing you may want to try is the glxgears command in your terminal. You will get a 3D animation and make sure it runs smoothly, drag the window, etc.

Just one thing...when you upgrade the Kernel you have to reinstall the ATI drivers or you will get a black screen.

Let me know if everything is working fine.

ZL

---

### Post by messiah on 2009-07-28
I'm using HP 6830s, 17" 2Gb DDR2, 800Mgz RAM, Pentium dual-core 2,16Ghz and ATI Mobility Radeon HD 3430 and it works fine without desktop effects enabled. Cube is working fine but when minimising,un-minimising and resizing windows there is few seconds delay! I goggled a bit and it turns to be ati driver issue (what a surprise :) ) I think that above mentioned hardware is more than capable to run Compiz. The only question is will and when ATI is going to  finally improve their support!?! Hopefully things are going to be better when Ceramic Koala hits the download servers.:):lolflag:

---

### Post by aaamos on 2009-07-28
You guys might want to have a look at [http://forum.compiz-fusion.org/showthread.php?p=73964#post73964](http://forum.compiz-fusion.org/showthread.php?p=73964#post73964) - I had the same issue with resize delays when compiz was switched on, for the same video card as ZaHACKieL (also Dell Studio), and was able to work around the issue with the combination of the latest Ubuntu updates and the Xorg patch mentioned in post #6. Compiz is working great, cube and all :)

Cheers,

Amos

---

### Post by messiah on 2009-07-28
> **aaamos said:**
> You guys might want to have a look at [http://forum.compiz-fusion.org/showthread.php?p=73964#post73964](http://forum.compiz-fusion.org/showthread.php?p=73964#post73964) - I had the same issue with resize delays when compiz was switched on, for the same video card as ZaHACKieL (also Dell Studio), and was able to work around the issue with the combination of the latest Ubuntu updates and the Xorg patch mentioned in post #6. Compiz is working great, cube and all :)

Cheers,

Amos

TNX Amos it did the trick now it works as it should! Maybe this post should be a sticky,I'll will spread this all over local LUG's in Bosnia an former yugoslav republic's :)=D>=D>=D>

---

### Post by Bateluer on 2009-07-28
I've ran several versions of Ubuntu from 6.10 to 9.04, using a Radeon 9600 Pro, a 2900XT, and a 4870 without any issues.

---

### Post by ZaHACKieL on 2009-07-29
> **aaamos said:**
> You guys might want to have a look at [http://forum.compiz-fusion.org/showthread.php?p=73964#post73964](http://forum.compiz-fusion.org/showthread.php?p=73964#post73964) - I had the same issue with resize delays when compiz was switched on, for the same video card as ZaHACKieL (also Dell Studio), and was able to work around the issue with the combination of the latest Ubuntu updates and the Xorg patch mentioned in post #6. Compiz is working great, cube and all :)

Cheers,

Amos

Thanx a lot Amos, it did work. I saw that solution before but I was waiting for someone to tell me if they got secondary effects after the update. At least for now I don't observe any malfunction. Thanx a lot!

---


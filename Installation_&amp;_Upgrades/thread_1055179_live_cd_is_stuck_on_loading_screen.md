---
title: "live cd is stuck on loading screen"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Sherina on 2009-01-30
I was thinking about upgrading from 7.10 to 8.10 and wanted to try out the live cd first to see if I liked it. However the live cd is stuck at the loading screen and loading bars appear above the main loading bar when I try to use it. I tried just straight installing it and it does the same thing. I am using a Toshiba satellite laptop with ati graphics and an intel celeron M processor.

---

### Post by taurus on 2009-01-30
How much RAM does it have?

---

### Post by Sherina on 2009-01-30
512 Mb and a 1.6 GHz processor

---

### Post by taurus on 2009-01-30
If you want to do a fresh install of 8.10 (intrepid), you could also use the alternate CD.  It's a text based installer so it doesn't have to boot into GUI first.

---

### Post by Sherina on 2009-01-30
I dual boot between windows xp and ubuntu. Would intrepid run correctly even though the live cd didn't work? And how do I do a clean install without deleting the ubuntu partition and repartitioning the drive?

---

### Post by dabl on 2009-01-30
You may have a bad CD (bad burn, or bad media) -- the Live CD should boot, even if you have to push F4 and use Safe Graphics mode.

---

### Post by Sherina on 2009-01-30
I reburned the cd with a new iso and it still does that. Also about doing a clean install could I use do a manual partition in the prepare disk part of the installer and choose "/" as the mounting point like in this tutorial? [http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p22.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p22.html) even though I am dual booting with windows xp

---

### Post by Sherina on 2009-01-30
I downloaded the iso and burned it and the same thing happened I also booted into safe graphics mode again same thing happened. it got stuck and then part of a loading bar appeared above the original bar

---

### Post by dabl on 2009-02-02
> **Sherina said:**
> 
could I use do a manual partition in the prepare disk part of the installer and choose "/" as the mounting point like in this tutorial? [http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p22.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p22.html) even though I am dual booting with windows xp

Yes.

I prefer to use a GParted Live CD and do the hard drive partitioning before I boot a Live CD or Alternate CD for installation.

On your installation CD, it sounds like you have some problem with the burning or else with the blank media quality.  Try a different brand of blank media, and also if you can burn it on a different computer/optical drive you might get a different result.  The problem that you are describing is the classic "bad CD" symptom.

---

### Post by icanfly0307 on 2009-02-02
I had the same problem with the same specs on my laptop. Try adding this to the boot options:

acpi=off apm=off

You can renable acpi and apm after the installation is done

---

### Post by mcloser on 2009-02-02
It is also possible to upgrade from within 7.10 to 8.04/8.10, that's what I did.  I understand if you are hesitant about upgrading if it is hanging on a Live CD load but if it works fine with 7.10 it should have no problems with upgrading using package manager.

goes without saying but of course, backup everything !

PS I also run dual boot XP pro. as I understand it the secret is to always install XP first then Ubu.

ask for more details

---


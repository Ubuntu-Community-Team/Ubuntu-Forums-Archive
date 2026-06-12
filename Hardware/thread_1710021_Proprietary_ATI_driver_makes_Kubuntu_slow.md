---
title: "Proprietary ATI driver makes Kubuntu slow"
date: 2011-03-19
forum: Hardware
---

### Post by SpectrumDT on 2011-03-19
Hello.

I am running a fresh installation of Kubuntu 10.10. I have this problem: Installing ATI driver made my Ubuntu slow.

I have an ATI Radeon HD 5750. I have tried installing the proprietary driver like this:

1. Running "Additional Drivers" (from the K Menu; I don't know the command-line name).
2. Select "ATI/AMD proprietary FGLRX graphics driver".
3. Click "Activate".
4. Reboot.

After rebooting, Catalyst worked but my Kubuntu was significantly slower than before. Switching between desktops or windows took much longer. 

Does anyone know what causes this and if it can be fixed? (I have searched a bit but only found old posts that look outdated.)

Thanks in advance.

**Edit:** I tried disabling desktop effects. That did not help. "top" (from the command line) does not show any processes hogging resources, so I don't know how to debug this.

---

### Post by daiwai on 2011-03-24
I have the same problem with one of my machines at work. :/

---

### Post by Yellow Pasque on 2011-03-24
Try newer Catalyst drivers: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

Remove the old ones first: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

---


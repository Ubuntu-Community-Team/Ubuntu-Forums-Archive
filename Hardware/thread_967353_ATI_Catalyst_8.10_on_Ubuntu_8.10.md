---
title: "ATI Catalyst 8.10 on Ubuntu 8.10"
date: 2008-11-02
forum: Hardware
---

### Post by shevalano on 2008-11-02
I got an odd problem while installing video card driver ATI Catalyst 8.10 on my Ubuntu 8.10 manually.

I completely followed the way Unofficial ATI Linux Driver Wiki told me.
([http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide))
When I excuted "deb dpkg -i fglrx-amdccle.....deb",
I Got:
"Error! Build of fglrx.ko failed for 2.6.27-7-generic"
"Error! Could not locate fglrx.ko for module fglrx in the DKMS tree"...

Finally, when I reboot my PC, Ubuntu told me:
"(EE) module ABI major version (0) doesn't match the server's version (1)"

How could I fix this problem????

---

### Post by adamo on 2008-11-03
I experienced the same behaviour. 
My platform is AMD 64bits and ATI4850... 
A bit strange is that on Ubuntu 8.04 everything was fine with graphics (even compiz was working).

How to fix this ???

---

### Post by shevalano on 2008-11-11
any help?

---

### Post by cutOff on 2008-11-13
Same here. 

Any clue what happening?

My kernel: 2.6.24-20-generic

My graphics card:

```
cutoff@this:~$ sudo lshw -C Video
  *-display               
       description: VGA compatible controller
       product: RS482 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx

```

---

### Post by seapahn on 2008-11-13
I was messing with this last night. I think the one that gets installed with Ubuntu 8.10 is newer (I seem to recall something about 8.543 vs 8.542 for the driver).  I had more luck with the packaged driver that comes with Ubunut 8.10 but still has a lot of problems with dual-head.

ATI has the new 8.11 on their site but I can't fully download it (only get 15MB of the file where it's supposed to be over 72MB). So hopefully that will be fixed later today and will actually install.

Edit: I just tried downloading catalyst 8.11 and it seems to have gone fine. No idea about how it works yet though.

---

### Post by brian77095 on 2008-11-13
> **shevalano said:**
> I got an odd problem while installing video card driver ATI Catalyst 8.10 on my Ubuntu 8.10 manually.

I completely followed the way Unofficial ATI Linux Driver Wiki told me.
([http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide))
When I excuted "deb dpkg -i fglrx-amdccle.....deb",
I Got:
"Error! Build of fglrx.ko failed for 2.6.27-7-generic"
"Error! Could not locate fglrx.ko for module fglrx in the DKMS tree"...

Finally, when I reboot my PC, Ubuntu told me:
"(EE) module ABI major version (0) doesn't match the server's version (1)"

How could I fix this problem????


Wow  Any one know of a simpler way to do this the wiki link about has a lot of steps and seems easy to mess up.  I have dual monitors and my settings will not save so I know I need to update my drivers but dont think I am ready to tackle that links howto just yet....

---

### Post by shevalano on 2008-11-16
But...It seems that Catalyst 8.11 doesn't work on Ubuntu 8.10 either. I got the same problem as Catalyst 8.10

---

### Post by seapahn on 2008-11-24
> **shevalano said:**
> But...It seems that Catalyst 8.11 doesn't work on Ubuntu 8.10 either. I got the same problem as Catalyst 8.10

Sorry for the late reply but I did have luck with Catalyst 8.11 on Ubuntu 8.10. The packages were generated without error but after I installed using dpkg, I had trouble starting X.

So I used the ati installer (by running their package using sudo and letting it install) and then it worked like a charm.  I did have to add fglrx to /etc/default/linux-restricted-modules-common.

I am running 64bit on an Asus M2A-vm HDMI motherboard with a built in ATI x1250 graphics processor. I am using both the HDMI output and DVI as dual head.

---

### Post by adamo on 2008-11-28
Hi,

Just installed Catalyst 8.11 (maybe 10 minutes ago) from amd site ([http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)). In my case (AMD 64bits) it works, i have driver instaled without errors, without magic tricks (only "sh ./ati-driver-installer-8-11-x86.x86_64.run". Nice.
Compiz works too.

Cheers
____
Adam

---


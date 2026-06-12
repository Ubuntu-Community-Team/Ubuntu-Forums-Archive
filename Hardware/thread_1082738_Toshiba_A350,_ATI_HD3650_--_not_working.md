---
title: "Toshiba A350, ATI HD3650 -- not working"
date: 2009-02-28
forum: Hardware
---

### Post by PauGNU on 2009-02-28
Hi

I recently installed Ubuntu in a laptop Toshiba A350 which uses the ATI HD3650 graphics card. The only way to install ubuntu was using the alternate cd because the livecd wasn't able to recognize the graphic card.

Now I'm working using the vesa driver with a very low resolution. I've tried installing the fglrx driver from the repositories or from the binaries, but both times I got a black screen. 

Is there a way to configure this graphic card?. It's really weird because I have other laptop Dell with the same graphic card and it works perfectly with the proprietary driver. Maybe is the screen?

Thanks for your help!

---

### Post by PauGNU on 2009-03-01
Nothing?...

---

### Post by funnyav on 2009-07-27
Same problem. Tried a lot of different things. None work :/

---

### Post by r2-d2 on 2009-07-28
> **funnyav said:**
> Same problem. Tried a lot of different things. None work :/
Same here, using IBM Lenovo T500 with ATI hd3650. Found numbers of workarounds and tips and tricks...none worked. Not even with Catalyst 9.7.

---

### Post by ZaHACKieL on 2009-07-28
Uhmm....the Live CD doesn't recognize the card? But what about if you just go directly to the installation. I remember the Live CD didn't detect some components from my laptop, like the video card or wifi but they did work after I installed it.

I have the HD3650 and you just have to download the drivers from here:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

and go to Linux > Radeon > ATI Radeon HD 3xxx

Try that and let me know what happens

ZL

---

### Post by r2-d2 on 2009-07-30
> **ZaHACKieL said:**
> Uhmm....the Live CD doesn't recognize the card? But what about if you just go directly to the installation. I remember the Live CD didn't detect some components from my laptop, like the video card or wifi but they did work after I installed it.
 
I have the HD3650 and you just have to download the drivers from here:
 
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
 
and go to Linux > Radeon > ATI Radeon HD 3xxx
 
Try that and let me know what happens
 
ZL
 
Tried that as well, ended up dkms error. Installed new linux headers and new kernel, same thing happend. I think it's a memory related thing because POSIX memory share does not work as well. Are you useing 64bit version of Ubuntu ?

---

### Post by KooKooKahbuntu on 2009-12-09
I have tried installing a driver through envyng, the ATI driver and the fglrx driver through "Hardware Drivers".

And then limited the RAM to 2GB.
(as mentioned here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/341681](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/341681))


 Still this does not work for me.


 I am new to using Ubuntu. Am I missing some steps in what should be done?
 I am using Ubuntu 9.10 amd64 and had install and still currently running on the safe graphics (vesa) setting. My computer is the Toshiba A350 laptop with Intel Core 2 Duo Processor P7450 / 4GB SDRAM / ATI Mobility Radeon HD 3650 512 MB.

---


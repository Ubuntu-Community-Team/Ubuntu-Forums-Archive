---
title: "nothing runs!"
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by pentium on 2006-09-19
I just finished installing ubuntu 6.06 LTS and the first thing I was greeted to was no sound and the system not connecting to the internet. Drivers were not loaded for the internal crystal chipset and for the network it is even more strange. The system can see the card but can't connect to the internet. It should be no problem, ver. 5 of ubuntu connected without problem.
Any ideas?

---

### Post by John.Michael.Kane on 2006-09-19
Try posting your system spec's. right now your question is vague at best,and will not garner the help you may need

---

### Post by pentium on 2006-09-19
I am at school but I can easily recall most of the specs.
It is a Digital PC 5000 made by Digital (probably not the real model # but google it anyways).

-256 mb ram
-boosted with powerleap to over 300 mhz. (bios just shows pentium 300)
-ATI Xpert128 PCI video card
-Internal 10/100 network adapter (possibly SMC)
-internal Sound with CRYSTAL chipset (don't know the numbers)
-internal video (disabled)
-usb and ps/2 sockets and the usual serial and parallel
-ASUS PCI SCSI card (Forget model, know it's fine)
...I really don't think the drives are an issue.

I have always had a problem with sound. I have tried PCI and ISA sound blaster cards too but they are not seen. The more I also think, I might have just forgotten to plug the network cable in completely:o 
When I get home I will double check the device list. I swear I enabled sound in the bios.

---

### Post by pentium on 2006-09-19
Yep, the network cable was unplugged.:tongue: 

The chipset is: CRYSTAL CS4236B

I checked the device manager and ubuntu can see the sound chipset. Do I need a driver or something or is it just imcompatible?

---

### Post by John.Michael.Kane on 2006-09-19
CRYSTAL CS4236B should be supported. 

you can try Adding the following line to /etc/modules
**snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5**

make sure to reboot.

---

### Post by pentium on 2006-09-20
Nuts!
I forgot how to give editing privelages to other people! I can't save it now!

---

### Post by enopepsoo on 2006-09-20
try opening the file with sudo:

```
sudo gedit /etc/whatever
```

sudo will give you ultimate rights on a command by command basis.:D

---

### Post by pentium on 2006-09-20
^^thanks for the refresh.

Nope. I still can't get sound.

---

### Post by John.Michael.Kane on 2006-09-20
Is the device using OSS or Alsa

---

### Post by pentium on 2006-09-20
^^^WHAT?

Speak less technical, I am a linux newbie (still).

---

### Post by John.Michael.Kane on 2006-09-20
Right Click on the speaker icon. select preferences. this should tell you what sound mixer is being use.

---

### Post by pentium on 2006-09-20
interesting. It don't list any.

---

### Post by John.Michael.Kane on 2006-09-20
If no sound mixers are listed then it would seem this chip is not being seen properly.

Did you have sound working under 5.10?

---

### Post by pentium on 2006-09-20
nope, sound didn't work then either.

---


---
title: "Hard disk lost during installation"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by mmasroorali on 2007-11-06
Oh, NO, NO, NO. That is the punishment for impatience. I should have never done this.

This evening I tried to install ubuntu 7.10 in my Dell PC with two (sata) hard disks. /dev/sda contained Fedora and /dev/sdb was empty. I wanted to install ubuntu in the second one. During disk resizing (I opted for 20% of size), it was taking so much time. I got impatient at one point (even with the warning before start) and tried a number of mouse clicks (Backward, Forward, Cancel) etc. The installer got stuck and I killed it by clicking repeatedly on the cross button. At that point I had not realized the damage.

Next time I tried to boot the machine, during POST I got a message that SATA 3 is not detected, that means /dev/sdb is not there. Previously this disk has worked fine as a mounted partition. Right now there is no problemetic sound from the disk, so it appears to be soft error (hopefully). 

Could you please tell me how can I get this hard disk back? I can run Fedora in my machine. /deb/sda is completely fine. But the 160 GB Maxtor /dev/sdb is not even detected by BIOS.

Thanks in advance for your help

---

### Post by creeco on 2007-11-06
Sounds like you HD is broken.. Try getting some support from your the reseller you bought it from..

---

### Post by mmasroorali on 2007-11-06
Getting support is not possible due to several reasons (including it was bought in another country and was given to me as a gift). 

Is there any utility I can try?

---

### Post by az on 2007-11-06
> **mmasroorali said:**
> Getting support is not possible due to several reasons (including it was bought in another country and was given to me as a gift). 

Is there any utility I can try?

I can't explain why the drive is no longer detected inthe BIOS.  For any partitioning tools to work, you need to at least have the machine be able to detect that the drive is there.

It doesn't sound like your installation attempt is at fault here.  You need to troubleshoot the drive on a hardware level.

Are the cables plugged in?  What happens if you unplug all the other drives?  Can you force your motherboard to try to detect the drives?

---


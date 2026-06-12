---
title: "the sound card is not dectected"
date: 2004-11-08
forum: Hardware &amp; Laptops
---

### Post by bela on 2004-11-08
Hi, 
My sound card , an isa one, ess1869, is not detected. while knoppix detects automatically  it, or in RH  7.3 I used sndconfig to detect it.  8-[  
how to do it here. sndconfig couldn't use it no longer because it searches for soundcore.o  while in kernel 2.6 and over the name of modules are *.ko.
thanks a lot
bela  :o

---

### Post by ulrich on 2004-11-08
hi,
according to the alsa-project the module is called es18xx.
so what gives
```
modprobe snd-es18xx
```
?

---

### Post by ploum on 2005-04-13
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8852](https://bugzilla.ubuntu.com/show_bug.cgi?id=8852)

---

### Post by nlogax on 2005-04-14
I've got mine working now - I found the fix [here](http://lists.debian.org/debian-user/2005/01/msg03569.html) (a Debian newsgroup) - basically, just create /etc/modprobe.conf (if it doesn't exist) and add the following lines to it:

alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

(your options line may vary, depending on the IRQs, Ports etc but try this if you don't have anything else to go on)
...then run:

modprobe snd-es18xx

It should load successfully, but you may not have sound until you reboot (I didn't).

Also, see the articles here:

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ESS+Technology&card=.&chip=ES18xx&module=es18xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ESS+Technology&card=.&chip=ES18xx&module=es18xx)

[http://www.linuxquestions.org/hcl/showproduct.php?product=470](http://www.linuxquestions.org/hcl/showproduct.php?product=470)

---

### Post by nlogax on 2005-04-17
Actually, I've since done some reading and the preferred way of getting this working is to create a file in /etc/modprobe.d called snd-es18xx and put the following line in it:

options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

(your options line may vary, depending on the IRQs, Ports etc but try this if you don't have anything else to go on)

Whereas, if you do it the way I suggested in my earlier message, you'll probably get a warning that /etc/modprobe.conf exists but doesn't INCLUDE /etc/modprobe.d on boot

---

### Post by nlogax on 2005-04-17
Please see the updated BugZilla article here for a more detailed explanation of the fix etc.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8852](https://bugzilla.ubuntu.com/show_bug.cgi?id=8852)

---


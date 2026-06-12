---
title: "Sound Card not detected"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by albertro on 2005-06-22
Hi veryone

Here is my story.  I have an old Compaq Deskpro EN series Pentium II 350, 256MB Ram, 8GB Herd Drive.  (Please don't laugh, my gaming PC is an AMD64 3000+ 2GBs RAM etc,  but this is just a PC to play around with linux and learn)  I used to have Red Hat 8 for more than a year and worked like a charm.  Yesterday I decide to scratch it and install ubuntu 5.04.  Installation was smooth and everything works perfect but ubuntu don't see my sound card.  This is one of those integrated cards that Compaq put on their PCs.  In Red Hat I configured the card manually telling the sndconfig that was a sound blaster compatible and specifying all the addresses / irqs manually.  Here I don't know how to do it.  Any help will be appreciated.

Thanks

 :roll:

---

### Post by joelito on 2005-06-22
from a root terminal run 
#alsamixer 

disable anything that reads

IEC958 

by pressing the (>) key

That was the solution that worked for me but I'm not sure if will work for you

---

### Post by albertro on 2005-06-23
I try it bu didn't worked.   ](*,)   This is what I got:

root@lin-mix:/usr/bin # alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
root@lin-mix:/usr/bin #

Any other hint? 

Thanks

Alberto

---

### Post by wvslkr on 2005-06-24
I suspect this uses this the es18xx driver as they are pretty common onboard older Compaqs. Open a terminal and try;

sudo modprobe snd-es18xx

If this is accepted without error, that is your module.

To make it permanent, open /etc/modules in an editor and add the line-

snd-es18xx isapnp=0

The isapnp assumes it is an isa bus.  If it is not then it is not necessary.  Your card should work fine from then on.  It is what I use.  If this does't in fact work you will need to find what chipset is used and post back.

GL :)

---

### Post by eMuNiX on 2005-08-05
I have an old Compaq Armada 7400 laptop and have not been able to get the es18xx sound card to work under Ubuntu yet.  I have tried [this threads suggestions](http://www.ubuntuforums.org/showthread.php?t=19307&page=1&pp=10) but no joy.  Everytime the machine boots I get an artsmessage:-

Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.

modprobe snd-es18xx gives an error:-
FATAL: Error inserting snd_es18xx (/lib/modules/2.6.10-5-386/updates/alsa/isa/snd-es18xx.ko): No such device
FATAL: Error running install command for snd_es18xx

Any thoughts?

---

### Post by wvslkr on 2005-08-05
I'm not sure if this will help, but your module search path is different than mine.

Mine is /lib/modules/2.6.10-5-386/kernel/sound/isa.

Check if there is an ess18xx entry in your /lib/modules/2.6.10-5-386/updates/alsa/isa/.
It may not have updated correctly.
There is also an old sound card how to somewhere on the forums.  Quick search will find it for you.

GL :)

---


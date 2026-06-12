---
title: "No Sound from toshiba stellite pro p100-286"
date: 2009-10-31
forum: Hardware
---

### Post by forbzie22 on 2009-10-31
Just installed ubuntu 9.10 which all seems good but no sound.

The laptop has inbuilt harmon kardon speakers.

Anyone know a fix for this, or can point me in the right direction ?

lspci output below for sound 


00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Cheers

---

### Post by Tryfon on 2009-11-01
I have a Satellite A100-003 with the same sound card with you and no sound either. Please help!

Edit: Well, I noticed that if I restart ALSA with the command "sudo alsa force-reload" sound works. But then I have to do that every time I boot up my computer. Any ideas?

---

### Post by Tryfon on 2009-11-01
Ok, I solved the problem in my case by following the instructions here: [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by forbzie22 on 2009-11-01
Thanks for the reply but the link doesnt contain a fix for Toshiba Satellite Pro P100-286

Still unresolved.

---

### Post by Tryfon on 2009-11-01
Check out the following two links, which are also mentioned in the post where I previously linked you to. You should be able to find the solution to your problem there. First step is to identify the chipset of your soundcard, not the computer model. In my case it was the ALC861VD. Just follow the instructions:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by forbzie22 on 2009-11-01
Have checked the lists and mine isnt listed

 cat /proc/asound/card0/codec#* | grep Codec

Codec: Conexant CX20549 (Venice)

Looks like windows will prob have to be re-installed :(

---


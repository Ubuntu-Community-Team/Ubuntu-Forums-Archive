---
title: "Xubuntu, does not install..."
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by ik8vwa on 2008-12-30
I have launched the "boot from cd" option (in order to test the live version from cd without installing) and xubuntu seems to start but then there are a series of errors that appear on the screen and seem to go on without end.
My pc is an old Toshiba laptop with Windows ME and Mobile Intel Celeron 650 mhz, plus 256 mb of ram.
The xubuntu version is 8.10 and it works flawlessly on another pc in the live mode from cd (simulation).
Is my pc completely gone? Or can I try the installation? In the latter case, could I save the pre-existing Windows installation?
Thanks a lot in advance

---

### Post by gettinoriginal on 2008-12-30
What hardware does your Toshiba have, since you mention ME, is the computer that old, or just the OS.  You might try a lighter, or older distribution.  :)

---

### Post by linux_tech on 2008-12-30
Try alternate cd install

[http://mirror.anl.gov/pub/ubuntu-iso.../8.10/release/](http://mirror.anl.gov/pub/ubuntu-iso.../8.10/release/)
select 
PC (Intel x86) alternate install CD

Burn new iso and try to install.

---

### Post by ik8vwa on 2008-12-30
> **linux_tech said:**
> Try alternate cd install

[http://mirror.anl.gov/pub/ubuntu-iso.../8.10/release/](http://mirror.anl.gov/pub/ubuntu-iso.../8.10/release/)
select 
PC (Intel x86) alternate install CD

Burn new iso and try to install.

I have chosen exactly that version and also tested the cd obtained on another pc...so I guess my pc is the faulty one!

---

### Post by ik8vwa on 2008-12-30
> **gettinoriginal said:**
> What hardware does your Toshiba have, since you mention ME, is the computer that old, or just the OS.  You might try a lighter, or older distribution.  :)

First of all thanks for your reply. I'm a totally new fish in this pond and I'm trying to figure out the best steps to begin. Since the distribution I've chosen does not seem to work with my 650 mhz laptop, I have just downloaded the so called "damn small linux" or DSL. I'll let you know if it starts and if it will be able to coesist with windows millennium edition.

---

### Post by Sour Mash on 2008-12-30
Try xubuntu 8.04 - it works on my machine, well it did until I upgraded to 8.10 :-( 

Guess who's reinstalling 8.04 now?

---

### Post by ik8vwa on 2008-12-30
> **Sour Mash said:**
> Try xubuntu 8.04 - it works on my machine, well it did until I upgraded to 8.10 :-( 

Guess who's reinstalling 8.04 now?

Ok, maybe I'll try to find it, thanks

---

### Post by Sour Mash on 2009-01-01
I went back to 8.04 and it's fine again, well apart from a "stall" on boot that means I have to press the screen print button to move on, it's not a major issue just an irritation

---

### Post by Sealbhach on 2009-01-01
> **Sour Mash said:**
> I went back to 8.04 and it's fine again, well apart from a "stall" on boot that means I have to press the screen print button to move on, it's not a major issue just an irritation

Hey Sourmash, did you ever get your internet connection sorted out?


.

---

### Post by Sour Mash on 2009-01-01
Yes and no - I swapped the WiFi card for a 3com one and it worked fine, slower but working and as that machine will not need a fast connection I decided to leave it at that!

What I haven't solved yet is the "stalled" boot where I get a black screen and have to press the screen print button to complete the boot and get a log on screen.

---

### Post by Sealbhach on 2009-01-01
> **Sour Mash said:**
> 
What I haven't solved yet is the "stalled" boot where I get a black screen and have to press the screen print button to complete the boot and get a log on screen.

That's weird, never saw that one before. And it booted up Ok first time you installed 8.04? How did you figure out the Prt Sc solution?

Might be a good idea to start (yet) another thread to ask about this. In your thread, paste the output of the command

```
dmesg
```

This shows all the system messages generated as your computer boots up.


.

---

### Post by Sour Mash on 2009-01-01
I found out through frustrated random key punching :-)

I'll get the machine back from my daughter tomorrow and run dmesg, I've already started another thread, will post out put there :-)

---

### Post by Sealbhach on 2009-01-01
> **Sour Mash said:**
> I found out through frustrated random key punching :-)


Ah yes, similar method to my own.:D


.

---


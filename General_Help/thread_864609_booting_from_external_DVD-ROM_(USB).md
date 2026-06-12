---
title: "booting from external DVD-ROM (USB)"
date: 2008-07-19
forum: General Help
---

### Post by bishman on 2008-07-19
The internal DVD drive on my laptop is broken so I was wondering how I can tell my laptop to boot from the ext dvd drive (USB, NEC-1500A). Laptop is a Compaq N610c (old - and old enough to NOT have the option in the BIOS).

Awesomely enough, I was able to install hardy heron in this way by choosing an option in the windows autorun from the cd that allowed the computer to boot from the cd on the next reboot.

But would be good to know how to do it myself (in the event of getting rid of windows completly). Anyone know?

---

### Post by falcon61102 on 2008-07-19
Have you checked to see if there was an update for the BIOS available from the manufacture?  
That's the only thing I can think of.

---

### Post by bishman on 2008-07-19
hmmm... I was hoping that wouldn't be nessessary given the ubuntu install cd somehow told my computer how to do it (after loading it in windows XP first)... my hope is that there is some command?? thanks anyway - will have a look ;)

---

### Post by falcon61102 on 2008-07-19
If I remember correctly, the Ubuntu CD loads a temporary file onto the harddrive to act as a one time boot loader.  If your system at least recognizes the device at start-up you may be able to play with GRUB a bit and use that.

Personally, I'd try the BIOS thing first.  That's normally a five minute job.  If you have no luck there, then I'd start exploring other means.

---

### Post by bishman on 2008-07-19
Cool thanks. I'm sorted now. T'was an option in the BIOS to enable multiboot from the multibay and if the dvd drive is plugged in, it will appear as an option in a list unpon booting. I could swear I tried this before but apparently I've done something different this time.

Now I can get on with wiping over windows!

---

### Post by falcon61102 on 2008-07-19
Lol... glad you got it working.  And with all those options its really easy to miss one anyway.  Good luck and congrats on losing windows.

---


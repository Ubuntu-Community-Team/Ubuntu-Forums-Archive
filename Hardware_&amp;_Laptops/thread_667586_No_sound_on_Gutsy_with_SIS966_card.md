---
title: "No sound on Gutsy with SIS966 card"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by alan_18 on 2008-01-14
I've got Gutsy installed on my Packard Bell Easynote with an SIS966 soundcard, but I have NO sounds at all.  Not even system beeps.  I'm new to Linux, so I have no idea how to fix this.  I'd appreciate any help.

---

### Post by Yellow Pasque on 2008-01-14
What sound device do you have? SiS966 is the name of the southbridge, which supports "HDA/Azalia" audio as well as older AC97 sound devices/chips.
Please run the following and paste outpt from lspci command:
```
sudo update-pciids
sudo lspci | grep Audio
```
(try grep audio or just run lspci if that command doesn't give you output)

---

### Post by alan_18 on 2008-01-15
alan@alan-laptop:~$ sudo lspci | grep Audio
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller

That's what came up.

---

### Post by Yellow Pasque on 2008-01-15
Try adding "options snd-hda-intel model=laptop" to your /etc/modprobe.d/alsa-base file (open file with sudo gedit). Save, reboot. See if that helps.

---

### Post by alan_18 on 2008-01-15
SUCCESS!!!!  Thank you!  I've got sound now.  All that's left to do is figure out how to get it out of 800x600 resolution.

---

### Post by jojotjuh on 2008-05-04
> **alan_18 said:**
> SUCCESS!!!!  Thank you!  I've got sound now.  All that's left to do is figure out how to get it out of 800x600 resolution.

you can do that through configuration scrreen->screen size
or, you might need newer video card drivers. try updating your system if you haven't done so already.

I'm sorry if any names are incorrect, I have the dutch version of 8.04

---

### Post by iainrowe on 2008-07-21
hi,

is there a simple step by step i can take for this as i am having same problem and i am a total newbie.

thanks

---


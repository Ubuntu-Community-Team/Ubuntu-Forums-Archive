---
title: "ubuntu disk blank screen."
date: 2008-08-09
forum: General Help
---

### Post by li10 on 2008-08-09
when I load the ubuntu live disk, I choose run/install ubuntu, it loads and then leaves me at a blank, black screen with a blinking underscore in the top left of the screen. Accepts no input and does nothing. I checked the disk for errors and it was fine. 

any help would be appreciated.

---

### Post by Ryadt on 2008-08-09
You probably will have to install using the alternate cd. Download it from the Ubuntu homepage.

---

### Post by phidia on 2008-08-09
What are your systems specs and what version # of ubuntu are you attempting to use?

Can you get a commandline (CLI) by pressing Ctrl+Alt+F1 (also try F2-F7)?
If that key combination opens the commandline you can try to reconfigure your xserver by entering > sudo dpkg-reconfigure -phigh xserver-xorg
Hope that helps.

---

### Post by li10 on 2008-08-09
The computer's got 384MB of RAM, pentium 3 processor 300mhz. 

I'll try to get to the commandline.

---

### Post by Sycron on 2008-08-09
Your ram is OK , but CPU is a bit slower... You may try alternate CD , or another lightweight distro like Zenwalk or Puppylinux.

---

### Post by li10 on 2008-08-09
I pressed F6 and it brought up a line where I could write, it was like to boot or something. I wrote 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and I ended up at a blank screen. No blinking underscore either.

I forgot to say, it's 7.04, I think.

---

### Post by Sycron on 2008-08-09
You may try the alternate CD.

---

### Post by li10 on 2008-08-09
ok, thanks. Any other suggestions are welcome, though.

---

### Post by li10 on 2008-08-11
the hard drive makes the clicking noise even when the ubuntu CD isn't in the disk drive, which according to wikipedia means it's failed catastrophically. But why's this making the BIOS really slow? 

also, I read something about masters and slaves, about computer drives. The computer has two IDEs (ATA cables), primary and secondary. I connected the hard drive to the secondary IDE, this would make the CD drive the master and the hard drive the slave, right? Which isn't right, I think, they need to be on the same cable, and the hard drive first. Is that right?#

Also, I made an Xubuntu CD, put it in and rebooted the thing. The BIOS just says 'boot failed, system halted'.

---

### Post by vivicawikc2 on 2011-01-15
> **li10 said:**
> when I load the ubuntu live disk, I choose run/[[COLOR=#000000]install[/COLOR]](http://www.****************.com/sony-psp-video-format/convert-mkv-video-to-sony-psp-format.html) ubuntu, it loads and then leaves me at a blank, black screen with a blinking underscore in the top left of the screen. Accepts no input and does nothing. I checked the disk for errors and it was fine. any help would be appreciated.I still wonder why though I already got it solved, Thanks for your help!

---


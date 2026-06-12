---
title: "black screen, 1 cursor, no error msg"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by Cenci-Thomas on 2009-01-06
Hello. Windows tech attempting to make the jump here. Downloaded the ISO, checksum passed; tested the burned CD on my laptop, verified good; but when I boot to the CD in my desktop, any option I pick (Try Ubuntu without installing, Install Ubuntu, Verify CD) results in a blank screen with a cursor in the upper left-hand corner, and no further response until I cold-boot. Searched the forums but didn't see anything similar. Has anyone seen this?


motherboard: ASUS P4S800D-X
processor:   Pentium 4 2.80 GHz
RAM:         1 GB
IDE HDD:     WDC WD800AB-00CBA0 80GB
optical 1:   Sony DVD-RW DRU-180A
optical 2:   ATAPI CD-RW 52x24 (generic)


Any help greatly appreciated :) thanks.

---

### Post by gettinoriginal on 2009-01-06
When the cursor shows up, try these:

```
 startx 
```

then if that fails, try

```
 sudo dpkg --configure xserver-xorg 
```

---

### Post by cencithomas on 2009-01-06
Thanks :) I should've clarified though, there's no actual command prompt and the keyboard isn't taking any input. It's literally just a blinking dash...

---

### Post by theozzlives on 2009-01-06
when you boot the CD and get to the main menu, hit F4 and choose safe video mode

---

### Post by Rithmarin on 2009-01-06
What video card are you using? There seem to be quite a few reports of blank screens with the packages on the installation CD. 

If the safe graphics mode doesnt work, heres what I did to fix mine:

when you get to the blinking prompt try CTRL-ALT-F1 (or F2) to select one of the console windows which hopefully will give you a login prompt. Login and run "sudo apt-get update && sudo apt-get upgrade" to get updates and reboot.

---


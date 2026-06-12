---
title: "graphical display missing on live session"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by reldon on 2009-01-19
Hello,

I am trying to set up a dual boot on my Windows system but have run into a snag.

When I boot my computer using the Ubuntu live DVD it gets to the place where the desktop screen would show but then goes blank.  My monitor shows a VGA signal but nothing is displayed.  I can get to a terminal session with "CTRL+ALT+F1" and there is the command prompt so I know that it is running but am unable to get the graphical window to show.  Using "ALT+F7" just takes me back to the blank screen.  I tried running ubiquity from the tty1 session but it says "cannot open display"

I have tried using the F4 option to select "safe graphics mode" but with the same result.

Any suggestions??

---

### Post by mikewhatever on 2009-01-19
What are your computer specs, CPU, RAM, graphics?

---

### Post by dff3bc on 2009-01-19
Ok...same problem.

Intel T9300
2GB RAM
NVidia 8800m GTX

---

### Post by mikewhatever on 2009-01-19
> **dff3bc said:**
> Ok...same problem.

Intel T9300
2GB RAM
NVidia 8800m GTX

One possible explanation may be that the open source driver on the Live cd doesn't support your graphics card, hence no graphical environment from the live cd. That said, the restricted drivers from the repositories have 8800m GTX listed, both nvidia-glx-177 and nvidia-glx-180.
To get around that problem, use the Alternate installation CD, and once Ubuntu is installed, manually install the driver.

---

### Post by reldon on 2009-01-19
I am using a desktop with:

M/B Asus: P5LD2-VM w/onboard video, sound, and ethernet
     CPU: Celeron D 3.06GHz
 Grapics: Intel 945G
     Ram: 4GiB
     H/D: Western Digital SATA 128GiB and 400GiB
Mouse/Kb: Microsoft usb wiresless desktop

I have tried all options including vga=771 with same result.

---

### Post by mikewhatever on 2009-01-21
Don't know, Intel GMA 950 should be working out of the box. Did you try checking the live cd for errors?

---

### Post by reldon on 2009-01-23
Sorry to take so long to reply.  

Yes, I did do a check.  If I disable quiet and splash the last line shows "loading ubquity.." then hangs.

---


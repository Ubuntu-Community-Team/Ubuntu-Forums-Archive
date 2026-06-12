---
title: "Display problems in Natty with custom HW and LVDS"
date: 2011-05-27
forum: Hardware
---

### Post by Turifuzz on 2011-05-27
Hi
 
I'm struggling with a custom-made carrier board for Congatec QA6 Qseven module running Atom E660T and Intel EG20 chipset, more info here: [http://www.congatec.com/qa6.html](http://www.congatec.com/qa6.html).
 
18-bit 5.7" LVDS panel is connected directly to the module data lines and I'm encountering interesting problems with grub and tty output. Resolution should be panel's native 640x480, but I have five top lines duplicated at the bottom of the screen. Could this be something about Ubuntu trying to run 24-bit data on 18-bit display (the fourth data signal pair is not connected) or just about resolution?
 
Also, Natty's GRUB entry with line "set gfxpayload=$linux_gfx_mode" got me to blank boot screen and ttys, but fixed it with "GRUB_GFXPAYLOAD_LINUX=text" in /etc/default/grub.
 
Any help appreciated, I've been banging my head on keyboard and don't know where to start.
 
Edit: Let me point out that carrier board only routes signals to external connectors and provides power, thus EG20 drivers are all that's needed. BIOS screen is ok without those duplicate lines, so this problem exists only in Linux.

Second edit: It was BIOS after all, needed some tricky cfg

---

### Post by cdwilson on 2012-11-05
Can you describe how you got things working with the Congatec QA6 Qseven module?  I'm working with the conga-QEVAL board and QA6 module, but after the CD-ROM installer finishes and tries to boot off the HDD, I get no graphics output on the DVI output.  I have no idea if anything is actually booting, or if it's just a display problem.  

If you can detail the steps you got to get the QA6 running Ubuntu, it would help me out tremendously...I'm banging my head on the keyboard too :)

---


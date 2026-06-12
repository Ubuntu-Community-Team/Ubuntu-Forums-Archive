---
title: "ATI 1250 no console"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by Timbers2k on 2007-10-25
I have a ASUS V3-M2A690G AM2 barebones system that I'm setting up for someone. It has the ATI Radeon 1250 IGS and I've had a lot of trouble getting it running. I finally got it installed using the Ubuntu 7.10 Alt CD, then installed the fglrx by booting from the CD in recover mode, since GDM would not start and there was no display at all. Well, it's finally running, and I've even got direct rendering working! 

However, that doesn't mean everything is right. I have no consoles at all, so hitting Ctrl+Alt+F1, F2, etc. only shows a blank screen. I can hit Alt+F7 to get back to the Gnome desktop. The problem starts during the boot process. When the PC is turned on you can see the BIOS splash screen, then grub comes up, then it says "Loading..". Then the screen goes blank with no indication that anything is happening, except for disk activity. Then suddenly the GDM login screen appears and you can log in just fine. The only thing missing is the consoles. 

Does the boot process use some fancy frame buffer display? If so, is there some way to shut it off? Anyone know any way to just get the consoles back?

Thanks,
Tim

---

### Post by Nikos.Alexandris on 2007-10-25
Did you try to install the newly released ATI driver?

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by Timbers2k on 2007-10-25
No, I haven't tried the latest driver. I prefer to stay with the one supplied by the restricted manager, but if I have to load the latest one I will. Anyone know if this will fix my issue?

---

### Post by Timbers2k on 2007-10-30
Anyone using the ATI 1250 have the same issue with no text console?

---

### Post by Nikos.Alexandris on 2007-10-30
Maybe it will help you... or maybe it will mess you up further. Have a look... 

[[COLOR="Blue"]http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

and... [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=3609271&mode=threaded&highlight=ati+1250#post3609271[/COLOR]]("http://ubuntuforums.org/showthread.php?p=3609271&mode=threaded&highlight=ati+1250#post3609271")

---

### Post by Timbers2k on 2007-10-30
I've checked all those links, and no one mentions a problem with the text consoles! I have the fglrx driver working for X and opengl, just no consoles. The system has a wide screen display, so maybe the text is coming up in a mode it does not support. How do you configure the setting for the text consoles before X starts?

---

### Post by jsully1 on 2007-10-30
This will probably be related to your grub settings.  Carefully do a "sudo nano /boot/grub/menu.lst" and scroll down to your first kernel that's listed - if this is a fresh Gutsy install it should be Ubuntu 7.10, kernel 2.6.22-14 generic.
Go to the kernel line - what options are there?
On mine at the end I've changed it to ro splash vga=794
vga 794 tells it to use 1280x1024, 16bit - you may also want to try it without any vga options.

---

### Post by Timbers2k on 2007-11-04
Finally got back to this PC. It has no vga options in grub for the kernel. This seems like a good line to investigate, so I'll try some different values there and see what happens. Thanks.

---

### Post by larseko on 2007-12-11
Did you find a solution to this? Thanks.

---


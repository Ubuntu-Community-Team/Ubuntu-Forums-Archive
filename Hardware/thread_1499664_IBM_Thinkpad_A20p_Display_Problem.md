---
title: "IBM Thinkpad A20p Display Problem"
date: 2010-06-02
forum: Hardware
---

### Post by Gary128 on 2010-06-02
I have tried to install 10.04 on an IBM Thinkpad A20p (very old machine).  The display misbehaves right from CD boot.  It is as if the display were divided into vertical sections and some are shown twice, others not at all.

I guess this is an ATI driver problem.  Is there a simple workaround, or should I just junk this machine?

---

### Post by utnubuuser on 2010-06-02
Have you tried the "nomodeset" fix?

Here's one how-to:[http://www.absolutelytech.com/2010/05/01/solved-blank-screen-while-booting-lucid-lynx-on-older-ati-graphics/]("http://www.absolutelytech.com/2010/05/01/solved-blank-screen-while-booting-lucid-lynx-on-older-ati-graphics/")

Might help, might not.\\

The easiest way to check the nomodeset fix is to select the kernel to boot in grub, while selected, press e then use the arrow keys to scroll to the line that begins with 'kernel', then scroll to the end of that line and add nomodeset after quiet splash, then cntrl+x to boot.

---

### Post by Gary128 on 2010-06-03
Sadly, this did not work.  My previous experience with a non-cooperating graphics card (the infamous SiS 671) makes me wary of wasting further time on this.  Thanks anyway.

If anyone has solved this specific problem, I would like to hear from you.

---

### Post by utnubuuser on 2010-06-04
What about using the vesa driver instead?  Should work on darn near any hardware, though there's not much to be had by way of performance...

I think you can ask the machine to use it by creating a xorg.conf file and specifying vesa as the driver..

---

### Post by zean1 on 2010-07-29
I have the same problem and until i find a better way I select to boot into _Recovery mode_ then scroll down to _failsafeX_ Run in failsafe graphic mode **click ok** then put a dot in _Run ubuntu in low-graphics mode for just one session_ **click ok** then everything seems to be running ok.
 witch i think make it run using that VESA driver but don't no for sure all tho at 
   [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
under 6.[Troubleshooting]("https://wiki.ubuntu.com/WubiGuide#Troubleshooting") 
                  4.[ Other boot or video problems]("https://wiki.ubuntu.com/WubiGuide#Other%20boot%20or%20video%20problems")
                  8.[Video Problems after second reboot]("https://wiki.ubuntu.com/WubiGuide#Video%20Problems%20after%20second%20reboot")
but i haven't figured out how to do those or they don't work 
         
   P.S If someone No's a better fix or more permanent fix so i dont have to do all that every time i boot i could use the help thanx

---

### Post by utnubuuser on 2010-07-31
You'd have to create a xorg.conf file(plenty of how to around for that), and put something like:> Section "Device"
Identifier "ATI"
Driver "Vesa"
EndSection
Though you might want to check around.  - It's easy enough to try, and if it doesn't work, easy to undo.

This is how my Hardy xorg.conf is configured:> Section "Device"
Identifier "ATI"
Driver "ati"
Option "AGPMode" "4"
Option "AGPFastWrite" "yes"
Option "AGPSize" "16"
Option "EnablePageFlip" "on"
Option "RenderAccel" "on"
Option "DynamicClocks" "on"
Option "BIOSHotkeys" "on"
EndSection

Switch out ATI for Vesa, delete the various options, reboot and see. (PS. there is a proper way to create an xorg file for Lucid, check the Wiki or read this:[QUOTE][http://ubuntuforums.org/showthread.php?t=1428788]("http://ubuntuforums.org/showthread.php?t=1428788")

You might also like to post the output of:> lspci | grep ATI so people can see which card/chipset your trying to configure.

---


---
title: "nvidia geforce 9800gt"
date: 2011-10-05
forum: Hardware
---

### Post by MilesEpps on 2011-10-05
I have recently upgraded to an nvidia geforce 9800gt, but when i turn it on I just get black screen. On my monitor there is a green LED that is flashing (this usually happens when my monitor is on but my computer isn't or it isn't connected. I am using a small dvi to vga (or D-SUB?(the little blue one)) adaptor could this be the problem?

---

### Post by oldfred on 2011-10-05
I have a 9600GT and have to use nomodeset. Early versions just put monitor to sleep & system was still installing. I only knew that as I used USB flash and I could see it was still working for a long time. Then recent versions just seem to have black screen. But once nVidia driver is installed it works great.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

---

### Post by MilesEpps on 2011-10-05
I think the problem might be my adapter, should i use a bigger "proper" one

---

### Post by MilesEpps on 2011-10-05
I have tried to use a boot cd but i still have black screen , could it be my adapter?

---

### Post by oldfred on 2011-10-05
My monitor uses DVI and I just used the cable that came with the card. Not sure if adapter makes a difference or not. 

Did you use nomodeset?

---

### Post by MilesEpps on 2011-10-06
I can't my screen is black (I have an adapter because my monitor is vga), boot cd's don't work. the led light on my monitor is flashing (meaning that my monitor is not connected to my computer) but it is connected. Is it possible that there isn't enough power supply, I have a pretty old computer (i don't know exactly what computer because i can't find it online but it's an imedia) so... + I get 1 long beep and three short beeps on startup.

---

### Post by oldfred on 2011-10-06
Beeps from motherboard mean something, but without manual it is difficult to tell exactly what that is. But it sound like it is telling you something is not connected or has failed.

Double check that all connections are secure. Sometimes removing memory, cleaning & replacing, and just confirming everything is correctly installed.

---

### Post by SeijiSensei on 2011-10-06
> **MilesEpps said:**
> Is it possible that there isn't enough power supply, I have a pretty old computer (i don't know exactly what computer because i can't find it online but it's an imedia) so... + I get 1 long beep and three short beeps on startup.

I'd guess that it's a power problem, too.  Modern video cards like a lot of watts. I'd suggest visiting the manufacturer's site and see if you can read a manual for your computer online.  It may tell you what the one-long/three-short code means.

---

### Post by MilesEpps on 2011-10-06
the problem is, i don't know what computer i have so figuring things like this out is pretty hard.

---


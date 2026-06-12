---
title: "Installation problem on SIS 630 Display Via C3"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by peeyushd on 2009-06-04
Hi,

I am trying to install Ubuntu 9.04 on an old PC at my home having Via C3 733 MHz processor with 384 MB SDRAM on SiS 630 chipset and display adapter. Currently the machine is running Windows 2000 workstation without any problems. But when I try to install ubuntu after doing initial the screen black outs. I tried installing with Safe Display Mode, I got some screens but then some errors in text mode and then computer hanged.

Though I am known to Linux and have used it for some time back in 2003. But trying it again. So anyone can please help me on the issue....

peeyush

---

### Post by peeyushd on 2009-06-05
Hello Everyone

Still waiting for some response....:o

Peeyush

---

### Post by overdrank on 2009-06-05
Hi and you may try the alternate cd for the install, also you may look at Hardy 8.04 as it maybe easier for that graphics chipset.
[Ubuntu 8.04.2 LTS]("http://releases.ubuntu.com/hardy/")
[Ubuntu 9.04]("http://releases.ubuntu.com/jaunty/")

---

### Post by peeyushd on 2009-06-05
Hi 

Thanx, I am downloading Alternate CD image of **9.04**. Where can I find instructions on how to use alternate CD?

I also understand that 8.04 LTS needs atleast 384 MB RAM, but in my PC 16MB is shared with the processor.

Regards

Peeyush

---

### Post by overdrank on 2009-06-05
> **peeyushd said:**
> Hi 

Thanx, I am downloading Alternate CD image of **9.04**. Where can I find instructions on how to use alternate CD?

I also understand that 8.04 LTS needs atleast 384 MB RAM, but in my PC 16MB is shared with the processor.

Regards

Peeyush

[Installation using the Alternate CD]("https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD")
Also Hardy 8.04 is recommended to use 384 mb but using the alternate cd for the install should help. I was just making a suggestion for the easy of configuring the   SIS 630 graphics as there are many threads with Jaunty and that graphics.
I believe you mean the 16mb is shared with the graphics :)

---

### Post by peeyushd on 2009-06-06
Hi

The alternate CD is not helping. Again after starting the installation Screen blurs and computer hangs. So should I try downloading 8.04 LTS or take any other step??

And yes I meant 16MB is shared with Graphics.:)

Regards

Peeyush

---

### Post by peeyushd on 2009-06-08
Still unresolved

I have downloaded 8.04 LTS and was able to get the Live Desktop of Ubuntu by selecting "Safe Graphics Mode". Desktop is working well with 800x600 resolution, sound is working. But there is problem with the installation. 

The installation programs is reacting very random. It just closes down without any error message or info at any step. Like sometimes it stops at Time Zone selection, sometimes at Partition Manager, sometimes at copying files, at one time the installation was through to 90% and it stopped working when the Hardware Installation was going on.

So I am unable to understand where exactly the problem is? So what to do next, is there any other installation method of 8.04 LTS?

Thanx & Regards

---

### Post by overdrank on 2009-06-08
> **peeyushd said:**
> Still unresolved

I have downloaded 8.04 LTS and was able to get the Live Desktop of Ubuntu by selecting "Safe Graphics Mode". Desktop is working well with 800x600 resolution, sound is working. But there is problem with the installation. 

The installation programs is reacting very random. It just closes down without any error message or info at any step. Like sometimes it stops at Time Zone selection, sometimes at Partition Manager, sometimes at copying files, at one time the installation was through to 90% and it stopped working when the Hardware Installation was going on.

So I am unable to understand where exactly the problem is? So what to do next, is there any other installation method of 8.04 LTS?

Thanx & Regards

Hi and have you checked the cd for errors? You may also want to [HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") on the iso you downloaded.
Have you tried the alternate cd install for Hardy?

---

### Post by prshah on 2009-06-09
> **peeyushd said:**
> 
But when I try to install ubuntu after doing initial the screen black outs. I tried installing with Safe Display Mode, I got some screens but then some errors in text mode and then computer hanged.

There are known problems with Sis 630 in 24 bit (true color) mode, which is the default mode (especially if the VESA driver is in use).

You need to switch to 16 bit color (High color) mode.

This gets a little complicated in 9.04, so it's better you try this with 8.04.2 (8.04 LTS)

Try to get a desktop using the live CD (Even safe display is OK).

Then, switch to a virtual terminal using Ctrl+Alt+F1. Edit the /etc/X11/xorg.conf file with the command ```
sudo pico /etc/X11/xorg.conf
```

Find the below piece of code in the file, and add the line in red. Don't change any lines that are already there.```
Section "Screen"
...
...
[color=red]DefaultDepth      16[/color]
EndSection
```

Then, save and exit (Ctrl+X, Enter)

Then, give this command to restart the GUI mode```

sudo /etc/init.d/gdm restart
```

You should be back in GUI mode within a few seconds, otherwise, press Ctrl+Alt+F7.

Now try installing. 

If the installation completes, you may have to repeat the procedure once after rebooting your installed system.

If you run into problems, please post back with details.

---

### Post by peeyushd on 2009-06-13
> **prshah said:**
> If the installation completes, you may have to repeat the procedure once after rebooting your installed system.

If you run into problems, please post back with details.

Hi

I have tried all things you have told, but still installation doesnot completes. I was able to get 16 bit depth for the screen, then I tried installing Ubuntu 8.04.2 LTS but the same problem of installation stopping without any error message. One thing I have noticed is that there is no particular place of installation stopping i.e. it stops sometimes at partition manager, sometimes at copying files, sometimes at formatting.

What to do next? Is there any other way to do it? Should I try some older version?

Peeyush

---

### Post by peeyushd on 2009-06-15
Hello Everyone

Any Help???? Hey prshah where are you????:o

Peeyush

---


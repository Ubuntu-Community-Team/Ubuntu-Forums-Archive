---
title: "Dual Boot Windows 7rc and 9.04"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by inxs on 2009-07-09
I am a newb to ubuntu, so I installed windows 7rc and 9.04 on separate partitions of my 320 GB drive on my laptop. 

I do not want to manually select the OS every time I boot up the laptop.  I want the laptop to automatically select Windows within ~5 seconds or allow me to hit a key so I can choose between Windows or 9.04.  I would like to easily change the primary OS once I get accustomed to Ubuntu.

What program will easily allow me to set up this type of configuration?  I don't care if it is a Windows or Ubuntu application right now.

Thanks for your help.

 My laptop is a thinkpad t61, although that shouldn't make much of a difference.

---

### Post by louieb on 2009-07-09
Grub the boot manager installed with Ubuntu  can be set up to do just that. 

Probably the easiest way to set up grub is to open  System>administration>Synaptic Package Manager. and install the package **starupmanager **. You can use it to configure Gurb.

I just manually edit /boot/grub/menu.lst  [GrubHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/GrubHowto#head-1296ce2b184032373f19ad50a91d506eb886ac5f") 

.

---

### Post by Mark Phelps on 2009-07-10
> **inxs said:**
> I do not want to manually select the OS every time I boot up the laptop.  I want the laptop to automatically select Windows within ~5 seconds or allow me to hit a key so I can choose between Windows or 9.04.

Actually, you don't need a program in order to do this.  There is a GRUB boot menu that is hidden by default and it also selects the first OS in the list by default.

To change both, open a terminal, cd to /boot/grub , and edit your menu.lst file by entering "gksudo gedit menu.lst".

Once in the file, you will find a line that says "default" with a number, usually "0" (zero).  You need to change that to the stanza # that matches your MS Windows entry.  You may have to experiment to get it right.

After you have it booting into MS Windows by default, you might want to ensure that the boot menu is hidden but also be sure to set the time to something like 3 seconds.

After this, when you boot, you will have 3 seconds to press the Esc key to bring up the GRUB menu, otherwise, the laptop will boot straight into MS Windows.

and BTW, I'm also quite impressed with the improvements of Seven over Vista and plan on replacing ALL of my Vista installs with Seven.

---


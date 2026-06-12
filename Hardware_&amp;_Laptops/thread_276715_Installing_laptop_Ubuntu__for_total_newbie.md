---
title: "Installing laptop Ubuntu  for total newbie"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by tuqann on 2006-10-13
I've been reading everything I can, half of which I can't understand at all (though it's listed under absolute beginner).

I have having major problems starting Ubuntu's installation. Not that I managed to install it, the most of seen of Ubuntu is the prompt "ubuntu@ubuntu$" and nothing I've found so far remotely prepared me to what I'm seeing right now.

Problem:
I put the CD, it boots, I get the simple graphical menu to select
-start/install ubuntu
-start in simple graphical mode
-etc
-etc

Regardless of what I try, the installation goes nowhere. Tried windows linux installation, the instulix program didn't help, I still get the graphical error and it stop there.
If there is a command-line, I'm no linux wiz, please spoon feed me any help.

My problem originates from the fact that I have XP installed before, something I cannot tamper with, and it's a laptop (laptop section didn't help as everything I found about my modul there starts AFTER ubuntu is installed).

It's a Fujitsu Siemens Amilo M 1437g with ATI x700 graphics and a SATA.

Thanks for the help in advance, and sorry if I sound bitter, but I'm getting very agitated with this...:evil:

---

### Post by onioneater36 on 2006-10-13
I doubt this will help, but its worth a try.  I had the same problem and I had to go into my BIOS and DISABLE LEGACY USB.  Whenever Legacy USB is enabled on my machine, I cannot boot and Ubuntu LiveCD.

---

### Post by Kateikyoushi on 2006-10-13
I think it is because of your VGA, try the alternate install cd to install in text mode. Then you can get the correct driver for your X700.

---

### Post by tuqann on 2006-10-13
is there a walkthrough on how to use it, somewhere where I can look for that?

---

### Post by Sef on 2006-10-13
Have you checked out Herman's [Illustrated Dual Boot Site?]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Frazer on 2006-10-17
Could it be a graphical problem?  I have to use text mode to install on my desktop and then use the command line loggin to get drivers before I can display GDM.  Install in text mode and pick the screen sizes you know you can use.  If you can get through text mode with it all installed then you may be able to grab graphics drivers from the recovery mode.

I use a Nvidia 6800 GS

to get my drivers I have to

sudo apt-get install nvidia-glx

Then to activate it I have to do 

sudo nano /ect/X11/xorg.conf

scroll down to where it says the video card I think its under device 

change the driver from 'nv' to 'nvidia'

I am not sure how to do this on anything thats not nvidia

---------------------------------------------------

edit just saw you got ATI sorry, Im waiting for a laptop with an ATI card (x1600) to get to me (should be this week yay)  If I get it working ill reply here

---

### Post by hawk88 on 2006-10-28
i don't no if you already solved the problem, but i've the same laptop, an this method worked for me.

- just boot form the live cd
- wait untill you get the gdm erro
- pres Ctrl Alt F2
- first type "clear" and press [enter] ( just to clean the console )
- then type sudo apt-get update [enter]
- then: sudo apt-get install xorg-driver-fglrx
- then: sudo aticonfig --initial [enter]
- then: sudo aticonfig -ovt=Xv   [enter]
- then: startx                   [enter]

X sould be working right now, just install ubuntu en after rebooting repeat the hole thing

---

### Post by esaym on 2006-10-28
> **Sef said:**
> Have you checked out Herman's [Illustrated Dual Boot Site?]("http://users.bigpond.net.au/hermanzone/")

wow  i didn't know i could have installed ubuntu with lilo ](*,) ](*,)

---


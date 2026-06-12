---
title: "No GUI in breezy stuck at command line"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by edifuzzy on 2005-10-14
Basically did fresh install of Breezy 5.1 last night......get an error message after ubuntu splash screen..

I think it is related to my X800XL (I have done some research and other people have problems with this card)

""Failed to start the X server (your graphical interface).It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?   Yes    No""

selecting  "yes"  takes me to this next bit!!

""X Window System Version 6.8.2 (Ubuntu 6.8.2-77 [email]20051010174523root@vernadsky.buil[/email]dd)
release date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating system: Linux Ubuntu  2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
          Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
          to make sure that you have the latest version.
Module Loader Present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
Markers: (--) probed, (**) from config file, (==) default setting
                                   <Ok>""

when I click "OK" it asks if I want to view detailed x server output as well and then gives me exactly the same crap!!!!

Then it goes on to say

"The X Server is now disabled. Restart GDM when it is configured correctly"

I'm a bit of a noob at linux and spent hours last night learning how to navigate from a command prompt....

I also tried to download the newest ATI proprietary drivers but got an anti-leech warning....

I have tried editing my xorg.conf file but no luck

just tried the startx command from the resulting command promt and no go...noticed a log file being spewed out and looked at it..

last 3 lines were

""(EE) No drivers available.
Fatal server error:
No screens found""

I'm getting very pissed off......but more determined!!

Any ideas.....I will continue searching!!

---

### Post by Anchovie on 2005-10-14
When you are in the command line, try "sudo apt-get install xorg-driver-fglrx". See if you can get the driver that way. Afterwards, do "sudo nano /etc/X11/xorg.conf" and go to line 75, it should say "Driver: "ati (or whatever)"", replace the string with "fglrx", Ctrl + X, Y, and Enter, Enter to save, try startx again.

---

### Post by edifuzzy on 2005-10-14
I have been through the log file again(and put all back to default) and it seems to mention every single ATI card that I can think off...both AGP and PCIE (mine is PCIE) that I can think of but no mention of X800XL at all...

I believe that mine is an R430  chip....can I tell it that it is and R430 SE or XTP just so that I can get into a GUI to download drivers!!

Anchovie thanks for getting back to me so quickly....will try sudo thing.....already changed ati to fglrx in config already but didn't have fglrx package installed....duh!!! lol!will give it a go...thanks..

---

### Post by edifuzzy on 2005-10-14
Anchovie......F**k me you are a genius I want to have your babies!!!!

It works...thanks a lot mate!!!!!

Is this just one of those thing that all noobs with X800XL's ask??

---

### Post by hotcorrado1 on 2006-01-16
ok i am having basically tha same problem. i have an msi k8neon4 board with an x600 pcie with tv out adaptor: 
i loaded a fresh install of hoary x_64 version, no dice, cannot detect device.
so i put my old rage II+dvd(pci) all in wonder in and did another install.
everything works great.
i used apt-get to update everything, including adding kde. (kubuntu) so i then i had breezy(plus a lot of packages i thought i would like.
so i wanted to get the tv card to work, or at least my pcie card. so i followed the how to on here and installed the ati drivers from the ati website. 
now i am all hosed up again
stuck in console no matter what i do.
i have tried editing xfree86 and xorg config files with no luck. i there a way to post my log files on here from console? i am sure that would help people help me.

from what i can see, when i try to rerun the ati installer, it is asking for an older version of Xfree86. 
i have ver 4.5.0 and on the install notes it says 4.1,4.2 and 4.3 and i think only one of those works with 64 bit. i am a noob, but learning quickly (at the cost of doing my homework). 
can anyone give me an idea where to start? i have been looking through a lot of forums, so i have been trying a LOT of things.
:confused:

---


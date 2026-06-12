---
title: "can't install ubuntu 9.10"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by tony12 on 2009-11-01
Hi Everyone!

I've been trying to install  ubuntu 9.10 but without success so far. The problem is when I get to the page of PREPARE PARTITION it is blank, there are no options.
I don't have that problem when I have installed,again, the ubuntu 9.04.

Please help.

Thank you

---

### Post by Ginsu543 on 2009-11-02
You may be having the same problem I'm having, which is getting the installer to recognize your hdds. You might want to try this and see if it works for you:

1) Run Ubuntu 9.10 using the Live CD
2) Once you are in the live session, open a terminal
3) Remove dmraid by typing "sudo apt-get remove dmraid" at the command line
4) Trying installing 9.10 again by double-clicking on the install icon
5) See if your hdds will show up

---

### Post by Fodox on 2009-11-02
I have the same problem. 
After starting installation I tryed to set the switch "nodmraid", pressing the F6 key, but it doesn't work. 

Is this solution similar to your?

Fodox

---

### Post by Evil Rabbit on 2009-11-02
Hi Fodox!

I also had similar problems with the live CD.  Checking the nodmraid from the menu did not work for me either. You can follow the instructions provided by Ginsu543 or try the alternate install CD as I did. At some point the installer (text based, not a GUI installer) asks whether to enable RAID array or not. Even that way the dmraid will not be removed and you'll have to pass nodmraid to the kernel line in the GRUB.
I recommend you try it the Ginsu way first...

---

### Post by kfhughes on 2009-11-02
Tried both steps (nodmraid on boot from the Live CD) and using apt-get to remove dmraid; finally the install manager detected my hard drive. :D

---

### Post by Fodox on 2009-11-02
woah, it work! I followed steps of Ginso, without setting the nodmraid. 

Thank you all!
   Fodox

---

### Post by Ginsu543 on 2009-11-03
Excellent! I'm glad it worked for you. I just wish it had worked for me... :P

---

### Post by yn0t on 2009-11-03
I can't wait to try this when I get home!

I have a ASUS P4C800-E Deluxe with onboard Promise FastTrak 378.  It is disabled in the BIOS, however, the installer seems to still detect it somehow.  Plus, on top of that my SATA drives are not even plugged into the RAID ports on the motherboard.

I've tried the nodmraid option on bootup but then the installer does not detect any drives at all.

I'll post my findings tonight!

---

### Post by yn0t on 2009-11-03
Hey how about that.  Someone that said they'd post after trying it and actually does it!

Here's how I was able to get it to work.  Again, I'm using an ASUS P4C800-E Deluxe with a Promise FastTrak 378 RAID controller.  Though, I'm not booting off of the RAID (and it is disabled in the BIOS), Ubuntu was still trying to use it.

Booted from CD
Choose the F6 + nodmraid option
Choose "Install Ubuntu" option (not the Live enivronment)
Before getting to the partition I switched to a tty session using CTRL+ALT+F1 and ran "sudo apt-get remove dmraid"
After this I was able to see the drives.

Note:  Simply running "sudo apt-get remove dmraid" did not work for me.  I was able to see the drives but for some reason when it came to install to them the installer could not write.  In order for it to work I had to do the nodmraid option as well as the apt-get remove.

---

### Post by ewomack on 2009-11-04
Just for completeness, removing nodmraid also worked for Mythbuntu 9.10 64bit on a Shuttle KPC and a SATA HD.

Thanks for the tip - I was chasing this all day.

---

### Post by joama on 2010-08-23
Thanks to Ginsu543. We followed your instructions but did it for Ubuntu 10.04 and it worked :D. By the way the computer is an acer Aspire m3400 desktop. We have been trying to get stock cheep computers to work with Ubuntu so we can convince people to switch from Windows :)

Thanks again

---

### Post by jrobiii on 2011-11-19
Still saving butts in 11.10 ;-)

Thanks Ginsu543!

---

### Post by oldos2er on 2011-11-19
Closed, necromancy.

---


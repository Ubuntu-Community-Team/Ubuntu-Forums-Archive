---
title: "Installing ubuntu on vista"
date: 2008-05-20
forum: Hardware
---

### Post by santhosh443 on 2008-05-20
I have formatted whole hard disk of my laptop to install both windows and linux.

1)My hard disk is 160 GB
2)First i have made a 50 GB primary partition and installed window vista and left the remaining as empty space

3)Now how can i install linux and make it dual boot

4)I have tried installing ubuntu but it is not detecting the existing window vista...

Please help me

---

### Post by bobblehat on 2008-05-20
What happened when you did the Ubuntu installation? Did it complete but then not give you the option to boot Vista? Or did the installation fail?

---

### Post by santhosh443 on 2008-05-20
It installed correctly only but no option to boot from linux

---

### Post by bobblehat on 2008-05-20
When you first boot the machine does it give you any option to press a key and get into the Grub menu. If so, could you describe what you get? With your setup it should be something like:

Ubuntu (version) kernel etc
Ubuntu (version) kernel etc (recovery mode)
Ubuntu...
Other operating systems:
Windows Vista/Longhorn (loader)

...but I'm guessing it doesn't?

---

### Post by santhosh443 on 2008-05-20
Ya it doesn't give any options it directly goes in to vista

---

### Post by bobblehat on 2008-05-20
OK - I'm maybe going into too much detail with the following but just to help me with the diagnosis, assuming you're working off the CD installer it should go something like:

Boot from CD
Select 'Install Ubuntu'
Go through all the location stuff 
In the partitioning options select 'Guided - use largest continuous free space'
Complete the rest of the options
Install completes and the CD pops out

Does any of that sound different from your experience? I'm not trying to be pedantic - just trying to figure out what's different from normal on your install.

Edit: it might help to post what version you're using too - i.e. verion of Ubuntu and whether you're using the alternate installer or whatever.

---

### Post by santhosh443 on 2008-05-20
every thing is same except iam giving the partitions manually

swap space of 4 GB
root is 20GB

Iam using ubuntu 8.04

---

### Post by bford16 on 2008-05-20
Did you choose not to install GRUB?

---

### Post by bobblehat on 2008-05-20
If Grub's not installed, or you just want to check what's there, the instructions here might help -> [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Included in the instructions is a section on how to boot from the install CD, check what partitions you have and complete the Grub installs. I hope that's some help. At minimum it should let you see if you have the partitions you expect.

---

### Post by santhosh443 on 2008-05-22
Thanks for for your suggestion guys........At last i got it working......

---


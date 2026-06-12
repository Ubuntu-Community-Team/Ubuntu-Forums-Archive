---
title: "Ejected DVD drive auto closes as soon as it has ejected."
date: 2010-05-25
forum: Hardware
---

### Post by gencon on 2010-05-25
Using: Ubuntu Lucid

My desktop PC has 2 DVD drives, both Samsung, one is a read/writer, DVD-RW, the  other is read only, DVD-ROM. In /dev/ they are 'dvdrw' and 'dvd'.

Every time I eject the DVD-ROM device the system ejects it but then as  soon as it is fully out automatically closes the drive again, there is  no time to remove or insert a disk without risking damage, only a 1  second delay before the auto-closing. This happens however I try to  eject it: with the drive's open/close button, right-clicking on the  drive volume name on the desktop or in Nautilus and clicking 'eject', or  using 'eject /dev/dvd' in a terminal (-T results in the same thing, and  being su does not help either). Strangely all these methods work fine  with the other drive, 'dvdrw', it ejects normally.

I actually had to boot into Windows today to change the disk and then  boot back into Ubuntu !!

Any ideas how to fix it? The drives appear to work fine apart from this  problem.

Many thanks.

PS. When I tried using 'eject' in a terminal with /dev/cdrw and  /dev/cdrom both commands resulted in the /dev/dvdrw device ejecting,  even though I expected /dev/cdrom to apply to the read-only drive.

---

### Post by Nattereri on 2010-09-23
I still have the same problem with Ubuntu 10.04 server 64 bit and 32 bit desktop. The desktop machine has a sony CRX220E1 cd writer and the server has a LG dvd writer, I'm not sure of the model. I found a bug report on it but no solution as of yet. The bug report I found was under Ubuntu, bugs, Bug #525654.

---

### Post by gencon on 2010-09-24
There are several bug reports concerning this, it seems several things can cause it.

I fixed mine with this solution:

Run this command from the terminal:

sudo sysctl -w dev.cdrom.autoclose=0

If it works for you add it to a config file so you do not need to enter the above command after every reboot.

Edit this file as SU (the file probably will not already exist):

/etc/sysctl.d/60-cdrom-autoclose.conf

Add this line:

dev.cdrom.autoclose = 0

Worked for me.

HTH.

---

### Post by ChrisOfBristol on 2011-09-15
Works for me too, on Ubuntu 11.04.

---

### Post by gencon on 2011-09-15
Glad to hear the solution worked for you, but sorry to hear that this bug is still not resolved in Natty.

---

### Post by reedstrm on 2011-12-18
> **gencon said:**
> Glad to hear the solution worked for you, but sorry to hear that this bug is still not resolved in Natty.

Yay! this worked for me, too! (also sad it's not fixed)

---

### Post by versat3x on 2012-02-25
> **gencon said:**
> There are several bug reports concerning this, it seems several things can cause it.

I fixed mine with this solution:

Run this command from the terminal:

sudo sysctl -w dev.cdrom.autoclose=0

If it works for you add it to a config file so you do not need to enter the above command after every reboot.

Edit this file as SU (the file probably will not already exist):

/etc/sysctl.d/60-cdrom-autoclose.conf

Add this line:

dev.cdrom.autoclose = 0

Worked for me.

HTH.


hi i am new to linux and this soloution worked grate for me but how do you create and edit a config file excuse me if its a silly question consider me a caveman you are trying to teach how to shave

---

### Post by winh8r on 2012-02-25
First of all open a terminal either by pressing control + alt + T,

or using the menu

Then copy and paste this code into the terminal:

```
sudo gedit /etc/sysctl.d/60-cdrom-autoclose.conf
```

this will open a file

then copy and paste this code into the file:

```
dev.cdrom.autoclose = 0
```

click on save and exit

Job done!

---

### Post by gencon on 2012-02-25
versat3x,

winh8r has written how to do it...

In Linux config files are just plain text files, gedit is just a text editor. You could use 'nano' instead of 'gedit' which would bring up the nano text editor inside the terminal. sudo is a program that allows users to run programs as 'root' - in Linux config files are owned by root for security reasons.

You might want to spend a few hours reading through a Ubuntu manual. The link below is a good one, although the manual is for Ubuntu 10.10 (Maverick Meerkat) that's not something to be worried about it won't matter if you're using Lucid, Natty, or Oneiric.

You can download the manual in PDF from here: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

HTH.

---

### Post by versat3x on 2012-02-25
thank you winhr8 and gencon for your help i think i will have to read the manual but then i am a man never read the instructions first :-) it seems to have fixed the problem all though the eject button on my apple key board will open the tray but now does not close it

---


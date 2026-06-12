---
title: "Can cd be used to repair?"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by jerlinux on 2009-11-05
Online upgrade from 9.04 to 9.1 went VERY BADLY.  Now I can't even boot.  If I download and create the 9.10 cd, can it be used to repair the present setup or do I loose everything?

Thanks

---

### Post by ratcheer on 2009-11-05
Yes, you can. I just went through all that when I lost my ability to boot.

You will need to know what partition your root is stored on. Once you have booted the LiveCD, open a terminal.

Use "sudo fdisk -l" to see your disk partitions.

Use "sudo mount /dev/sdXX /mnt" to mount your root partition, e.g., /dev/sda5

Then, "sudo mount --bind /dev/ /mnt/dev"

Then, "sudo chroot /mnt" to get to a prompt where you can make your needed fixes.

Ctrl-d to exit when you are done.

"sudo umount /mnt/dev"

"sudo umount /mnt"

Finally, reboot your system and remove the LiveCD before grub starts.

Good luck,
Tim

---

### Post by jerlinux on 2009-11-05
Thanks for the reply.  But I worded the question wrong.
Although I have used Ubuntu for over a year, I have been too lazy to real figure out what I was doing.  It is a testimony to the user friendliness of Ubuntu that I was able to get the wireless network and printer set up.  And wine almost ran itself for the simple projects that I gave it.

So, what I meant to say was more like "If I put the cd in the drive and boot the machine, will it come back with a question like I found some 9.10 already here.  Would you like to try to repair this package?"

Your suggested procedure leaves me lost at the bakery when you say "make your needed fixes".  I have no idea what I would fix unless the software sees something and makes suggestions.

I have downloaded and burnt the cd, I think that this weekend I will just start over and hope that I can remember how I got the box set up as nicely as it was before I checked ok on the box that said install all updates.

Thanks again

---

### Post by stinger30au on 2009-11-05
aparently you can do a cd repair type thing with the alternative cd

i cant confirm this %100 as i have not done it myself but have read of others who have

---

### Post by bytecode on 2009-11-06
> **jerlinux said:**
> Thanks for the reply.  But I worded the question wrong.
Although I have used Ubuntu for over a year, I have been too lazy to real figure out what I was doing.  It is a testimony to the user friendliness of Ubuntu that I was able to get the wireless network and printer set up.  And wine almost ran itself for the simple projects that I gave it.

So, what I meant to say was more like "If I put the cd in the drive and boot the machine, will it come back with a question like I found some 9.10 already here.  Would you like to try to repair this package?"

Your suggested procedure leaves me lost at the bakery when you say "make your needed fixes".  I have no idea what I would fix unless the software sees something and makes suggestions.

I have downloaded and burnt the cd, I think that this weekend I will just start over and hope that I can remember how I got the box set up as nicely as it was before I checked ok on the box that said install all updates.

Thanks again


Hi jerlinux,

I understand what you're saying about needing to know "how/what/where" to fix.

ratcheer's suggestion was to mount (in other words access) the disk(s) and partition(s) of your broken system by mounting them into the live environment of the CD.

I guess the problem that you have is knowing what it is that you need or want to fix.

Which, of course, comes down to what the nature of the problem is.
You say:
> Online upgrade from 9.04 to 9.1 went VERY BADLY. Now I can't even boot. 

There could be a number of issues to resolve here, some quick and simple, others not so.

Even when I was a Windows user, I came from the "learn to fix it" rather than just "re-install" school of users.
Hence I've learnt many good things.  But it's all a question of time.

I take a similar approach now that I'm a Gnu/Linux user.  

What I would suggest, if you're willing to take a few minutes - maybe half an hour - is to have ago at using the live CD to boot up, and then try a couple of things to see whether you can indeed repair what you have.

If not, then yes - you can just re-install.


**Re-installation if you had a separate home partition**

The great thing about re-installation is that if you defined a separate /home  partition last time that you installed your system, then when you reinstall, you can choose **NOT** to format  that partition.  You can again choose it as your home partition from the "manual partitioning" part of the installer.

Then, when setting up your user account, ensure you have the same username as before..

The beauty of this, is that when you finally boot into your fresh, reinstalled system, all of your personal settings, data etc... should still be present.

You'd still need to reinstall any "custom" applications that you had, but they /should/ typically pick up any personal prefs. that you already had.


**Trying to fix what you have with a live CD**

Trying to fix it depends upon what the problem is, the ones that come to mind are:

In order of boot: 

[LIST=1]
[*]missing GRUB boot loader[LIST=1]
[*]mis-configured GRUB boot loader menu
[*]damaged filesystem
[*]broken / missing packages
[/LIST]

These can all typically be fixed with the live cd.

In order of ease of remedy:
[LIST=1]
[*]repair filesystem using the "fsck" file system check command
[*]re-install grub boot loader
[*]re-configure GRUB bootloader
[*]Re-install packages
[/LIST]

Sadly, there isn't an "AUTO REPAIR" facility with the live cd - 

(Isn't it about time that there was though guys?  Is it time to slow down the pace of change and maybe look at stability, features and a "repair-my-distro" live tool?)

But fixing the above problems is fairly straight forward, once you know which problem(s) you have and therefore, can find the "how-to" to fix it.

Can you give us a description of "how far" your computer gets before it all goes wrong?

What is the last intelligible text that you get on screen for instance?  

Do you get the grub menu? 

Do you get a "(Busybox)" shell? 

Does it just keep rebooting?

---

### Post by jerlinux on 2009-11-06
Thanks for the offer to help me learn a little about Ubuntu.

When I boot, the machine seems to want to start normally but this error appears before I see the desktop:

Error 16:  Inconsistent file system structure
Press any key to continue

After I press a key the screen gives me these choices:

Ubuntu 9.10, kernel 2.6.31-14 General
Ubuntu 9.10, kernel 2.6.31-14 General recovery mode
Ubuntu 9.10, kernel 2.6.27-11 General
Ubuntu 9.10, kernel 2.6.27-11 General recovery mode
Ubuntu 9.10, kernel 2.6.22-14 General
Ubuntu 9.10, kernel 2.6.22-14 General recovery mode
Ubuntu 9.10, kernel 2.6.20-16 General
Ubuntu 9.10, kernel 2.6.20-16 General recovery mode
Ubuntu 9.10, memtest86+

If I pick either of the top two, I come right back to the error 16.

If I pick any of the recovery choices, I get a few pages of script than the scroll stops.  If it is important, I can record the last line of the script but getting the rest of it would not be easy.  

If I pick the general choices, the color bar moves back and forth in the center of the screen under the little Ubuntu symbol but it never finishes - does not show the box to enter name and password.  Often a note appears at the bottom of the screen with the moving color bar adviseing I hit escape to go into a recovery shell.  But then the root password does not work and even the suggestion that I hit control -D to continue is ignored.  I have tried holding down the control key and pressing d.  I have tried holding down the control key and pressing D.  I have repeated both commands while including the minus sign.  I have even typed the word control into the machine.  Nothing ever happens at this point.

So that is where I am now.  Before I hit the update Ubuntu button, this thing ran well.  I was about to tell M$ that their help was no longer needed.  But if I have to reinstall this system, it might be a while before I get everything running as before.

But that seems to be my only choice right now.

---


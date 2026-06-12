---
title: "Hibernate does not work after update from dapper to edgy"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by barfoos on 2006-10-28
Hello

My laptop (Acer Extensa 2900) does not resume correctly after hibernation.
In fact it seems as if it does not even try to resume. It just boots up.
The only thing it complains about is that it is "Unable to find swap-space signature".

Resuming worked with dapper. Suspend to ram still works. I'm not quit sure,
which information to give. I have universe and multiverse in my sources list.
I have the packae "hibernate" installed. I do not realy know, if this package is needed at all. I used it to test whether suspend to ram works.
But it seems like pressing the sleep button of my notebook, or choosing hibernate from the gnome quit menu, does not call the things from the hibernate package, but some standard ubuntu things (possibly something from /etc/acpi).

Please give me a hint if any further information is needed to solve my problem.

I would be very glad if someone could help me, but I'll keep on searching for a solution my self, and if I find one, I'll post the problem.

btw: is there any website were the ubuntu way of hibernation is explained?
I would guess, that for example somewhere in the init.d directory there must be a check or something, whether a normal boot up or a resume is going on, but I can't find it.


thank you for any help

greetings
  barfoos

---

### Post by Stravos on 2006-10-29
I'm having a similar problem.  Suspend to RAM works for me in Edgy, but hibernate doesn't seem to at all.  I started getting that error about swap-space signature at boot time after I upgraded to edgy.  I don't think it's related to this problem at all, but I could be wrong :p

Anyway, when I manually try to put the laptop to sleep (Inspiron 8600) it goes to the screensaver, which runs for half a second then it freezes (did this in dapper too) then it dumps me at a console screen with the swap-space error, then screen goes blank.  The screen then turns back on and I'm prompted with a locked desktop.  It seems that there must be something preventing it from completing the hibernation powerdown, but I don't really know where to start.

I don't know if these problems are related.  Are hibernation problems known in Edgy or are these just isolated cases?

---

### Post by barfoos on 2006-10-29
adding a resume=/dev/hda5 option to the list of kernelparameters in grubs
menu.lst finally solved my problem.

I also changed the UUID stuff in /etc/fstab back to the normal device name of my swap partition and run mkswap on it.

---

### Post by barfoos on 2006-10-29
Hello again.

The changes I made still work, but one odd thing occurs.

When restarting after hibernating grub always defaults to boot up into
recovery mode. This is no big problem, but it's anoying.


What am I doing wrong?


greetings barfoos

PS: My search for some well founded documentation on the ubuntu process of supspending and hibernation still remains, and every little piece of information is appreciated.

---

### Post by Stravos on 2006-10-29
I made the changes you did and now it seems to hibernate ok, but like yours did before, when I boot up it's like a fresh boot.  I'm a little confused about this UUID= in /etc/fstab, are these for upstart?

Anyway, not much to offer here, but this post needs a bump anyway ;)

---

### Post by rrwo on 2006-10-30
Hibernate and Suspend no longer work after my upgrade.  When I do either, the screen blanks to a text console and then I'm returned to my X session (already logged in).  So it seems to have no effect.

---

### Post by zgornel on 2006-10-30
Ok. I solved my hibernate/suspend problems. Steps I took (all are necessary, tested every combination):
1. reverted to old /etc/fstab and added resume=/dev/sda4 <-- linux swap to kernel boot parameters
2. added in /etc/X11/xorg.conf, Section Device : *Option "VBERestore" "true"*
After this, Resume Worked, Hibernate would not function, brought me back to the password stage.
3. Installed *Hibernate* script from the repositories
Hibernate works too. 
(Tested on Toshiba Sattelite Pro L20)

ADDED: this might be another more elegant fix, gonna check it out:
[http://article.gmane.org/gmane.user-groups.linux.delhi/13814](http://article.gmane.org/gmane.user-groups.linux.delhi/13814)
RESULT: No change for me, sticking with older (see above method)

---

### Post by EDevil on 2006-10-30
That article from gmame.org worked for me... Edgy it seems is reaaaaly... edgy.

---

### Post by rrwo on 2006-10-31
I think that you don't need to change back your fstab. 

You can use resume=UUID=... (same UUID as in fstab) instead of resume=/dev/etc.

---

### Post by rrwo on 2006-10-31
I've tried installing the hibernate script from the repositories, and even tweaked some of the settings in /etc/hibernate, but still cannot get it working.

Suspend seems to do something like suspending, but when I press the power button, the system powers up but nothing happens (screen is still blank, no noise, response).

When I hibernate, it seems to hibernate and restore itself at once.

I've checked /var/log/hibernate.log and found nothing that might give me a clue here.

---

### Post by zgornel on 2006-10-31
> **rrwo said:**
> I've tried installing the hibernate script from the repositories, and even tweaked some of the settings in /etc/hibernate, but still cannot get it working.

Suspend seems to do something like suspending, but when I press the power button, the system powers up but nothing happens (screen is still blank, no noise, response).

When I hibernate, it seems to hibernate and restore itself at once.

I've checked /var/log/hibernate.log and found nothing that might give me a clue here. Suspend behaved like that for me too, have you modified xorg.conf ?

---

### Post by rrwo on 2006-10-31
No changes to xorg.conf, but I think that I've fixed it.  I was getting errors about it being unable to find the swap partition, and I realised that I mistyped the name of the swap device in the /etc/hibernate/suspend2.conf file.

So hibernate works.  Suspend does not, however.  It it shuts down, but does not completely start up (the fan turns on, but nothing happens... I guess it powers up but does not properly save anything to RAM to be able to restore itself.)

---

### Post by RafRaf on 2006-11-03
For me the hibernate scripts (sudo apt-get install hibernate) really seams to suspend quite well. However, when resume the network connections (ath0) is disabled. Anyone had the same problem?

---

### Post by RafRaf on 2006-11-03
Hi again. I have now done a clean install of edgy and so far it seams to be working fine..and suspend works! :D

---

### Post by er-ku on 2006-11-05
There are two things to do to make hibernation work, actually:
[LIST=1]
[*]add a "resume=YOURDISKPARTITION " kernel option to the #defoptions line in /boot/grub/menu.lst, to make it look like this:
```
# defoptions=resume=/dev/hda3 quiet splash
```
Which exactly form to describe YOURDISKPARTITION you use here, makes no difference. It could be /dev/devicename or LABEL=text or UUID=uuid. Resuming works in all cases. 
[*]run update-grub:
```
sudo update-grub
```
This script updates the rest of menu.lst, and actually makes hibernation work.
[/LIST]

---

### Post by briguy on 2006-12-09
Worked for me!  Thanks

---

### Post by le_vainqueur on 2006-12-19
> **er-ku said:**
> There are two things to do to make hibernation work, actually:
[LIST=1]
[*]add a "resume=YOURDISKPARTITION " kernel option to the #defoptions line in /boot/grub/menu.lst, to make it look like this:
```
# defoptions=resume=/dev/hda3 quiet splash
```
Which exactly form to describe YOURDISKPARTITION you use here, makes no difference. It could be /dev/devicename or LABEL=text or UUID=uuid. Resuming works in all cases. 


I do not have permissions to this file.  I tried to edit the permissions, but is said I do not own the file.  I tried to log in as the root user by typing "sudo su" into the terminal, but had no luck.  How do I edit this file?

---

### Post by nmincone on 2006-12-19
> When restarting after hibernating grub always defaults to boot up into
recovery mode. This is no big problem, but it's anoying.
Do the following to resolve the default boot string.
#sudo gedit /boot/grub/menu.lst

look for this;
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

Make the 'default' the number of the item list you want to load by default- it's numbered 0-x (x being the number of items in your list). A boot list looks like this (below) and this one has 3 entries, so changing the option mentioned above to 2 would default to the memory test boot.

## ## End Default Options ##
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by nmincone on 2006-12-19
> **le_vainqueur said:**
> I do not have permissions to this file.  I tried to edit the permissions, but is said I do not own the file.  I tried to log in as the root user by typing "sudo su" into the terminal, but had no luck.  How do I edit this file?
#sudo gedit /boot/grub/menu.lst

---

### Post by nmincone on 2006-12-19
> **le_vainqueur said:**
> I do not have permissions to this file.  I tried to edit the permissions, but is said I do not own the file.  I tried to log in as the root user by typing "sudo su" into the terminal, but had no luck.  How do I edit this file?
#sudo gedit /boot/grub/menu.lst

---

### Post by Dubbayoo on 2006-12-26
> **er-ku said:**
> There are two things to do to make hibernation work, actually:
[LIST=1]
[*]add a "resume=YOURDISKPARTITION " kernel option to the #defoptions line in /boot/grub/menu.lst, to make it look like this:
```
# defoptions=resume=/dev/hda3 quiet splash
```
Which exactly form to describe YOURDISKPARTITION you use here, makes no difference. It could be /dev/devicename or LABEL=text or UUID=uuid. Resuming works in all cases. 
[*]run update-grub:
```
sudo update-grub
```
This script updates the rest of menu.lst, and actually makes hibernation work.
[/LIST]

Is **"resume=YOURDISKPARTITION "** supposed to point to / or swap? I have:

- 1.5GB RAM
- root on /dev/sda1
- a 750MB swap partition on /dev/sda5
- a 1GB swap file on /data/swap_file

---

### Post by squido on 2007-01-04
> **barfoos said:**
> adding a resume=/dev/hda5 option to the list of kernelparameters in grubs
menu.lst finally solved my problem.

I also changed the UUID stuff in /etc/fstab back to the normal device name of my swap partition and run mkswap on it.

Just to add a "me too" for those searching:

I have a Thinkpad T-43. After the update to edgy suspend stopped working. Following the above steps corrected the issue. Thanks barfoos.

---

### Post by jonathanhowell on 2007-01-04
@Dubbayoo:

Point **resume=** to your swap partition (/dev/sda5 I beleive).

I had to restart my computer before hibernate would work. Since I had upgraded from Dapper, a hibernate file was there previously & the computer hung while "returning from hibernation". A power-cycle fixed that & all works OK now.

- Jonathan

---

### Post by prince_niceguy on 2007-01-22
hibernate is working for me with resume=swap drive... but suspend is not working with me... :-(

can some one please help...

---

### Post by scifan2 on 2007-01-23
I found the following works well for making Hibernation work on Edgy on my Acer 5672

(Note: my swap drive is /dev/sda4 - or UUID=fb2f566f-ac48-468d-bff2-03f0778b72bd)

(I have verified with blkid that /dev/sda4 does infact have a UUID of fb2f566f-ac48-468d-bff2-03f0778b72bd)

Slightly modified from here: [http://article.gmane.org/gmane.user-groups.linux.delhi/13814](http://article.gmane.org/gmane.user-groups.linux.delhi/13814)

1. edit the resume file located at /etc/initramfs-tools/conf.d/
2. change the RESUME=UUID line to RESUME=/dev/sda4, save+exit
3. Then issue the command -- sudo update-initramfs -c -k `uname -r`

then change the swap line in /etc/fstab from:

UUID=fb2f566f-ac48-468d-bff2-03f0778b72bd none            swap    sw   0  0 

to

/dev/sda4 none            swap    sw      0  0

And it works happily for me... I don't normally suspend to ram anyway... so this is GREAT... :)

Cheers

---

### Post by Cariboo1938 on 2007-11-02
> **zgornel said:**
> Ok. 
1. .........and added resume=/dev/sda4 <-- linux swap to kernel boot parameters
2. added in /etc/X11/xorg.conf, Section Device : *Option "VBERestore" "true"*
3. Installed *Hibernate* script from the repositories

Hi,
I have the "Hibernate not working issue " in Feisty and try to fix it your way.
Please, could you give more details on how to add "resume=/dev/sda4 <-- linux swap to kernel boot parameters"?
Thanks in advance!

---


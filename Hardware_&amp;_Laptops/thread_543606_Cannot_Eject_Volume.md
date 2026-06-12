---
title: "Cannot Eject Volume"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by hodad on 2007-09-05
My laptop removable CD Rom drive (6 year old Latitude C600 w Feisty) has all of the sudden started saying "Cannot Eject Volume", and I cannot get it to eject. It was working previously under Feisty.  Here are my particulars:

When I right click on CD Rom Drive - Properties, I get:
Owner- Unknown - Read Only
Group - Unknown - Read Only
Others - Read Only

Drive - samsung CD-ROM SN-124

When I left click on the icon for the drive, I get "Unable to mount Media"

I've tried researching other posts on this, but I can't seem to get anywhere.  HAs anybody got any ideas?

Thanks!

---

### Post by Solvax on 2007-09-05
I don't know but maybe you removed it unsafely?
try to insert it in windows and remove it safely.
Then try again...

Just guessing, I hope it helps.
(I have to do that with my external HD's,
otherwhise i cannot mount them in Linux)

Greetings Solvax

---

### Post by al2cane on 2007-09-14
I was having this problem too, even reformatted my external to it's original FAT32 hoping to resolve, before seeing a workaround over at [Marengo.com](http://www.marengo-ltd.com/blog/?p=41)

In a terminal type: 
```
sudo mv
/usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi ~
```

Works for me :-)

---

### Post by raijinsetsu on 2007-09-14
Open a terminal. Type "mount" and see what cdrom is mounted. Then type "sudo umount /media/cdromX" where cdromX is the cdrom listed by mount. This should unmount your volume. If it does not, try rebooting, and removing the CD from the drive before grubs starts.

Oh... If the unmount command says the drive is busy, there's probably an application that is accessing something on the CD (this application could even be hung). If that's the case, it's easiest for the less linux saavy to just reboot.

---

### Post by hodad on 2007-09-16
Thanks for the responses; still not working, here's what i got:

I typed "mount",  saw my hard drive"dev/hda1..." and ten more lines of stuff that I assume are other items that are considered "mounted" (?).  But no where do I see a CDROMx... listed.

I also typed in the command line from the Marengo site.  It apparently worked (no error message), but nothing changed.

???

At this point I'd try to reinstall Feisty, but, of course, I can't access my CDROM (classic Catch 22).

---

### Post by hodad on 2007-09-25
Thanks for your reply.  

As I mentioned previously, I see no CDROM drive listed after typing mount.   There are no apps running that I am aware of.  I have tried rebooting about 20 times, and have booted up in "safe" mode at least twice.  I've removed the removable drive and booted up in "recover" mode, then rebooted after re-plugging in the cdrom.  Cannot get cdrom to physically eject, I just keep getting "Cannot eject volume" error message.

I do see the following lines after typing mount:

/dev/hda1 on /type ext3 (rw, errors=remount -ro)
proc on /proc...
/sys on /sys...
varrun on var/run...
varlock on var/lock...
procbususb on /proc...
udev...
devshm...
devpts...
lrm...
binfmt_misc on...
(I'm copying this manually, so am leaving out some verbiage)


I then typed "sudo mount /mnt/cdrom" and got:
Mount: cannot find /mnt/cdrom in /etc/fstab or /etc/mtab

Any suggestions?

---

### Post by hodad on 2007-09-25
...update...

I tried mount /media/cdrom0 and got:

mount: block devie /dev/hdc is write protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc

I then tried the suggestion dmesg | tail and got:

"... hdc: drive not ready for command" followed by many other lines of error messages.

I suspect that the forst error message is the most significant, and think that perhaps the drive itself has a hardware problem.  Does anyone have any alternate ideas?

THanks!

---

### Post by taco man2 on 2008-05-03
Rebooting worked out for me fine. If it doesn't work with a simple reboot then you should unmount the cd drive before the grub in the boot menu and reboot again with the drive mounted in.

---


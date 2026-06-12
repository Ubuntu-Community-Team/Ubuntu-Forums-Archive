---
title: "Grub"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by Spunkbubble on 2009-04-06
Hi, I've finally managed to resolve my problem of not being able to partition the hard drive by just not doing it at all. Instead, I've taken the hard drive from a second computer and installed it in this one just for Ubuntu. I also managed to finally get my keyboard working by manually selecting it (only the US version was avilable in GUI). I also managed to figure out how to get permission to edit some files which were required... clever me 8-[

However, I have a big problem. I need to make a GRUB boot disk so that I can switch between hard drives, but I can't make it without using linux. However, when i attempt to mount the floppy in linux I get an error message saying something along the lines of "sudoers is mode 0644, should be 0440", and the terminal refuses to run any sudo commands. I can't edit the file because I don't have root privelages, and I can't find a way to get root privelages in the temporary version (using nautilus hasn't worked).

But now when I try to install, nothing happens. I can click the icon on the desktop, or select it from the admin menu, but nothing happens.

I also have an earlier version of Ubuntu installed on the second hard drive, but I can't access it without using GRUB, which I can't install without linux, which I can't install because I have this problem. I might be able to install it through the desktop on the second hard drive, but again I can't do that.

So the most helpful thing to me i feel right now would be if someone could tell me how I can make a GRUB floppy in Windows, since I am sick of trying to run commands I don't understand and which don't always work in the terminal. Once I have the floppy I can boot into the existing Ubuntu and jsut update from there.

---

### Post by SuperSonic4 on 2009-04-06
Can you get to the grub menu on the hard drive from the second computer? If you can try recovery mode which will should give you a root terminal. You can then use nano to edit grub but if you have non-important data a reinstall might work out easier

---

### Post by Spunkbubble on 2009-04-06
I'm not sure how I can access the non-primary hard disk without using GRUB to manually select it. Can you tell me how?

Oh, and a Maiden fan are we? Snap :guitar:

---

### Post by SuperSonic4 on 2009-04-06
Damn right - UP THE IRONS!

Er, I think you can choose in the BIOS which to boot from initially

---

### Post by Spunkbubble on 2009-04-06
Ok, I'll have a look at it now...

I was at the Twickenham gig last year :D

---

### Post by ronparent on 2009-04-06
Things in order. First you have to boot ubuntu from the live cd and in a terminal window run sudo fdisk -l and post he results here.

This simply will tell us what your current boot order is and what to do next.

Meanwhile, congrats on getting an ubuntu system installed. Using a spare disk is what I did on my own system to play it safe. Your install probably will not see your windows drive, again because you won't yet have raid software installed which will permit this. We can address that when grub is working to boot either ubuntu or windows.

---

### Post by Spunkbubble on 2009-04-06
sudo fdisk -l:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b0cee50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976765948    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc68581cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9588    77015578+  83  Linux
/dev/sdc2            9589        9964     3020220    5  Extended
/dev/sdc5            9589        9964     3020188+  82  Linux swap / Solaris
```

---

### Post by ronparent on 2009-04-06
Right,no change inboot order - this should be a oiece of cake!

From the live cd open aterminal. 

do: sudo grub

grub> find /boot/grub/stage2

This should find your ubuntu install if all in order. Use the output from the above command, probably (hd2,0) as follows:

grub> root (hd2,0) (or whatever)
grub> setup (hd0)

Note that this will rewrite your mbr on sda to find grub and that you will no longer be able to boot to windows except thru the grub menu.

On second thought, if you prefer not to do this (overwrite the windows mbr) then you can change the boot order in your bios to boot on what is now sdc. The advantage of this is that you can always get to window by restoring the boot order in bios. Do the same as above except that your root command will now be (hd0,0).

---

### Post by Spunkbubble on 2009-04-06
Ok, well like a tit, I didn't wait for more info. I ran the installer and it correctly identified all hard drives correctly, as well as sizes and data usage. So I installed fully on the second HD. However, when I restarted, I got a GRUB error 21.

This consistently happens on startup. If I try to change the boot order in BIOS, I'm told "READ ONLY". So I tried physically unplugging the second hard drive (with Ubuntu on it) to force a load from Windows. But doing this just returned GRUB error 21 again... so much for thinking that GRUB would only be installed on one HD. When I disconnect the Windows HD, I get error 2 instead.

Ideas?

---

### Post by ronparent on 2009-04-06
You have already overwritten the mbr for loading windows and the grub bootloader is finding nothing. No problem. Wth the ubuntu drive plugged in, run the script in terminal that I gave you in the prior post. Note that your second drive is actually sdb, the second disk in your raid array. Ubuntu is actually installed on the third hard drive - sdc. We can worry about restoring a windows mbr on sda later if you still want it. We should be able to boot windows satisfactorily from the grub menu once we get it working.  As long as you have not written anything to either sda or sdb except for the mbr there should be no problem.

---

### Post by Spunkbubble on 2009-04-06
Just to clarify - I actually have 3 HDs. Two 500GBs and an 85GB. Windows recognises the first two as being one, and I only have linux on the second. I can start up with the live disc, so I'll try the commands now.

---

### Post by SuperSonic4 on 2009-04-06
> **Spunkbubble said:**
> Ok, I'll have a look at it now...

I was at the Twickenham gig last year :D

Yeah same, and I already know I won't see a better gig for a long time. Aces High was better than sex and chocolate put together!

> **Spunkbubble said:**
> Just to clarify - I actually have 3 HDs. Two 500GBs and an 85GB. Windows recognises the first two as being one, and I only have linux on the second. I can start up with the live disc, so I'll try the commands now.

So Windows sees sda and sdb as the same disk? With ubuntu on the third? I'll wait and see what ronparent's post brings up xD

---

### Post by Spunkbubble on 2009-04-06
Ok, this is my exact terminal output executing the commands you included in the other post.
```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage2
find /boot/grub/stage2
 (hd2,0)
grub> root hd2,0
root hd2,0

Error 11: Unrecognized device string
grub> root (hd2,0)
root (hd2,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd2,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub>
```
Attempting to reboot gives the same problem... GRUB error 21. :(

---

### Post by Spunkbubble on 2009-04-06
Ok I finally found a temporary solution for this... I booted using the live disc, burned a Super Grub disc, and then booted from that and repaired the Linux/Windows boot sequences.

The only problem now is how I can configure GRUB to give me a choice of which OS I want to use; at the moment, I have no option of selecting Vista, it just loads straight into Ubuntu.

---

### Post by upchucky on 2009-04-06
search here for windows chainloader  it is info to add to the /boot/grub/menu.lst file that is needed to boot windows.

---

### Post by Spunkbubble on 2009-04-06
Ok, thanks for the info :)

---

### Post by Spunkbubble on 2009-04-06
Yet another problem! After a couple of sucessful sessions, I logged in as root to change some file permissions for installing programs, but when I logged out the login screen didn't show up, instead giving me an "Error 15" GRUB message.

Now whenever I attempt to log in to Ubuntu either normally or by using the GRUB CD I get the same message saying "No root string was found on selected fstab file", and "Error 15: File not found".

Please tell me there's something simple to fix this, I just spent the last hour tweaking my settings in minute detail after a whole day of installation attempts.

---

### Post by finalghost911 on 2009-04-06
i solved this problem by disconnecting my external hard drive from my usb hub so the files could move faster from the hard drive into the computer.

---

### Post by Spunkbubble on 2009-04-07
Thanks for the idea, but I'm not using any external HDs :(

---

### Post by Spunkbubble on 2009-04-07
UPDATE: Now if I try to start up using the GRUB CD, I get error 13, but if I try to boot normally into Ubuntu I get the following output:
```
kinit: No resume image, doing normal boot...
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
```

---

### Post by ronparent on 2009-04-07
Check this link for error 15: [http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

Your error is probably in the grub menu.lst!

---

### Post by Spunkbubble on 2009-04-07
I've just read over the page you suggested and I can't find anything to help me. I haven't modified my menu.lst file, I haven't done anything new with Windows, and my computer loads straight into Linux just fine, only it runs into these errors.

Any suggestions?

---

### Post by ronparent on 2009-04-07
Now that is a different situation. Please post those errors as best you can. Bump

---

### Post by Spunkbubble on 2009-04-07
> **Spunkbubble said:**
> UPDATE: Now if I try to start up using the GRUB CD, I get error 13, but if I try to boot normally into Ubuntu I get the following output:
```
kinit: No resume image, doing normal boot...
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
```
This is the problem.

---

### Post by upchucky on 2009-04-07
try advanced supergrub it has a few more bells and whistles to repair grub and set up dual boot. 

read everything carefully though, you will not damage anything, but can cause great confusion for yourself and others if you do something and do not understand why and what you did.

---

### Post by Spunkbubble on 2009-04-07
I'm booted on a live disc at the moment by the way.

EDIT: I can't find an advanced version of the Super GRUB disc, can you give me a link please? What advantage does it give me over my existing one?

---

### Post by upchucky on 2009-04-07
this is it, the "advanced" has been removed from the title.
If you look at the menu after you create the disk you will see the option to select advanced mode when using it. (Advanced mode has a few more bell and whistles.)

[http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)

---

### Post by Spunkbubble on 2009-04-07
Ok, what is it I need to do with the menu? Sorry to ask so many questions, but I want to jot down exactly what i need to do since booting from the live CD takes so long.

I've already tried to boot using recovery modes and a couple of ways like that.

---

### Post by upchucky on 2009-04-07
after you download and create the supergrub disk, boot it, then select the advanced options to fix the grub, to give more instructions here would mean i would have to type the instructions included with super grub, but you already have them, read carefully.

there are several options to try but look for the one that most closely matches your desired setup.

again it is important to understand the instructions so read, and google what you do not understand.

other than that I would need to be at the actual pc to be of better help.

good luck.

---

### Post by Spunkbubble on 2009-04-07
Ok well thanks for the help, I'll have a poke around with the GRUB disc and see what I can do.

---

### Post by Spunkbubble on 2009-04-08
I've had a look, tried all the options I can think of, and whichever way I do it, I still can't start up Ubuntu without getting error 13 or this:
```
kinit: No resume image, doing normal boot...
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
```

---

### Post by Spunkbubble on 2009-04-08
**The situation now is that:**

- Booting up normally into Ubuntu gives me a brief loading bar, then this:
```
kinit: No resume image, doing normal boot...
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
```

- Booting into Ubuntu via super GRUB disc gives an error 13

- Using the direct booting option on the super GRUB disc gives me error 15

---

### Post by Spunkbubble on 2009-04-08
Does anyone know a solution for this? Or at least where I've gone wrong so I can avoid the problem in future?

---

### Post by ronparent on 2009-04-08
Based on the boot errors you have posted, the first thing you need to know is whether or not the init file actually doesn't exist (if it does your ubuntu file system is probably intact)
.
Try from a live cd the commands:

grub
grub> find /sbin/init

If found, the output from that command will tell you that /sbin/init exist (and also that the file sysem probably is intact and where it resides). If so use that output as follows:

grub> root (hd?,?)
grub> setup (hdO)

This will set up your grub sot that you should again be able to boot into Linux (and Windows). If /sbin/init is not found, you may have to reinstall!!!?

---

### Post by Spunkbubble on 2009-04-09
I tried it out, and managed to sort the problem :)

Thanks very much.

---

### Post by ronparent on 2009-04-09
Glad to hear it. Good luck to you.

---


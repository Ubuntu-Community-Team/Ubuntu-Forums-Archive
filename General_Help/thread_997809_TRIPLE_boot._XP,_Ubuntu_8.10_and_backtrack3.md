---
title: "TRIPLE boot. XP, Ubuntu 8.10 and backtrack3"
date: 2008-11-30
forum: General Help
---

### Post by blurryone on 2008-11-30
Ok guys,

this has been giving me a massive headache and for the life of me i cannot work it out.

Here goes,

Initially i had XP, Ubuntu 8.04 and backtrack 3 - using grub and everything worked fine.

then i downloaded ubuntu 8.10 burned it to a disk, installed it. and now every time i try to boot into backtrack it restarts my computer.

Everything is the same in the menu.lst so i can't understand why it would do that.

anyone having the same problem or know what i could do to fix it?

fdisk -l prints this. (and always has done, not sure why)

Cannot open /dev/sda
Cannot open /dev/sdb


This is the last part of my menu.lst
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0bd4cef9-9c84-4e45-8d6f-f233496e4164
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0bd4cef9-9c84-4e45-8d6f-f233496e4164 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		0bd4cef9-9c84-4e45-8d6f-f233496e4164
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0bd4cef9-9c84-4e45-8d6f-f233496e4164 ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		0bd4cef9-9c84-4e45-8d6f-f233496e4164
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Backtrack (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz root=/dev/sda4 ro vga = 773
savedefault
boot

---

### Post by blurryone on 2008-11-30
Still no resolution to this one guys, I am going to try installing 8.04 and upgrading instead of doing new install.

Will post results.

Any help would be appreciated.

Thanks

---

### Post by blurryone on 2008-11-30
nope.

Upgrading to 8.10 kills it also.

Is there any way to do this upgrade without changing the GRUB settings? (the update must install something which changes the way grub looks at things, and thus kills backtrack)

Any help appreciated.

Thanks

---

### Post by markbuntu on 2008-11-30
Try chainloader with Backtrack. This should eliminate any grub issues and go right to the root without any grub stage involvement.

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title Backtrack (on /dev/sda4)
root (hd0,3)
chainloader  +1

---

### Post by blurryone on 2008-11-30
Thanks for the reply,

I tried that but still reboots.

Is there any reason why you do not have the kernal command in what you recommended?

Thanks

---

### Post by blurryone on 2008-11-30
I just tried without the kernel line too, and it does another problem altogether.

Is there perhaps a way to load the update and then install the previous version of grub off the 8.04 live CD?

Thanks

---

### Post by markbuntu on 2008-11-30
> **blurryone said:**
> Thanks for the reply,

I tried that but still reboots.

Is there any reason why you do not have the kernal command in what you recommended?

Thanks

You don't need it. chainloader just hands over the boot process entirely to that partition and gets out of the way. If you use the kernel command you need to know which kernel you are booting which can change and are dependent on grub to find the kernel which can be problematic in certain situations.

I have 4 operating systems on my machine, each with its own grub and I chainload 3 of them from the first hard drive. I never need to edit the menu.lst even when I reinstall one of them or replace it with something else though sometimes I change the title. 

Anyway, it looks like the boot sector of that partition got messed up somehow. Do you get any error messages?

---

### Post by blurryone on 2008-11-30
Nope, I just installed a clean 7.04 and it worked again (no change to backtrack partition)

No error message just a straight reboot. (if there is one it is happening way to fast for me to read it)

I didn't install a bootloader for backtrack as i was just using grub (got used to it using ubuntu) so would chainloader work in that case?

Thanks for the response.

---

### Post by falcon61102 on 2008-11-30
No, as markbuntu said, the chainloader is for handing off to another boot manager so if you didn't install one with Backtrack, chainloader is not going to work.  

With 8.10 using the UUID instead of the root(hdX,Y) have you attempted to use the UUID for your Backtrack partition in your boot string for Backtrack?

---

### Post by blurryone on 2008-11-30
excuse my ignorance, but how would i determine the UUID string from say (hd0,3)?

And to answer your question no i haven't tried that :confused:

Thanks!

---

### Post by falcon61102 on 2008-11-30
Boot into Ubuntu or run the Live CD version and then use the following code:
```
blkid
```

That will list the partitions and their UUIDs.  You're looking for the UUID for /dev/sda4.

---

### Post by detroit/zero on 2009-01-27
> **blurryone said:**
> Ok guys,

this has been giving me a massive headache and for the life of me i cannot work it out.

Here goes,

Initially i had XP, Ubuntu 8.04 and backtrack 3 - using grub and everything worked fine.

then i downloaded ubuntu 8.10 burned it to a disk, installed it. and now every time i try to boot into backtrack it restarts my computer.

Everything is the same in the menu.lst so i can't understand why it would do that.

anyone having the same problem or know what i could do to fix it?

fdisk -l prints this. (and always has done, not sure why)

Cannot open /dev/sda
Cannot open /dev/sdb


This is the last part of my menu.lst
## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        0bd4cef9-9c84-4e45-8d6f-f233496e4164
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=0bd4cef9-9c84-4e45-8d6f-f233496e4164 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

#title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid        0bd4cef9-9c84-4e45-8d6f-f233496e4164
#kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=0bd4cef9-9c84-4e45-8d6f-f233496e4164 ro  single
#initrd        /boot/initrd.img-2.6.27-7-generic

#title        Ubuntu 8.10, memtest86+
#uuid        0bd4cef9-9c84-4e45-8d6f-f233496e4164
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title        Backtrack (on /dev/sda4)
root        (hd0,3)
kernel        /boot/vmlinuz root=/dev/sda4 ro vga = 773
savedefault
boot
Hey,
I'm looking at installing BT3 in my drive, and in doing my pre-install research (which is how I found your thread) I just read [another post that might help you]("http://ubuntuforums.org/showthread.php?t=1021155&") with your problem.

Good luck!

---


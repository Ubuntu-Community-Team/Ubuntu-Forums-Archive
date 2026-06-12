---
title: "dual boot problem w98se heron fresh install"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by schober on 2009-04-28
i'm new to linux & i'm trying to build a dual boot w98se & ubuntu dual boot computer 
on a fresh hd ive installed 1)w98se and then 2) hardy heron
im having problems with grub
some times booting would "hang" at the blank  black screen stage after the boot menu & the ubuntu logo stage & just before login. It was neccesary to switch off at the mains and reboot and all appeared ok - it being possible to use heron and w98

now, at startup im not given the boot menu and it boots direcly into heron - no w98!!!!!

ive looked in [FONT=Arial][COLOR=Blue]/boot/grub/menu.lst[/COLOR][/FONT] and got  (rems deleted)

[I]default        0
timeout        10

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=592447e9-fa4c-410c-8ec7-21b6620c5fdd ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=592447e9-fa4c-410c-8ec7-21b6620c5fdd ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

title        Other operating systems:
root

title        Windows 95/98/Me
root        (hd0,0)
savedefault
makeactive
chainloader    +1
[/I]
any bright ideas whats wrong and where to startl looking????
should i give up and reinstaal w98 and a later ubuntu version?
im surprised at hitting this problem on an old version

---

### Post by Sef on 2009-04-28
Applications > Accessories > Terminal 

Copy and Paste (or type) this command:

```
sudo fdisk -l
``` Small L

Copy and Paste the results in this thread.

---

### Post by schober on 2009-04-28
thanks for reply sef; got this

[I]Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00009251

   Device         Boot           Start              End         Blocks               Id  System
/dev/sda1          *                   1                 644       5172898+        c  W95 FAT32 (LBA)
/dev/sda2                              645                2434    14378175            5  Extended
/dev/sda5                             645                2353    13727511           83  Linux
/dev/sda6                            2354               2434      650601              82  Linux swap / Solaris


[/I]

---

### Post by schober on 2009-04-28
hmmmm..................looks like we're in teh department of mysterious occurances!
i decided to try booting from a floppy. This went ok and i did a DIR and then switched off.
On swiching on again, as if by magic! a boot menu returned and w98 and heron were usable again. So, what fault has been corrected by this process? or are they merely two coincidental events?

---

### Post by Mark Phelps on 2009-04-28
If you installed GRUB in your first partition, my guess is that the filesystem was having integrity problems and, when you rebooted from diskette, the filesystem got repaired.

But, as I said, that's only a guess.

---

### Post by schober on 2009-04-29
thanks for reply mark; i just did the guided instal so i presume grub is in the 1st partition - i still have the problem that booting would "hang" at the blank black screen stage after the boot menu & the ubuntu logo stage & just before login. It is neccesary to switch off at the mains (ie the on/off switch on the computer will not turn it off!) and reboot and all appears ok - it being possible to use heron and w98. This happens erraticly.

---


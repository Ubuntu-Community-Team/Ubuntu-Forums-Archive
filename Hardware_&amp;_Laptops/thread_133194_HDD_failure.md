---
title: "HDD failure?"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by Neo40 on 2006-02-19
Hi,

I was playing a game (Civ IV) then after a while my machine was not responding. I did a hardware reset and here I got after reboot:

Booting 'Ubuntu, kernel 2.6.12-10k7'
root (hd0,0)
Filesystem type is ext2fs, partion type 0x83
Kernel /boot/vmlinuxz-2.6.12-10-7k root =/dev/hda1 ro quiet splash
[Linux-bzImage, setup 0x1c00, size 0x1343bc]
initrd /boot/initrd.img-2.6.12-10-k7
[Linux-initrd @ 0x17a7d000, 0x562c77 bytes]
save default
boot
Uncompressing linux...Ok, booting kernel.
Loading please wait...
mount: Mounting /dev/hda1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesnt have /sbin/init

/bin/sh: can't access tty; job control turned off
#


I have another distro with my second hdd and I tried to mount my Ubuntu's drive but didnt work:

[root@myhost eric]# mount /dev/hdb1 /mnt/hd
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so


Is there a  way to fix it? 
Thanks

---

### Post by dcstar on 2006-02-20
[QUOTE=Neo40]Hi,

I was playing a game (Civ IV) then after a while my machine was not responding. I did a hardware reset and here I got after reboot:
.......
Is there a  way to fix it? 
Thanks[/QUOTE]
Boot into Recovery Mode, and run "fsck -y"

---

### Post by Neo40 on 2006-02-20
[QUOTE=dcstar]Boot into Recovery Mode, and run "fsck -y"[/QUOTE]


I already tried to boot into recovery mode and I had the same error message. But I'll try to run "fsck -y" tonight. I hope it will work!

---

### Post by GNU on 2006-02-20
I had the same problem, after an update to the system (apt-get upgrade), so I used a liveCD to do fsck on my drive, and it was errorless, yet the problem remained.
So, I chrooted to my (broken) system, and tried to apt-get upgrade again, thinking that maybe it's a broken package needed at boot (initramfs?), still no good. 
Then I noticed that in the last update my /boot/grub/menu.list was altered (probably during the first system update I mentioned). I opened the file and the backup (menu.lst~) and noticed my "initrd" lines were replaced by the default one's. Since I use a self-compiled kernel and initrd, I guessed this can be the problem, so I copied the old line over again, reboot and voilla! it works!

So, my offer is that you try to do the same, the solution can be as simple as that. BTW, if we already talk about it, I think it's better to at least NOTIFY the user when the update infrastructure changes its grub configurations. One thing is a broken program, but a broken system that can't boot is something entirely different...

---

### Post by Neo40 on 2006-02-20
[QUOTE=GNU]I had the same problem, after an update to the system (apt-get upgrade), so I used a liveCD to do fsck on my drive, and it was errorless, yet the problem remained.
So, I chrooted to my (broken) system, and tried to apt-get upgrade again, thinking that maybe it's a broken package needed at boot (initramfs?), still no good. 
Then I noticed that in the last update my /boot/grub/menu.list was altered (probably during the first system update I mentioned). I opened the file and the backup (menu.lst~) and noticed my "initrd" lines were replaced by the default one's. Since I use a self-compiled kernel and initrd, I guessed this can be the problem, so I copied the old line over again, reboot and voilla! it works!

So, my offer is that you try to do the same, the solution can be as simple as that. BTW, if we already talk about it, I think it's better to at least NOTIFY the user when the update infrastructure changes its grub configurations. One thing is a broken program, but a broken system that can't boot is something entirely different...[/QUOTE]


Thanks for your tips. I'll try that too. Just one thing, when you said you chrooted to your broken system, how do you do that? Is it just type the command chroot???

---

### Post by Neo40 on 2006-02-20
Well, no luck so far. I booted with a live CD (Mepis), and I can't mount my defect hdd. 

root@1[root]# mount /dev/hdb1 /mnt/hdb1
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

And if I try :
root@1[root]# fsck.ext3 /dev/hdb1
e2fsck 1.39-WIP (31-Dec-2005)
Floating point exception

Other suggestions before I reinstall Ubuntu?
Thanks

---


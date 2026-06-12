---
title: "Grub Gone after Win Reinstall"
date: 2005-01-18
forum: Installation &amp; Upgrades
---

### Post by bkv on 2005-01-18
Hi

I have a machine with Ubuntu Linux and Windows XP on the same drive. Yesterday  had to re-install Windows. Afterwards Grub was gone from the MBR, and I can only boot Windows.

Must I really re-install Ubuntu too. Or is there a way to get Grub in place again?

Thanks,
Bjørn

---

### Post by Yukonjack on 2005-01-18
This might help you out. Also check the help for windows MBR dual booting help on ms site.

[Grub](http://home.nyc.rr.com/computertaijutsu/grub.html)

---

### Post by Stefan Max on 2005-01-18
I have a similar problem, but nothing has helped so far.

I have WinXP and Ubuntu running on the same machine, which worked flawlessly until I resized the partitions using Partition Magic (for Win). After that Grub didn't work anymore (could've thought of that before resizing, I know). I killed the MBR and overwrote it with the Windows-standard.

When I boot from a Knoppix Live-CD (3.4), I can access my old Ubuntu-Drive just fine (/dev/hda5). I can mount it, chroot to it and start grub. Then the following happens:
root (hd0,5)
works.
setup (hd0)
works until "running install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2" and then stops with "Error 12: Invalid device requested".

The same happens without mounting an chrooting /dev/hda5 and just starting grub from Knoppix.

"grub-install hd0" tells me "/boot/hd0/stage1 not read correctly"

I have not found anything about this behavior with google or in various grub-howtos... Any help would be greatly appreciated. Thanks.

---

### Post by Yukonjack on 2005-01-18
It's as been a long time but if I recall you can edit the windows MBR for dual booting from windows I have done this before but I can remember how. As long you have all your info for Ubuntu you should be able to do it. The ms knowlege base as many post on this, it might take a while to find it, huge data base.

Maybe someone else will have an easier way.
Sorry I can help you more.
Good luck

---

### Post by bkv on 2005-01-19
Thanks guys, but I couldn't get any of this to work. I'll proably reinstall Ubuntu one of these days. I'll try to put grub om a diskette then.

---

### Post by kanem on 2005-01-19
hey Stefan Max, 

grub notation has the partition number starting at 0 also, not just the drive number. So /dev/hda5 should be (hd0,4) in grub.

see
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10)

[QUOTE=Stefan Max]I have a similar problem, but nothing has helped so far.

When I boot from a Knoppix Live-CD (3.4), I can access my old Ubuntu-Drive just fine (/dev/hda5). I can mount it, chroot to it and start grub. Then the following happens:
root (hd0,5)
works.
setup (hd0)
works until "running install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2" and then stops with "Error 12: Invalid device requested".
[/QUOTE]

---

### Post by jobdrb on 2005-01-19
May be, Ubuntu people could make an rescue mode in Ubuntu CD, like has in Mandrake.

Where after boot the first cd, your type: rescue
and boot in rescue mode, in this mode you have one menu  with options to reinstall boot loader, and others options

but in principle you could reinstall useing ubuntu livecd

---

### Post by Happy on 2005-03-21
I too am getting this error =(

> Command (m for help): p

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         701     5630751   83  Linux
/dev/hda2             766       14592   111065377+   f  W95 Ext'd (LBA)
/dev/hda3             702         765      514080   82  Linux swap
/dev/hda5             766        1134     2963961    7  HPFS/NTFS
/dev/hda6            1135       14592   108101353+   b  W95 FAT32

Partition table entries are not in disk order

Command (m for help): 
I can boot Ubuntu perfectly, however when I try booting windows I get this error
> Error 12: Invalid Device Requested
I have tried installing lilo but it seemed to get ignored =(

liloconfig
lilo
...
yep, Ubuntu (well Grub) is not Windows friendly   :confused:

---

### Post by Happy on 2005-03-21
Here is a sample from my grub config file


> title		Ubuntu, kernel 2.6.8.1-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.8.1-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,0)
kernel		/boot/memtest86+.bin

title		Windows XP
root		(hd0,4)
makeactive
chainloader	+1
savedefault

---

### Post by dewey on 2005-03-21
Try verifying the partition table through fdisk?

dewey$ fdisk /dev/hda
Command()
v

And it should print out what kind of problems there are, if any.  And it tries to fix them.

---

### Post by Happy on 2005-03-21
all it gives me is this little snippet
> Expert command (m for help): v
16251 unallocated sectors

if I execute 'f' (fix partition order) what is liable to break?

---

### Post by Buffalo Soldier on 2005-03-21
[QUOTE=Happy]yep, Ubuntu (well Grub) is not Windows friendly   :confused:[/QUOTE]I think it's the other way around. MS Windows is not GRUB friendly. In fact it's not friendly with anything FOSS.

---

### Post by Happy on 2005-03-21
[QUOTE=Buffalo Soldier]I think it's the other way around. MS Windows is not GRUB friendly. In fact it's not friendly with anything FOSS.[/QUOTE]


Yes, but that is to be expected  :roll: 
The free Operating Systems have to bend over backwards to accomodate windows, well known fact  ](*,)

---

### Post by Happy on 2005-03-21
Well, the kind people at #grub on irc.freenode.net came to my rescue.
Unfortunately windows was on a logical partition (all I did was swap my linux and windows partitions around so I could have some more space for ubuntu)

this mean't that I didn't require the makeactive command.

so I ended up executing this:

> rootnoverify (hd0,4)
chainloader +1
boot

unfortunately for me the computer just hung after doing this.
now it is time to play with QTParted!
thanks for the help though

---

### Post by gnutux on 2005-03-22
rerun grub-install

gnutux

---

### Post by RiotNrrd on 2005-03-22
I had this very same problem this last weekend.  Had to reinstall Windows (it was bluescreening on boot) and the reinstall wiped out Grub.  Ubuntu was still on my harddrive, but unreachable.

My solution was to create a brand new partition and install Ubuntu's base files there.  That put Grub back on the MBR, but it was using the menu files on the new Ubuntu installation rather than the old one.  However, all three OS installations were listed at boot - Windows, my first Ubuntu install (the one I wanted to keep), and the second install (which only contained a skeleton of an Ubuntu installation and whose future I cared nothing about).  I booted into my "good" (i.e., first) Ubuntu installation and ran grub-install.  That repointed the Grub files in the MBR to the menu list in the "good" installation instead of the one in the new installation.  Then I removed the new partition, which I never even booted into.

Worked like a charm, even if it's a total kludge.

---

### Post by Happy on 2005-03-22
Fixed the problem.
Booted into Knoppix 3.7 using the knoppix noswap cheatcode
I deleted the windows partition from the logical partition.
Shrunk the logical partition and shuffled it over.
Grabbed the swap partition and shuffled it over leaving me with a ReiserFS system on /dev/hda1 which I can not move and has Ubuntu on it.

So I rebooted into Ubuntu, fixed the /etc/fstab file (forgot to do it in Knoppix)
than I started installing windows XP, formatted the empty partition (/dev/hda2) and rebooted the computer (because /dev/hda2 was pointing to G:)
Than I installed windows XP into /dev/hda2 pointing to C:

After that I rebooted using the Ubuntu cd and used the guide at [http://UbuntuGuide.org](http://UbuntuGuide.org) to reinstall grub in /dev/hda1 (unfortunately lpr spat out 20 copies of the guide before I realised what was happening, stupid high speed incorrectly configured laser printers)
adjusted the grub menu items and voila, everything worked like a charm...

scrap paper anyone?
I'm not too sure which method is more clunky, RiotNrrd's or mine  =D>

---

### Post by RiotNrrd on 2005-03-22
**I'm not too sure which method is more clunky, RiotNrrd's or mine  **

LOL.  Once I figured out what I had to do, it took just a few minutes to accomplish.  So I'm going out on a limb here and claiming my method is nowhere near as clunky as yours!   :lol:

---

### Post by remmelt on 2005-04-08
check this out too if you want to re-install grub. i know it's in the hoary forum, but it's the same for warty (plus, we're all upgrading anyway, right? :) )

[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---


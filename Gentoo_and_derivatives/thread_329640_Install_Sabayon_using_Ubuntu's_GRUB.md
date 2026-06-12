---
title: "Install Sabayon using Ubuntu's GRUB"
date: 2007-01-01
forum: Gentoo and derivatives
---

### Post by Crashmaxx on 2007-01-01
I tried the mini Sabayon CD and was very impressed. So I installed it, but I didn't have it install grub because I didn't want it to overwrite my current one Ubuntu installed.

But now I have no idea what I need in the menu.lst to boot Sabayon. And after looking for help, it looked like I might need to install grub on the Sabayon partition and chainload, but that doesn't sound right.

So what entry do I need in my menu.lst to boot Sabayon?

Do I need to install grub again for Sabayon, and if so, how?

Thanks, this a common problem for people dual booting Ubuntu and Sabayon, surprisingly.

---

### Post by d3v1ant_0n3 on 2007-01-01
I've actually been looking for a solution to the same problem, but the other way around- I installed sabayon, and installed GRUB with it, and it cleared Ubuntu's GRUB, so I've had to add Ubuntu to sabayon's grub. But as of yet I haven't quite got it going properly yet apparently (I have to edit the grub entry on boot for edgy)

---

### Post by RAV TUX on 2007-01-02
Try the [**Super Grub** Disk.]("http://supergrub.forjamari.linex.org/documentation.php")

---

### Post by d3v1ant_0n3 on 2007-01-02
Well I * think *I've solved my problem- I copied the grub menu entires from Ubuntu's to sabayon's, and it seems to work.

I did have to remove a line from my default Ubuntu tho (savedefault) and I'm not entirely sure what I'm losing by not having this in place.

---

### Post by mysticrider92 on 2007-01-19
This is the menu.lst entry I have been using for Gentoo:> title		Gentoo
root  		(hd0,1)
kernel 		/boot/kernel-genkernel-x86-2.6.17-gentoo-r7 root=/dev/sda2
initrd		/boot/initramfs-genkernel-x86-2.6.17-gentoo-r7

You will need to edit the kernel, root, and initrd lines to match the appropriate files and partitions on your computer, but that is all you need.

---

### Post by rplantz on 2007-02-01
I worked for a long time with grub to build a triple-boot system: Ubuntu; Debian; Gentoo. My grub is only installed on the disk that my bios tries to boot from first (after the floppy and cd).

Here are my disk partitions (from ldisk -l):
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            9363        9727     2931862+  82  Linux swap / Solaris
/dev/sda3            1217        9362    65432745   83  Linux
/dev/sda4            9728       19457    78156225    5  Extended
/dev/sda5   *        9728       10578     6835626   83  Linux
/dev/sda6           10946       19457    68372608+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1           5       40131   83  Linux
/dev/hdc2               6        9729    78108030    5  Extended
/dev/hdc5               6          68      506016   82  Linux swap / Solaris
/dev/hdc6              69        1936    15004678+  83  Linux
/dev/hdc7            1937        9729    62597241   83  Linux

```

Here are the relevant parts of my /boot/grub/menu.lst file.

First for Ubuntu:
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```
Notice from this that my bios is set up to boot from my SATA disk. grub calls the first disk hd0. My / partition is the first one on this disk, and grub calls that partition number 0. Hence, I tell grub that root is (hd0,0). Once grub finds the right disk/partition, we're back into linux disk naming. So I tell linux that the root is /dev/sda1, which is the first partition on my SATA disk.

Aside: If I told my bios to try my PATA disk first, I would then have to use (hd1,0) for grub's root, but my linux root would still be /dev/sda1.

Okay, here's my entry for Debian, which is also on my SATA disk:
```

title           Debian GNU/Linux, kernel 2.6.17-2-amd64
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-2-amd64 root=/dev/sda5 ro 
initrd          /boot/initrd.img-2.6.17-2-amd64
savedefault

```
Here, I tell grub to use my extended partition on my SATA disk, (hd0,4).

My Gentoo installation is on my PATA disk, and its /boot/grub/menu.lst entry is:
```

title           2.6.18-gentoo-r6
root            (hd1,0)
kernel          /boot/kernel-2.6.18-gentoo-r6 root=/dev/hdc6

```
The first partion on this disk (/dev/hdc1 in linux speak) is the Gentoo /boot partition. That's were my kernel is. Since my bios is set to consider my PATA disk as the second one, grub calls the first partition on this disk (hd1,0).

I learned this stuff from lots of reading and trial and error. I suspect that I have things in the /boot/grub/menu.lst entries that are not really required. And please realize that my explanation is partially rationalization. That is, I think this is the what's going on, but the main evidence I have is that it works on my system. :)

---

### Post by V-600 on 2007-02-06
I think i follow the logic in the post above but i still have problems getting sabayon to boot up.
I am presented with "Error 17: Unable to mount the selected partition" (if my memory serves)

This is my /boot/grub/menu.lst file

title           2.6.18-gentoo-r5
root            (hd0,1)
kernel          /boot/kernel-2.6.18-gentoo-r5 root=/dev/hda4
boot

This entry is after the three default Ubuntu ones, but before "### END DEBIAN AUTOMAGIC KERNELS LIST". I didn't think that makes a difference though.

I have just noticed the name of the kernal file is "kernel-genkernel-x86-2.6.18-gentoo-r5" and will change it now but again i don't think it would make a difference to whether or not the partition mounts

---

### Post by Crashmaxx on 2007-02-06
I had it working with similar settings. But now I did a fresh install of the 3.26 DVD and now I keep getting the error "invalid root block". This is my menu.lst:
```

title Sabayon Linux x86 3.26
        root (hd0,7)
        kernel /boot/kernel-genkernel-x86-2.6.19-gentoo-r4  root=/dev/ram0 ramdisk=8192 real_root=/dev/hda8  quiet  init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 pci=nomsi
        initrd /boot/initramfs-genkernel-x86-2.6.19-gentoo-r4 

```

---

### Post by igknighted on 2007-02-07
> **V-600 said:**
> I think i follow the logic in the post above but i still have problems getting sabayon to boot up.
I am presented with "Error 17: Unable to mount the selected partition" (if my memory serves)

This is my /boot/grub/menu.lst file

title           2.6.18-gentoo-r5
root            (hd0,1)
kernel          /boot/kernel-2.6.18-gentoo-r5 root=/dev/hda4
boot

This entry is after the three default Ubuntu ones, but before "### END DEBIAN AUTOMAGIC KERNELS LIST". I didn't think that makes a difference though.

I have just noticed the name of the kernal file is "kernel-genkernel-x86-2.6.18-gentoo-r5" and will change it now but again i don't think it would make a difference to whether or not the partition mounts

assuming that you know it is on that partition (partition 2 of disk 1), try this:

1) reboot and let grub load

2) hit 'e' when you get to the menu, over the sabayon entry.

3) go to the kernel line and hit 'e' again

4) now erase the path to the kernel and the root=/dev/**** sections for the moment.

5) for the new path, type this: (hd0,1)/boot/ then hit tab, it should give you a list of files in that folder.  Start typing the filename for the kernel you want to boot, then hit tab to auto complete.

6a) If you did get the proper kernel using this method, re-enter you root=/dev/**** as it was before.

6b) If you dont get the proper file, you have the wrong partition.  Try this method a few times, changing the (hd0,1) to other partitions/HD's you have until you find the proper one.  Then add the corresponding root=/dev/****.

7) do the same to the initrd entry (hd0,1)/boot/ <tab>, find filename, start typing and tab again to autocomplete.

8) write down the combination that works, because it wont save when you boot.  You still need to change the menu.lst file so you don't have to do this every time you boot.

9) hit 'b' to boot when you are ready

ONE FINAL NOTE: On your entry above you have root (hd0,1), and then root=/dev/hda4... if hda is hard disk 0 (the disk grub boots from) then that would be (hd0,3) for root=/dev/hda4.  You might need to change that as well.

ALSO: Instead of using (hd0,x) in front of each pathname, if you have the sabayon drive mounted on the ubuntu install you could use the path through that mount point (for me its /sabayon/boot/kernel, but use your own mount point).  Either should work fine, use the method in this paragraph if you know the pathname definitely, or the method above if you might need to trial and error it a bit.

---

### Post by V-600 on 2007-02-07
I kept fiddling with it last night and have found an alternate solution. I just booted into ubuntu, mounted hda4 and copied the kernal from sabayon "/boot" into ubuntu's "/boot". Then copied and pasted one of the ubuntu entries and just changed the filenames.

title           2.6.18-gentoo-r5
root            (hd0,0)
kernel          /boot/kernel-genkernel-x86-2.6.18-gentoo-r5 root=/dev/hda4
initrd		/boot/initramfs-genkernel-x86-2.6.18-gentoo-r5
boot

This may not be too elegant but is simple and worked for me.

Purely out of interest now. The section root (hd0,0) confuses me, so i welcome clarification. The first "0" (i.e. hd**0**0) refers to the first hard disk? The second "0" (hd0,**0**) refers to partitions on the disk? As such, does it refer to them in physical order or by number. My disk has hda1(ubuntu), hda4(sabayon), hda3(/home), hda2(hda5 swap). I assumed hd0,1 would point at the second partition. Was i actually trying to mount the swap file?

---

### Post by rplantz on 2007-02-08
> **V-600 said:**
> 
Purely out of interest now. The section root (hd0,0) confuses me, so i welcome clarification. The first "0" (i.e. hd**0**0) refers to the first hard disk? The second "0" (hd0,**0**) refers to partitions on the disk? As such, does it refer to them in physical order or by number. My disk has hda1(ubuntu), hda4(sabayon), hda3(/home), hda2(hda5 swap). I assumed hd0,1 would point at the second partition. Was i actually trying to mount the swap file?

In the syntax (hdn,m), n is the disk number and m is the partition number. However, grub starts numbering from 0, not 1. And disk number is the boot order set in your bios.

I think you have a typo in "hda2(hda5 swap)".

It looks like you have one disk. grub would call it hd0, and linux calls it hda. So I think it's like this:
```

       partition   linux                  grub               your use
              1         /dev/hda1        (hd0,0)           ubuntu
              2         /dev/hda2        (hd0,1)           swap
              3         /dev/hda3        (hd0,2)           /home
              4         /dev/hda4        (hd0,3)           sabayon

```
If my understanding of grub is correct, you first have to tell it which disk to go to with something like
```

root            (hd0,0)

```
But once it has started with that disk, linux takes over and you have to switch to the linux terminology with something like:
```

kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash

```
Of course, a different OS might use a different terminology. A few months ago I got freeBSD to boot from my grub. I forget the terminology now, but it's different from linux.

If a more knowledgeable person sees any errors here, please correct me. I'm trying to enhance my understanding, too.

---


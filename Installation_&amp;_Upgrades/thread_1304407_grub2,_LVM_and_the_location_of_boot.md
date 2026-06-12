---
title: "grub2, LVM and the location of /boot"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by 1jackjack on 2009-10-29
Hello everyone. I've been having some fun trying to dual-boot Karmic with Fedora 11 using LVM, and have some questions. I have 1 hard drive: hd0 (80GB). Someone else already had Fedora installed, with the disk arranged in the following way:

```

sda1: 200MB ext3 partition for /boot

sda2: 70GB partition using LVM which holds 1 volume group:
   vg_dev02: volume group containing 2 logical volumes:
      lv_root: 65GB for / (root)
      lv_swap: 3GB for swap

```

So then I wanted to install Karmic for a dual boot setup, so I shrank lv_root (yes; the filesystem, THEN the logical volume) and added another logical partition called lv_koala_root. Then *without thinking* (I was rather blindly following another guide), I formatted sda1 and used it for the /boot of my new Karmic install. The install went fine (I used the Alternate installer, which deals with LVM), and I'm now successfully using grub2 to boot into Karmic, which resides on a logical volume. The only problem is that grub2 shows no option for fedora (obviously, as that install no longer has a /boot directory). But doing update-grub does find it:

> 
jack@ubuntu:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /memtest86+.bin
Found Fedora release 11 (Leonidas) on /dev/mapper/vg_dev02-lv_root
done


So what should I do? Can I just populate the /boot of my fedora install in the logical volume lv_root, and tell grub2 to use that instead of looking for /boot on sda1? Or in order to boot, does grub2 need each OS's /boot on a non LVM partition?

Cheers,
Jack

---

### Post by PAC1 on 2009-12-04
Did you find a solution?  I've got the same problem.  I updated to GRUB2 (using the grub-pc route) and update-grub finds everything but doesn't bother to add an option for the system "Scientific Linux" (which resides in an LVM partition) to the grup.cfg.  Anyone have any ideas why?


sudo update-grub

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.27-11-generic
Found initrd image: /boot/initrd.img-2.6.27-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Scientific Linux SL release 5.2 (Boron) on /dev/mapper/VolGroup00-LogVol00
done

---

### Post by Herman on 2009-12-04
I don't know for sure if it would be easily possible to boot a kernel and initrd.img which are located inside an LVM. 
All the LVM installations I've seen have their own separate /boot partition which houses the kernel and initrd.img files as well as the boot loader files for that particular operating system. 
I suggest you could try downloading an up to date kernel and initrd.img file for Fedora or Scientific Linux and copy those to any partition that's not inside a logical volume.
It shouldn't matter where outside your logical volumes you put them, in your Ubuntu /boot partition should do if there's room or in some other partition, even a partition in a USB flash memory stick should work if your computer's BIOS is capable of booting from a USB.

You should be able to boot any kernel and initrd.img and get them to look for your specified root file system using GRUB 2 in command line mode, (press your 'c' key while your GRUB Menu is showing to shift into command line mode).
Once you get the kernel to load, it should have the drivers for your logical volume and if you have an encypted logical volume you can expect to be prompted for your passphase and your operating system should begin to boot.

---

### Post by Herman on 2009-12-04
I have a Karmic installation in an encrypted file system in an LMV partition and I was able to boot it with a kernel from another Karmic installation in a different hard disk with,
(from command line GRUB2),
for a list of disk drives:
```
cat (hd <tab>
```for a list of partitions in (hd1),
```
cat (hd1, <tab>
```to tell GRUB2 which partition to focus on (the one containing the Linux kernel I want to use),
```
set root=(hd1,1)
```command to load the kernel and tell it which file system to use for root,
```
linux /vmlinuz-2.6.31-14-generic root=/dev/mapper/t310--kryptokarimc-root

```where: I used tab completion after typing the first three letters of the kernel's name, and where: 't310--kryptokarmic-root' is the name of the logical volume. You might need to run 'sudo blkid' from a live CD to find out.

command to load the initial ram disk,
```
initrd /initrd.img
```command to boot,
```
boot
```That should be all you need if your LVM partition contains a plain ordinary file system.


I had some extra difficulties myself because mine has a LUKS encrypted file system and I found that it seems I need to use the original initrd.img file that belongs to that particular encrypted file system. (So I *cheated* a bit by copying that to my other operating system's /boot directory).
If you have an encrypted file system like I do and you don't have the initrd.img for it, (I presume you wouldn't), you should be able to make one with the mkinitramfs command, and I imagine you should be able to do that if you chroot into the operating system that you're trying to fix before running the mkinitramfs command.
While you're in there you'll probably need to edit your /etc/fstab too, it might still be looking for your deleted /boot partition that once belonged to Fedora or Scientific Linux.

Actually, you might even find it easier to just chroot into your Fedora or Scientific Linux partition and install a new kernel for it, that will come with it's own initrd.img file, that would be another work-around and might be the easiest method of all, but with me not being familiar with Scientific Linux or Fedora, I'm not sure what commands you might need to download and install your new kernel with.

---

### Post by PAC1 on 2009-12-08
In my case the kernal images already live on a small ext3 partition outside of the LVM volume.

Booting Scientific Linux isn't really my problem - I can manually add a custom boot option to Grub2.   I was basically wondering why "update-grub" can't find the images automatically?

Clear it can recognise the root LVM volume, as its listing it, but I guess it doesn't know to tie together the external ext3 partition with the main system.

---

### Post by 1jackjack on 2009-12-08
@PAC1: I'm not sure why update-grub doesn't find the images automatically; if the /root is outside the LVM, it seems like it should find it and add it. It did that for me when I installed Karmic, so pressumably it does some extra grub linking trickery while you are installing the OS (with the alternate installer which has added LVM support)

@Herman: Thanks a lot for your reply. I am very busy atm, but I will try this when I get a chance.

---

### Post by PAC1 on 2009-12-08
Okay, seems I kind of got it with my last comment.

As the external ext3 "/boot" partition is not part of the LVM partition the *update-grub* script can't find anything in the dangling /boot dir where it find the Scientic Linux root ( /dev/mapper/VolGroup00-LogVol00/ ).  Thus it doesn't add anything to grub.cfg.

If I copy a kernel image into /dev/mapper/VolGroup00-LogVol00/boot/ then update-grub will quite happily generate a menu option for this item.  Unfortunately the menu option it generates is garbage.   The update-grub script doesn't correctly map the partition the system can actually boot from, (i.e. if you select this newly generated option the kernel images boots but then panics).

I guess piecing together how this LVM partition is supposed to boot is just hard to figure out automatically.

I'll just have to live with manually adding the correct info to /etc/grub.d/40_custom.

---

### Post by PAC1 on 2009-12-08
> **1jackjack said:**
> @PAC1: I'm not sure why update-grub doesn't find the images automatically; if the /root is outside the LVM, it seems like it should find it and add it. It did that for me when I installed Karmic, so pressumably it does some extra grub linking trickery while you are installing the OS (with the alternate installer which has added LVM support)


I think my Ubuntu installation existed prior to installing Scientific Linux, though the upgrade to GRUB2 was a recent change.  I guess the Ubuntu LVM installer could be cleverer, though I'm not sure how it could guess that /dev/sdaX is the boot partition for LVM Volume00 with out looking into fstab on each volume? ... suppose it could do that ...

---


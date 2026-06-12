---
title: "Can't chainload boot grub2 in Ubuntu 9.10 from grub legacy"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by MrMerry on 2009-11-03
Hi,

I installed Ubuntu 9.10 (standard edition and Netbook remix) on a multiboot Acer netbook and chose to install the grub2 bootloader to the boot sector of installation partition (sda7) rather than the MBR. I have several distros booting from legacy grub (grub 0.97 installed on the MBR) using 'chainloader +1' method , but for Ubuntu it gives an error 'Invalid or Unsupported executable format'.

I can boot succesfully by copying the vmlinuz and initrd files to my legacy grub /boot partition and using the usual stanza in grub-legacy:

title Ubuntu 9.10
root (hd0,1)
kernel /vmlinuz-2.6.31-14-generic root=/dev/sda7 quiet splash
initrd /initrd.img-2.6.31-14-generic


But I would like to use:

root (hd0,6)
chainloader +1

After boot I tried using grub-setup and grub-install:

```
root@aaounr:~# grub-setup /dev/sda7 --force
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
root@aaounr:~# grub-install /dev/sda7
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb

```But still no luck, I get the same error 'Invalid or Unsupported executable format'.

I found a thread on another forum where the same problem is encountered on earlier alpha version of Ubuntu 9.10, [http://www.justlinux.com/forum/showthread.php?t=152784](http://www.justlinux.com/forum/showthread.php?t=152784)

Has anybody got Ubuntu 9.10 Grub2 bootloader to chainload succesfully from grub-legacy. If so, any ideas what I might try to fix it here?

---

### Post by coffeecat on 2009-11-03
> **MrMerry said:**
> Has anybody got Ubuntu 9.10 Grub2 bootloader to chainload succesfully from grub-legacy.

Rather bizarrely I did from an alpha install of Karmic, but since then all the Betas and Finals I've tried to install give the same error message after grub-setup as you get.

But despair not! I have a solution.

Try this in your legacy grub menu.lst

```
title Karmic grub2 menu 
root (hd0,6) 
kernel /boot/grub/core.img
```Goodness only knows how it works (I found it in a thread in the now-closed Karmic development subforum) but it seems to do what chainload would have done if only grub2 was working properly.

**Edit** by the way, I think there's a typo in:

> title Ubuntu 9.10
root (hd0,1)
kernel /vmlinuz-2.6.31-14-generic root=/dev/sda7 quiet splash
initrd /initrd.img-2.6.31-14-generic

There's a clash between the root value in the root line and in the kernel line. And you need 'kernel (hd0,6)/boot/grub/vmlinuz.....' etc. 

Which reminds me there's another way of booting into Karmic from legacy grub which gets round the problem of that stanza. The next time you do a kernel update in Karmic you'll need to edit the stanza. Have a look in the root of the Karmic partition - you'll see symlinks vmlinuz and initrd.img pointing to the latest version. The symlinks get updated every time there's a kernel update. You can take advantage of this with:

```
title Ubuntu 9.10
root (hd0,6)
kernel /vmlinuz root=/dev/sda7 ro quiet splash
initrd /initrd.img
```

Of course, this completely bypasses grub2.

---

### Post by MrMerry on 2009-11-03
thanks coffeecat, that first suggestion works :)

But I have to use a separate /boot partition (sda6) formatted as ext3 since the install partition for Ubuntu 9.10 ( sda7) is ext4, and my legacy grub doesn't work with ext4. (That's why you thought I had a typo)

I now use this in grub legacy's grub.conf:

```
title Ubuntu 9.10
root (hd0,5)
kernel /grub/core.img
```(Note my path's are relative to /boot not to /, since /boot is on its own partition)

So once legacy grub is patched to support ext4 (it is in the upcoming Fedora 12) I can reinstall Ubuntu 9.0 on a single partition and chainload as per your post, I'm happy enough now, since I can play with grub2 (without putting it on the mbr)

Thanks!

---

### Post by coffeecat on 2009-11-03
I'm glad it worked.

Out of interest, which distro's legacy grub are you using? I was under the impression that the current Fedora legacy grub supported ext4 - I must be wrong. Certainly Ubuntu Jaunty's (9.04) legacy grub does because ext4 was an option for the root partition in Jaunty.

---

### Post by MrMerry on 2009-11-03
I using Fedora 11's grub 0.97. On ext4 partitions it returns 'File not found' errors. They have patched it for the upcoming Fedora 12 release though.

---


---
title: "error: no such device  UUID error I think??"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by ubuntoPete on 2009-10-30
I have downloaded the 9.10 iso and burnt it to a disk.  It seems to install with no errors and then tells me to take out the disk, close the draw and press enter to reboot.  All good so far I thought.

After the reboot I get the Grub loading but then get the following
error: no such device: xxxxx-xxxx-xxxx-xxxxxxxxxx (it's a very long number)
Press any key to continue...

I press a key and get a GNU GRUB version 1.97~beta4 screen.  Both the Ubunto, Linux 2.6.31-14-generic and the recovery mode option just give the same error.

If I click "e" to edit I get a complicated set of commands 2 lines of which contain the xxxxx-xxxxx-xxxx-xxxxx number.

I am using an IBM Thinkpad T40 with a single HDD.

I suspect that I need to do something with the UUID number but I don't know what or how. :(

Any help would be brilliant.

Cheers

---

### Post by hal10000 on 2009-10-30
Notice the UUID number, then boot from a live-cd (knoppix, ubuntu or similar) and perform this command:
```
blkid
```
in the output search for your ubuntu boot partition and check wether it has the same UUID as you noticed (i guess it has not).
Notice the UUID you found for your boot partition with the **blkid** command. This is the correct UUID, which has to be replaced in the /boot/grub/menu.lst file and the /etc/fstab file of your ubuntu system partition.
TO replace the entries you first have to mount the ubuntu partition, e.g. if /dev/sda2 is your ubuntu system partition then perform:
```
sudo mount /dev/sda2 /mnt
```
Then edit the menu.lst file as root:
```
gksudo gedit /mnt/boot/grub/menu.lst
```
scroll to the line which looks similar to this one (this is from my own menu.lst):
```

# kopt=root=UUID=1a8cdf2e-e6f9-4020-a751-30f83844bc82 ro

```
and replace the UUID here with the UUID you found with blkid for your ubuntu system.

Then scroll down and find the part which looks similsr to this one (again from my own menu.lst):
```

## ## End Default Options ##

title           Ubuntu 9.04, kernel 2.6.28-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=1a8cdf2e-e6f9-4020-a751-30f83844bc82 ro
initrd          /boot/initrd.img-2.6.28-16-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=1a8cdf2e-e6f9-4020-a751-30f83844bc82 ro  single
initrd          /boot/initrd.img-2.6.28-16-generic

title           Ubuntu 9.04, kernel 2.6.28-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=1a8cdf2e-e6f9-4020-a751-30f83844bc82 ro
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=1a8cdf2e-e6f9-4020-a751-30f83844bc82 ro  single
initrd          /boot/initrd.img-2.6.28-15-generic

```
Replace the UUID here again with the UUID you found with **blkid**
Save the file.

Next, we have to take a look into the /mnt/etc/fstab file an also replace the UUID for your ubuntu system partition with the UUID you found with blkid (edit the fstab file as root).

Btw., in the fstab file the UUID's of other partitions (swap, data partitions, windows partition etc.) must be the same as you found with the blkid command, so maybe you have to change these too

I hope this can help you. If you have separate partitions for your /boot and / (root) and you don't know how to handle this, the post it here and we can take some other steps to get your system working again.

---

### Post by ubuntoPete on 2009-10-30
Thanks for this

my fstab file has the correct values and is all good.

I do not have a menu.lst file in the boot grub directory.  I see this might be a problem but I don't know what to do about it.

---

### Post by hal10000 on 2009-10-30
> I do not have a menu.lst file in the boot grub directory. I see this might be a problem but I don't know what to do about it.
If you don't have a /boot/grub/menu.lst file in your ubuntu system, then something went wrong during the installation-process, although i can't believe that you don't have a menu.lst file, because if you can see a boot menu upon booting, then you must have a menu.lst file, the bot menu is stored just in this file.

Neverthless, something went wrong and you should boot from the live-cd. Then post the output of the command
```
sudo fdisk -l
```
to see the partitions of your harddrives.

---

### Post by mechro on 2009-10-30
> **hal10000 said:**
> If you don't have a /boot/grub/menu.lst file in your ubuntu system, then something went wrong during the installation-process, although i can't believe that you don't have a menu.lst file, because if you can see a boot menu upon booting, then you must have a menu.lst file, the bot menu is stored just in this file.

Neverthless, something went wrong and you should boot from the live-cd. Then post the output of the command
```
sudo fdisk -l
```
to see the partitions of your harddrives.

It might now be grub.cfg amongst other things. Grub is changing.

---

### Post by axel_2078 on 2009-10-30
This is the exact problem I'm having. However, I don't have a /boot/grub/menu.lst file on my installation either. I have /boot/grub/grub.cfg. The UUID for the boot partition seems to match what is listed when I run blkid. I looked in the fstab file as well and the UUID matched for the boot partition and for the swap partition. I don't understand what's going on here. I still can't boot.

---

### Post by hal10000 on 2009-11-01
I'm sorry but i have no expeience with the new grub2 configuration.
Maybe this is the right place for you: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Chirpz on 2009-11-04
I have the problem to.  Here is a work around to boot.

Turn on the machine.  As soon as it starts to boot press SHIFT or press ESC to bring up the boot menu.  

Hightlight the first line and press E to edit.

Cursor down to the line that says "search --no floppy etc etc"

Use the delete key and delete the whole line and any part of it that wrapped below it

Now hold the cTRL key and press X to boot.

I have a laptop with NO floppy and this works for me...but you have to
do it every time you boot up..it does not fix the problem

The problem is in the grub.cfg file I think

---

### Post by VEute on 2009-11-05
I have the same problem as ubuntoPete as well. It seems like I get an error about no such device flash past just before I get the Grub boot menu as well.
I've tried most of the things I can find on the forums here with no success. If I boot on the live cd and follow the threads in the grub2 forum to try and reinstall grub to not use the UUID, it doesn't find the disk at all.

For what it's worth, I tried to install 9.10 on a spare pc and had the same trouble. I put an IDE disk into the spare pc instead of the normal sata and even though it would not install without running the install from within the live cd, when it did install it works fine. On this install I don't even see the grub menu, it boots straight to 9.10.

---

### Post by snoopyq on 2009-11-06
> **Chirpz said:**
> I have the problem to.  Here is a work around to boot.

Turn on the machine.  As soon as it starts to boot press SHIFT or press ESC to bring up the boot menu.  

Hightlight the first line and press E to edit.

Cursor down to the line that says "search --no floppy etc etc"

Use the delete key and delete the whole line and any part of it that wrapped below it

Now hold the cTRL key and press X to boot.

I have a laptop with NO floppy and this works for me...but you have to
do it every time you boot up..it does not fix the problem

The problem is in the grub.cfg file I think


your right.. grub.cfg is rooted...  just shove a ; in front of that line & continue, no need to delete the whole line.. (still f## retarded tho)

---

### Post by exXplode on 2009-11-11
> **Chirpz said:**
> 
original post, just reformating to hightlight the working work around


[SIZE="4"]**Confirmed to work**[/SIZE] as a **work around** to be able to startup:
[LIST]
[*]Turn on the machine.  As soon as it starts to boot press SHIFT or press ESC to bring up the **grub boot menu**. (or press enter after grub error message)
[*]Hightlight the first line and press **[e]** to edit.
[*]Cursor down to the line that says *search --no floppy etc etc*
[*]Use the delete key and **delete the whole line** and any part of it that wrapped below it
[*]Now hold the **[Ctrl] key and press [x]** to boot.
[/LIST]

---


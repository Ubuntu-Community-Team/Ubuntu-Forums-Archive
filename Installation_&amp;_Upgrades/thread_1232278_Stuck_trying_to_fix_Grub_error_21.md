---
title: "Stuck trying to fix Grub error 21"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by Lithium Rain on 2009-08-05
So long story short I must have screwed up when I installed ubuntu to an external hdd connecting to my current box, because I get grub error 21 and have to use super grub disk to boot at all (and I can't figure out how to use the disk to fix it... :\ ).

Anyway, I followed the instructions found here: [https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing)

(from which I'll just copy/paste) but I'm stuck after I do the following:

```
$sudo fdisk -l
```*mount each to see which /dev/sda has what. Once you done that you need to mount your root 1st, in my case /dev/sda2 *

```
$sudo mount /dev/sda2 /mnt
```*if you ls your /mnt you should see /boot, /dev, /home etc from your HDD. Now mount your /boot in my case it is on a separate partition called /dev/sda1 *

```
$sudo mount /dev/sda1 /mnt/boot
```*Next you need to bind mount all your devices from USB to the HDD... *
```
$sudo mount --bind /dev/ /mnt/dev
```*chroot into your HDD system and fix things... *

```
$sudo chroot /mnt
```

So I do all that. It all looks good and tells me what I need to know.
So far, so good. But when I attempt to do the next thing,

*now you can run the command grub-install again to install grub to your /dev/sda *




```
$sudo grub-install /dev/sda
```

```
$sudo grub-install --recheck /dev/sda
```

[I]Hit CTRL+D to get out of the chroot, unmount dirs in LIFO order, /mnt/dev, /mnt/boot and /mnt. reboot the system and you are good to go!

[/I]It fails. It tells me 

/dev/sda: Not found or not a block device.

So I thought maybe I need to append 1 on it. But I get the exact same thing trying to do it to /dev/sda. It's already mounted; mtab tells me so.

I'm really at a loss here...not quite sure what to do...I'd appreciate any help. :)

---

### Post by running_rabbit07 on 2009-08-05
I would recommend install Ubuntu on local drive. You only need to use about 10 gigs of the local drive to install and then save all other files tot he external drive.

---

### Post by ibuclaw on 2009-08-05
> **Lithium Rain said:**
> So long story short I must have screwed up when I installed ubuntu to an external hdd connecting to my current box, because I get grub error 21 and have to use super grub disk to boot at all (and I can't figure out how to use the disk to fix it... :\ ).


Follow the routine as usual
```
sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo mount --bind /dev/ /mnt/dev
sudo chroot /mnt

```
But once inside the chroot environment, run the following:
```

mount -t proc proc /proc
mount -t sysfs sys /sys
mount -t devpts devpts /dev/pts

```

Then continue on with the installation.

Once finished, type in:
```

sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt

```

Although, and alternative would be to use Karmic Alpha.
Grub 2 will be the default in Karmic. So you may be better off testing it there. :)

Regards
Iain

---

### Post by Lithium Rain on 2009-08-05
> **tinivole said:**
> Follow the routine as usual
```
sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo mount --bind /dev/ /mnt/dev
sudo chroot /mnt

```But once inside the chroot environment, run the following:
```

mount -t proc proc /proc
mount -t sysfs sys /sys
mount -t devpts devpts /dev/pts

```Then continue on with the installation.

Once finished, type in:
```

sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt

```Although, and alternative would be to use Karmic Alpha.
Grub 2 will be the default in Karmic. So you may be better off testing it there. :)

Regards
Iain


Thank you very much for your help! 

It *almost* works. Everything worked flawlessly when I did the first series of commands you gave me. When I then tried to 

```
$sudo grub-install /dev/sda
```

It told me

/dev/sda does not have any corresponding BIOS drive.

I read about it a little bit and it was suggested to try 

```
# grub-install --recheck /dev/sda
```So I ran that and got:

Could not find device for /boot: Not found or not a block device.

I'm sure I'm being very dense, but I still can't get it.    ](*,)](*,)

---

### Post by Lithium Rain on 2009-08-07
I fixed it. :D

I followed the instructions found here : [http://ubuntuforums.org/showthread.php?t=866246&highlight=grub+error+21](http://ubuntuforums.org/showthread.php?t=866246&highlight=grub+error+21)

only instead of hd(0,0) I had to put the hd inside the parenthesis (hd0,0).

I'm sooooooooooooooo happy. I have my bootloader back! I was beginning to think I'd have to use Super Grub Disk to boot for the rest of my days (and would never get winblows back...). :KS

---


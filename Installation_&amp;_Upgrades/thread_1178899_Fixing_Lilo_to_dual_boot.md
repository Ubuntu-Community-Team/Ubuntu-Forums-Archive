---
title: "Fixing Lilo to dual boot"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by dmanno on 2009-06-05
Hi all, 
I have installed Ubuntu 9.04 and Vista before that. (64-bit of each). I now can not get back into Linux. I have tried many things. I am trying to get Lilo to run again so I can get into Linux. I'm in the Live CD terminal trying to get it all to work. Please see below for disk configuration and lilo.conf printout. I only have one hard drive but I've been getting some RAID errors. Maybe there's something funky in my lilo.conf file? 

Here's what I want to do: I want to install lilo onto the Linux root partition so that I can use Vista's EasyBCD bootloader. When I installed lilo onto the MBR, it overrode EasyBCD. When I replaced the EasyBCD bootloader, it overrid the lilo bootloader which is where I'm at now. Here's my info:

(/dev/sda4 has my Linux root, /dev/sda2 has my Linux /home, /dev/sda1 is Vista, /dev/sda5 is Linux swap)

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+ 172297- 172298- 1383981048    7  HPFS/NTFS
/dev/sda2     178034  181553    3520   28274400   83  Linux
/dev/sda3     181554  182400     847    6803527+   5  Extended
/dev/sda4     172298  178033    5736   46074420   83  Linux
/dev/sda5     181554+ 182400     847-   6803496   82  Linux swap / Solaris


lilo.conf:

**************************************************
large-memory
lba32
boot=/dev/sda4
map=/boot/map

# message=/boot/bootmess.txt
        prompt
        delay=100
        timeout=100

default=Linux

image=/vmlinuz
        label=Linux
        read-only
        append="root=/dev/sda4  "
        initrd=/initrd.img

image=/vmlinuz.old
        label=LinuxOLD
        read-only
        optional
        append="root=/dev/sda4  "
        initrd=/initrd.img.old

other=/dev/sda1
        label=Windows
**************************************************

When I try to then re-configure lilo, i get this:

root@ubuntu:/etc# sudo /mnt/ubun/sbin/lilo
Warning: Partition 4 on /dev/sda is not marked Active.
Fatal: Trying to map files from unnamed device 0x0011 (NFS/RAID mirror down ?)


Remember, I'm doing all of this from the Ubuntu 9.04 64-bit Live CD terminal.
Thanks amigos!

---

### Post by dmanno on 2009-06-05
Anyone out there that can offer some assistance? 

I've spent countless hours trying to get my Linux installation working over the past week. Long story short, I am unable to install Grub, which is why I am using Lilo. Now I just need to finalize the dual-booting by fixing Lilo and then hopefully using EasyBCD. I'm just not sure how to make it all work!

---

### Post by dmanno on 2009-06-05
I FINALLY fixed it! I found this link that lead me to the solution:

[http://forums.remote-exploit.org/bt3beta-software-related-issues/13616-cant-reinstall-lilo-2.html](http://forums.remote-exploit.org/bt3beta-software-related-issues/13616-cant-reinstall-lilo-2.html)

In case anyone else has this problem and needs to reinstall Lilo from a Linux Live CD, here's what you do to get Lilo to run in the terminal of a Live CD (I dual boot with Vista. My Ubuntu root is on partition /dev/sda4):

```
sudo mkdir /mnt/sda4          # makes a new directory where you mount your Linux partition
sudo mount /dev/sda4 /mnt/sda4          # mounts your LInux partition to the directory
sudo mount -o bind /dev /mnt/sda4/dev          # points the Live CD's /dev directory to your partition's /dev
sudo chroot /mnt/sda4 /bin/bash          # so you work from your partition's root and loads bash
sudo lilo          # re-configures Lilo
```

I'm a Linux n00b, so if my explanations of each command are not quite right, I apologize! Wow, it feels so good to finally be done getting Vista and Linux to dual boot. Only took me 4 days... :( And it's all because my computer did not like it when I installed from the regular CD using GRUB. I had to install from the alternate CD, and when GRUB failed it gave me the option to install Lilo instead. I wish the regular CD gave you that option to save people like me headaches.

Now I'm off to play in Ubuntu and learn new stuffs.

---


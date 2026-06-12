---
title: "New HDD, multiple bootloaders"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by dishayu on 2008-12-02
Hi all,

i previously had a single 320GB Harddisk with a dual boot ubuntu 8.04 and windows XP...

I recently did the following : 
1. added a new 500GB Harddisk
2. did a clean install of ubuntu 8.10 on it (with the bootloader in the new harddisk)...
3. deleted all the ext3 partitions on my older HDD and merged the free space with the logical ntfs partitions while installing 8.10

NOW, when i booted, it gave me GRUB error 17 (booting from my older HDD which STILL had the bootloader which was installed with 8.04)
so, i changed the boot priority to boot from the newer HDD first and the bootloader worked just fine (giving options to boot from 8.10 or windows)...

Now, to the main problem : i want to move around with my 320GB OLD hdd, so i need to remove grub and have my windows xp bootloader back on it WITHOUT messing with the GRUB on my new drive... what do i do?

---

### Post by cariboo on 2008-12-02
To restore your mbr on your 320Gb disk, boot from your Windows install cd and go into the recovery console and run fixmbr and fixboot. I may not have the commands exactly right, but if you type help at the C: prompt it will print out a list of all the available commands.

Jim

---

### Post by caljohnsmith on 2008-12-02
You can install a Windows MBR (Master Boot Record) to your Windows drive with the Windows Install CD as Jim above mentions, or if you don't have that, you can do the same thing from Ubuntu by doing:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/[COLOR="Blue"]sda[/COLOR]
```
Just make sure to get the correct drive, but sda will most likely be your internal drive.

---


---
title: "Can't boot Windows from Grub (dual boot)"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by kgilkerson on 2005-12-28
I recently installed ubuntu to dual boot with Win XP Pro. The installation went fine, but there is a problem with booting windows. When I select it and press enter in the grub, it shows five command lines and then just sits there, not doing anything. I partitioned as follows: 
1.Windows 7.0Gb NTFS
2.Ubuntu 3.0Gb Ext3 journaling
3.Swap space

The messages that come up after I press enter to load windows are:

Booting ‘Windows NT/2000/XP (loader)’

root  (hd0,0)
        filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

Then it just leaves that on the screen and sits there. Ubuntu boots just fine from the grub. I searched the forums and tried the rootnoverify command, but it still hangs. I don’t know anything about the grub, mount sites, or linux commands. I am trying linux for the first time.

---

### Post by joshuapurcell on 2005-12-28
Did you install Linux after installing Windows? You probably know this already, but Windows likes to think it's the only OS installed (so it needs to be installed first). It's possible to install it after Linux but it is more of a pain.

Also, did you need to use a partition resizing tool in order to make enough space for the ext3 and swap partitions on your hard drive? If that is the case, then did you check to make sure you could still boot into Windows after resizing the NTFS partition? It's possible that resizing the partition could have caused the problem instead of the installation of grub (or Linux).

You may also boot the system and press escape when you get the grub menu, then look at the selections in the grub menu and make sure it looks ok at that point. If you think something doesn't look right (or if there's something you could try just to see what happens), then press **e** while highlighting the appropriate line for booting in Windows and you can edit the line. One line I would check out is the second line in the Windows portion of the grub menu (related to the filesystem)... it looks to me like either grub isn't selecting the correct place on your hard drive for the NTFS partition or the NTFS partition is corrupted possibly due to resizing.

---

### Post by kgilkerson on 2005-12-28
I installed linux first. I partitioned the drive using only ubuntu installer. I didn't check to see if I could still boot to windows. I'll check that. Thanks alot. Anyone else have any more ideas?

---

### Post by kgilkerson on 2005-12-28
Never mind. I got it to work. What I did was reformat the entire drive (not a big deal for me to lose data), then reinstalled windows, but I partitioned the drive with the windows partitioner. Then installed Ubuntu in the second partition. I worked, but I don't know why that would make a difference.

---

### Post by joshuapurcell on 2005-12-28
[QUOTE=kgilkerson]I installed linux first. I partitioned the drive using only ubuntu installer. I didn't check to see if I could still boot to windows. I'll check that. Thanks alot. Anyone else have any more ideas?[/QUOTE]
It's recommended that you install Windows first due to these problems. I've actually dealt with this same problem recently when I wanted to get Windows up and running on a system that only had Linux installed at the time. I also wanted to continue using GRUB as the bootloader and not have to reinstall my Linux installation. I was finally able to do this, but I think the only reason it worked was because I had two hard drives. I switched which hard drive the computer would use to boot from in the BIOS to the one that I would install Windows on (leaving the Linux hard drive intact), and then once the Windows install was complete I switched the boot hard drive back to the Linux one in BIOS.

For some reason I ended up having to reinstall GRUB anyway since it would not start correctly, so I used the Ubuntu install CD, booted using the 'linux expert' installation option, and only selected the options given that were needed to reinstall GRUB. GRUB then automatically detected both the Windows and Linux installations, and when I restarted both were able to boot up as needed.

If you do try something like this, I would recommend writing down all information that you find in the GRUB menu before reinstalling GRUB. As you can see, this is why it is recommended to install Windows on your computer before installing Linux.

---


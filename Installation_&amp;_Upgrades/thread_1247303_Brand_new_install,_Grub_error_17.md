---
title: "Brand new install, Grub error 17"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by billdotson on 2009-08-22
I unplugged my internal drive and my flash drive leaving only my external USB drive plugged in. I can boot from it (I have done so numerous times) but it will absolutely not work at all now. First off, I had 3 primary partitions and an extended one. I put Ubuntu in the first logical partition (/dev/sdb5) and installed grub to hd1 (not hd0 the Windows XP drive). Booted from external drive and got Grub error 5 (had partition 3 set as unformatted)

Wiped partition table, created new msdos partition table. Reinstalled in the same manner except with internal drive unplugged. Same problem. (had partition 3 set as unformatted)

Installed PC-BSD 7.2 on third partition and tried to boot it with the PC-BSD bootloader. It gave me four options: Linux, Linux, BSD and drive 1. The two Linux ones are just data partitions. If I got anything but the drive 1 it would just give me a system beep (I thought having a partition unrecognizable by grub was causing error 5 at first).

Wiped partition 3, formatted to ext3 and installed Ubuntu with only the flash drive and external drive in. Installed GRUB to external drive (hd0) in this case. Rebooted and got grub error 21. 

Took the flash drive out and reinstalled. Get GRUB error 17 every time now.

This is absolutely ridiculous. I have never had such issues with GRUB before. I ran fsck on the third partition and no errors (which I didn't expect because this is a day old partition table).

Tried doing:

> 
sudo grub
grub (hd0,2)
setup (hd0)
quit 

from a livecd and that didn't change anything. 

Super grub disk won't recognize the partition at all (booting from flash drive).

sudo update-grub from the livecd says no grub directory can be found (mounted or unmounted).

Typing sudo grub-install '(hd0)' in the livecd returns:

```

Could not find device for /boot: Not found or not a block device.

```

Typing sudo grub-install hd0 in the livecd returns:

```

Could not find device for /boot: Not found or not a block device.

```

Typing sudo grub-install /dev/sda in the livecd returns:

```

Could not find device for /boot: Not found or not a block device.

```

sudo fdisk -l returns:

[http://paste.ubuntu.com/257777/]("http://paste.ubuntu.com/257777/")

boot_info_script.sh returns:

[http://paste.ubuntu.com/257779/]("http://paste.ubuntu.com/257779/")

This is absolutely infuriating, why can't I do anything with my external hard drive, especially when I was booting by itself with the same Ubuntu a week ago? Now I can't boot PCBSD, Ubuntu or anything. I would be a little more understanding if I were trying something more advanced like a dual boot or having GRUB just on the external and booting that way, but with the only drive in being this one with grub this is not acceptable. Ubuntu 9.04 is a big disappointment. Not only has X continued to crash multiple times for me livecd and regular install I can't even boot into it now. 

I have had this hard drive for 3-4ish years so it is past the point of DOA or a faulty drive but I wouldn't think it would be time for it to fail since it has been working fine (no noises or anything).

What is going on?! ARGH!

---

### Post by louieb on 2009-08-22
Are you sure your BIOS recognizes hard drive space more than 137GB   from the start of the hard drive?  Guess your not even seeing the Grub menu?  or I believe you would have gotten a GRUB error 18. 
> 
=================== sda3: Location of files loaded by Grub: ===================


 195.9GB: boot/grub/menu.lst
 195.8GB: boot/grub/stage2
 195.8GB: boot/initrd.img-2.6.28-11-generic
 195.8GB: boot/vmlinuz-2.6.28-11-generic
 195.8GB: initrd.img
 195.8GB: vmlinuz



BTW: Why did you start this thread looks the same problem as your other. [http://ubuntuforums.org/showthread.php?t=1244001](http://ubuntuforums.org/showthread.php?t=1244001)
Its just going to confused you and the members who are trying to help.

---

### Post by presence1960 on 2009-08-22
> **billdotson said:**
> [COLOR="Red"]I unplugged my internal drive and my flash drive leaving only my external USB drive plugged in[/COLOR]. I can boot from it (I have done so numerous times) but it will absolutely not work at all now. First off, I had 3 primary partitions and an extended one. [COLOR="Red"]I put Ubuntu in the first logical partition (/dev/sdb5) and installed grub to hd1 (not hd0 the Windows XP drive)[/COLOR]. Booted from external drive and got Grub error 5 (had partition 3 set as unformatted)


If you had everything unplugged except your external drive, then that drive is (hd0) as it is the only hard disk at the time you installed your OS and GRUB. I think this is where you went wrong Bill. There is no (hd1) until you add another hard disk to the equation. When you plug in your internal drive that becomes (hd0). But when you installed you only had external so that is (hd0) at that moment in time. To see if this is correct or not boot the ubuntu live CD with only the external disk and run > sudo fdisk -l from terminal and see what is reported. if it says sda for the external then it is (hd0) not (hd1)

Edit: I just saw your fdisk output with only the external plugged in and it in fact does say sda for that external disk. So you should have installed GRUB to (hd0) at that point in time. Then when you plugged in the internal drive regardless of the switch in designation from sda to sdb GRUB already would have been on MBR so the drive designation is irrelevant. You have to consider that the installer and any CLI you do only knows about hardware connected at the time of install or at time of CLI. It has no way of knowing that you unplugged the Windows drive with the intention of plugging it in again. All it saw was a single hard disk and of course that disk is designated sda and (hd0) at that point in time.

---

### Post by billdotson on 2009-08-22
If desired, a forum administrator can delete my older post or merge that post and this one. The other thread was long-winded and drawn-out and would be of little help to someone looking for a concise answer. I am frustrated and felt like the issue was going to be pushed back into the older pages only to be forgotten.

Presence, thanks for your help thus far.

I don't know if that is a typing error or I actually did install it to hd1 or not. I have a feeling I did not as I would have likely known that it was unplugged at the time. If I had done that I would have GRUB on my flash drive, not just super grub disk. I suppose the matter is irrelevant but if I did install GRUB to hd1 when it was the only drive present the next time I reinstalled I installed it to hd0. Upon booting, still without any drive except the external drive I get GRUB error 17. I really don't understand, if the drive is hd0, there are no other drives attached and it was the only one installed when I installed Ubuntu then it should work. There really isn't any reason why it shouldn't unless for some reason the installer only generates bad GRUB configuration files for my PC, which is highly doubtful and something I find to be hard to believe.

I don't know why it would be limited to 137GB. I have an Asus P5B deluxe wifi-ap edition motherboard ([http://www.bit-tech.net/hardware/2006/08/03/asus_p5b_deluxe_wifi_ap_edn/1]("http://www.bit-tech.net/hardware/2006/08/03/asus_p5b_deluxe_wifi_ap_edn/1")) with the latest BIOS (beta version 1238 2/11/2009 update; the last 9 BIOS updates have been betas, but I have no idea why you wouldn't actually finish support for one update before making 8 more unless you just don't care about the board anymore because it is 3 years old). The board came out when the Intel Core 2 Dus had been released a handful of months earlier so it should work. 

When partitioning the hard drive it shows ~279 GiB of hard drive space, which is what it is (advertised as 300GB, but the 1000MB "retail gigabyte" not the real 1024MB one). It if it didn't recognize past 137GB I shouldn't have been able to mount partitions and write to them (or read from them) successfully before, unless there is some strange thing about the BIOS only being able to see boot information x amount of gigabytes out, which, considering the year in which it was made and the parts it was made to be compatible for simply is not acceptable. The only other thing could be something going on the drive itself not allowing that but I have no clue if that is even possible. I have a couple cheap flash drives that aren't bootable, so perhaps it is, but to be bootable only "x" GB out seems silly.

I will try moving the boot folder to the first partition of the hard drive and see if it will work then. If it does work then I am going to be really ticked off.

---

### Post by billdotson on 2009-08-23
Ok, so I reinstalled Ubuntu on partition /deb/sda3 (sda being the external hard drive and sdb being the bootable flash drive that I have; the internal hard drive was not and is still not plugged in). I partitioned the flash drive like so: 1st partition ~60MB ext3, the remaining ~1.9-2 GB as fat32. /boot was installed to the ext3 partition. / (root) was installed to /dev/sda3, /home was installed to /dev/sda6 and swap was assigned to /dev/sda5. Grub was installed to hd0 (being the external hard drive), not the flash drive. 

I booted up and it stayed at the GRUB loading screen for about 5 seconds (I thought it was going to hang) but then it proceeded to boot Ubuntu. However, I was not shown a grub menu where I could choose between the normal boot, the recovery boot and the memtest +86. The computer simply booted straight to Ubuntu.

I am going to go to my BIOS and check settings. Perhaps I should change my USB drive configuration from [Auto] to [Hard drive] and see if that does anything in regard to booting. I will see if there is an LBA setting on the hard drive but really, if anything it should be the quality of the external hard drive and its age that would be the problem here, not the PC I spent basically all of my money at the time on.

---

### Post by louieb on 2009-08-23
> **billdotson said:**
> 
I booted up and it stayed at the GRUB loading screen for about 5 seconds (I thought it was going to hang) but then it proceeded to boot Ubuntu. However, I was not shown a grub menu where I could choose between the normal boot, the recovery boot and the memtest +86. The computer simply booted straight to Ubuntu.
Try pressing <ESC> during boot to get the menu. Sounds like  **hiddenmenu **is turned on. Or just comment out the line in /boot/grub/menu.lst  
> 
I don't know why it would be limited to 137GB.

Its a mystery to me to, I just have seen it work that way. Maybe a USB thing too. Seen plenty of threads about USB keyboard not working with GRUB but work fine after boot. Go figure. 
> The other thread was long-winded and drawn-out... .I am frustrated... 

Fair enough - I call it throwing stuff at the wall and see what sticks.

---

### Post by billdotson on 2009-08-24
The GRUB menu isn't showing because I have to press esc to show it. However, I am completely and totally baffled as to why GRUB will boot Ubuntu (regardless of Ubuntu's location as far as I have tested) if /boot is installed on my USB flash drive (where it has the kernel, menu.lst and all the other stuff). However, isn't running the Linux kernel from a flash drive and having the OS on an external hard drive going to be slow? The kernel loads into RAM upon boot doesn't it?

Here are my PC specifications:

Intel Core 2 Duo E6600.
USB 2.0 Maxtor 3200 279 GiB external hard drive
Seagate 7200.10 250 GB SATA 2 hard drive (the 250GB is the advertised)
nVidia 8800GT 512MB PCI-e 2.0 x16.
Soundblaster Audigy 4
Asus P5B Deluxe Wifi-AP edition with latest BIOS 1238 (beta BIOS but the last 7 or so BIOS releases have been BIOS; the board was purchased in 2006 I believe)

I am pretty sure that I ran Vista off of another partition on my internal drive for a good while, but I don't remember if it was more than 137GB out. Do you think that perhaps it could be a bug in the BIOS? What about something with that external hard drive? It may just end up being a weird USB thing, who knows. One thing I do know is that being limited to using the first 137GB on the hard drive for booting is going to be a major annoyance. I have two huge data partitions on that external drive and it is a major pain to have to gate them off inside of an extended partition. They are both at least 75GB so if I have to rearrange anything it is a huge pain. I am thinking it is probably time to get an external drive that can be eSATA and switch to USB if needed. It might be something related to my motherboard or something else as well but I have no way of knowing that right now.

---

### Post by louieb on 2009-08-24
> However, I am completely and totally baffled as to why GRUB will boot Ubuntu (regardless of Ubuntu's location as far as I have tested)

Ubuntu since v6.10 has a modified version of GRUB that can identify a partition by its UUID. Before that sometimes you had to modify files if a drive got removed or added. or you made some partition changes.  Now the main problem left is getting GRUB to load when hardware changes and most of the time thats not a problem.

---

### Post by billdotson on 2009-08-25
No, I know about UUIDs, I just don't understand why my system won't boot anything with a boot info file, folder or whatever that is farther out (say third partition 180GiB out). I put GRUB's /boot on my flash drive and ubuntu boots right up. If I put boot on /dev/sda3 (external drive) it spits error 17 or 21 at me. If I put /boot in a logical partition it spits erro5 at me.

---

### Post by billdotson on 2009-08-25
...bump?:confused:

I wonder if I need to put the flag "lba" on partitions that are farther out than 137GiB on my external hard drive when I am in gparted...?

For the internal hard drive LBA is on but since the external one is USB I don't think I was given that option.

---


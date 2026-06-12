---
title: "Upgraded, and now GRUB does not load"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Brownedwg89 on 2009-10-30
So I decided to upgrade my desktop to Karmic with a complete reinstall using ubuntu-9.10-server-amd64.

It seemed to install normally. When I started up after installing it said "GRUB loading." and stays there.

I tried reinstalling GRUB using the rescue option on the cd and tried reinstalling ubuntu again. Neither fixed my problem, so now I'm stuck.

---

### Post by axel_2078 on 2009-10-30
I have a similar problem. My grub menu loads and I can choose an option, but as soon as I do, it fails with an error message.

---

### Post by Rumpty on 2009-10-30
I had a problem which might be relevant to yours, axel-2078. My re-installation involved using the partitioner, and in that process the UUID of the drive was changed. Therefore grub "could not find the file", or words to that effect.

Had to get the new UUID and manually put it into menu.lst. Don't ask why I'm using the old grub! At this stage I can edit it - haven't really learnt enough about grub2 yet.

---

### Post by maxideci on 2009-10-30
I'm also facing same problem, the funny thing is, I have already upgraded my to Grub2, before going for upgrade from 9.04 to 9.10. But now when i try to boot, the box pops up error as "grub-machine_fini" not found and shows up grub rescue menu. what do i do there ??? 

I booted using live usb stick, I have attached the output of boot_info_script (I found somewhere in this forum).

steps i followed :

root@ubuntu:~# mount /dev/sda9 /mnt   -- This is my Linux root partition
root@ubuntu:~# mount --bind /dev /mnt/dev
root@ubuntu:~# mount --bind /proc /mnt/proc
root@ubuntu:~# chroot /mnt
root@ubuntu:/# grub-install /dev/sda9
output : [I]grub-probe: error: Cannot find a GRUB drive for /dev/sda9.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.[/I]

my device map looks like this :
(hd0)   /dev/sda
(hd1)   /dev/sdb

then i tried 
root@ubuntu:/# grub-install /dev/sda
output : [I]grub-probe: error: Cannot find a GRUB drive for /dev/sda9.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.[/I]

I have googled about this problem, but nothing works out in my way. Finally I have decided to fresh install, but when i reach the section about disk partition, 9.10 does not show any partition table at all. Does that mean my system's partition table is corrupt ??? i dont get how ??
I have now fixed my mbr using windows dvd, atleast now i can boot into windows, but i dont feel good.

can anyone help ??

i tried to probe for boot devie..
root@ubuntu:/# grub-probe -t device /boot/
output */dev/sda9*

I tried running Gparted, and see that, the partition table is gone, it shows complete disk as unallocated space.

the upgrade from 9.04 to 9.10 didn't finish correctly, as it threw up some error with +memtest...

I guess that's the reason why partition table is screwed up.

Is there anyway to recover partiton table ??

Thanks.

---

### Post by Brownedwg89 on 2009-10-30
Any advice?

---

### Post by drs305 on 2009-10-30
@ maxideci,

You might try testdisk. It does an excellent job of restoring partition tables. Since you have done some attempted installs I don't know what it's going to show, but that is where I would start.
Here are a couple of good links:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/~herman546/p21.html")

@ Brownedwg89

Upgrades normally retain Grub, but you mention rescue mode. Are you using Grub legacy or Grub 2? If you are using Grub 2, I would direct you to the community doc (GRUB 2). 

If you are getting any kind of menu, you can review the instructions for booting from the menu or from the grub or grub-rescue prompt. If you get no menu at all there are instructions for reinstalling Grub 2 from the LiveCD.
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by Brownedwg89 on 2009-10-30
> **drs305 said:**
> @ Brownedwg89

Upgrades normally retain Grub, but you mention rescue mode. Are you using Grub legacy or Grub 2? If you are using Grub 2, I would direct you to the community doc (GRUB 2). 

If you are getting any kind of menu, you can review the instructions for booting from the menu or from the grub or grub-rescue prompt. If you get no menu at all there are instructions for reinstalling Grub 2 from the LiveCD.
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

I decided to do a clean install, so I'm guessing it replaced my GRUB with GRUB 2. I am not getting any GRUB menu, just "GRUB loading." I installed using the server version, so right now I'm using an old LiveCD (7.10 :P) to download the 9.10 LiveCD, so that I can use that to try to reinstall GRUB 2...

---

### Post by wkulecz on 2009-10-30
I tried a fresh install to what IMHO should have been /dev/hda, but which the installer identified as sdb, there are two SATA drives in the system which hopefully were untouched, but on the initial reboot it fails with:

Grub loading, please wait ....
Error 15

This is 64-bit desktop install.

I think the root of all this is when they started mucking with device IDs and trying to make every hard drive be some /dev/sd  IDE, SATA, and SCSI are different, trying to make them all the same seems stupid to me!  This UUID stuff IMHO is an abomination.  I'm all for common code to support the various drive types, but denying the physical differences in the device interfaces, I don't see an upside to this -- enlighten me, at best it "just works" and I don't notice it, but it didn't! 

I'm in the process of investigating what is fubar.

I don't think you are stuck, boot the live CD and poke around, that is what I'm doing now.

--wally.

Grub2, WTF? All pain no gain so far!
I don't think I have time to mess around with this.  If they don't straighten out this mess for 10.4LTS, I'll be leaving Ubuntu.

---

### Post by overkill1 on 2009-10-31
I agree I shall be leaving too it makes you wonder what all the hype was and the wait until release date for 9.10. 

So much for their beta testers, ppl who dont know what their doing should leave grub well alone.

---

### Post by efflandt on 2009-10-31
Are you people using grub or grub2.  I did an upgrade install on 2 computers (64-bit desktop and 32-bit laptop), and they both still use grub (v0.97-20ubuntu59).

So maybe something tripped up and grub2 is looking for grub.cfg, while Ubuntu 9.10 configured menu.lst (or vice versa).

I am certainly no grub expert, but I wonder if there is an issue about which grub is actually being used.

---


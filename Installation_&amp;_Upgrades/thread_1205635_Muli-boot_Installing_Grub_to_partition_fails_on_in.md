---
title: "Muli-boot: Installing Grub to partition fails on installation of Jaunty"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by youoneah on 2009-07-06
**Synopsis**
I have unexpectedly run into great, unsolvable problems installing Jaunty on a known Ubuntu-compatible system. This actually is due not to a hardware issue, but to the multi-booting arrangement. Installing Grub to the partition boot sector (not MBR) apparently failed during installation. Multiple post-installation attempts to install Grub to the partition failed. Further attempts using fresh Jaunty installation, followed by manual attempts to install Grub to the partition, all failed. A subsequent fresh installation of Jaunty, in which Grub should write the MBR, hung without overwriting the MBR.

**System**
Dell M1330
Fresh install of Jaunty (amd64) on an extended partition

**Problem description**
The SATA drive partitioning scheme is mildly complex, since I am multi-booting Vista, Debian Lenny (amd64), and Ubuntu, as well as reserving partitions for trying out distros. My intention is to have Debian manage Grub in the MBR, and to chainload not only Vista but also the bootloader (usually Grub) from the respective operating systems. So far, Vista and Debian are installed. Here are the partitions relevant to the Ubuntu install:

/dev/sda1 NTFS
/dev/sda2 /boot (managed by Debian Lenny, which lives on about four partitions)
/dev/sda9 swap
/dev/sda10 Ubuntu root
/dev/sda11 Ubuntu home

The Grub entry in Debian's /boot/grub/menu.lst for chainloading the Grub (theoretically) installed Jaunty's partition is something like:```
title           Jaunty
root            (hd0,9)
chainloader     +1
```

The difficulty I've run into is successfully installing Grub to the Ubuntu partition, /dev/sda10, which for Grub is (hd0,9). I've double-checked that both Lenny and Jaunty are using Grub Legacy (version 0.97). I've tried many things, so here is a rough chronological account of the steps taken:

[LIST]
[*]**Install jaunty.** During installation, select the sda10 and sda11 partitions, choose mount points and format XFS; select "Advanced" and specify to install Grub to /dev/sda10. The installation was successful, but to my surprise, Grub appeared not to be installed. Chainloading from the Debian-managed Grub in the MBR failed. Curiously, there is no initrd that I could see in the Jaunty installation. Trying to load the vmlinuz directly by manually editing the Grub entry failed. Unfortunately, I didn't write down those error messages. The proof that Jaunty did not install Grub to the partition is that, although the grub package was installed, there was no grub directory in Jaunty's /boot.
[*]**Install Grub manually.** References 2 and 3 (see below) describe ways to mount the freshly installed Jaunty (also mounting proc and dev) and use chroot to run Grub from within the system and install to (hd0,9). I tried this both from Debian and from the Jaunty live CD. Grub gave error messages; running "find /boot/grub/stage1" returned only the entry in /dev/sda2 (Debian). This is because there was no /boot/grub directory in Jaunty, despite having specified it to install Grub to /dev/sda10 during the Jaunty installation.
[*]**Try, fail, rinse-and-repeat.** In my efforts to install Grub I figured I'd broken something. Or, it would be simpler to try something different during installation. This happened more than once, so I ended up installing Jaunty about four times. Well... installation doesn't take that long, after all. ;)
[*]**Kickstart Grub.** I ended up creating a /boot/grub directory and copying all files from /usr/lib64/grub/x86_64-pc/ from hand after a fresh Jaunty install. In the chroot, this allowed Grub to find /boot/grub/stage1, and it reported successfully installing to (hd0,9), meaning /dev/sda10; however, it did report failing to install 1_5, although it reports "this is not fatal". Unfortunately, the attempt to chainload from the MBR Grub (the one that reads from /dev/sda2 where Debian's /boot resides) fails with Error 13: "Invalid or unsupported executable format".
[*]**Generate menu.lst** Since the previous step failed, I though maybe the problem was that there was still no menu.lst. So I ran "sudo update-grub", but this failed, saying that it couldn't resolve the UUID for either /dev/sda9 or /dev/sda10. I edited /etc/fstab, replacing the UUID entries with the appropriate /dev/sda9 and /dev/sda10. Chainloading still failed with Error 13.
[*]**Install Jaunty and write its Grub to MBR.** At this point, I figured it would be simpler to just let Jaunty write Grub to the MBR during a fresh install. Then at least it should have a standard installation of /boot/grub, complete with a Jaunty-configured menu.lst. Afterward, I could boot Jaunty directly, install Grub to the sda9 partition boot sector, and finally rewrite the Debian Grub to the MBR. During installation, I specified formatting the partitions, gave in all information, selected to install to (hd0), and the installation proceeded. Unexpectedly, after the progress bar reached the end, the installation hung, showing only the Jaunty wallpaper, instead of the live CD desktop as usual. I switched to the shell with Ctl-Alt-F1, and it had the prompt with no activity, as though the installation were complete. There was no hard-drive or CD activity, so after waiting a while, I issued a "sudo shutdown -r now" from the shell. Upon rebooting, I got the Debian Grub menu as usual, so Jaunty did not successfully write Grub to the MBR. I don't know why this behavior after several successful installations; the only difference may have been that the switch controlling wifi, bluetooth, etc. was on.
[*]**Check disk.** Ran the integrity check of the live disk, it passed.
[*]**Installation failed again.** I tried installing again, it failed the same way. At this point, I hadn't thought of the wifi switch.
[/LIST]

This brings me up to the present. I will of course try the install again with the wifi switch off.

**Resources**
I've used several resources to keep myself on the straight-and-narrow.
1. [http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)
2. [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
3. [ How to install Grub from a live Ubuntu cd.]("http://ubuntuforums.org/showthread.php?t=224351as:")
4. many Google results

**The actual questions**
[LIST=1]
[*]The most urgent issue is to figure out why Ubuntu isn't installing correctly anymore. If it turns out not to be caused by the wifi switch, how to I diagnose the installation hanging where it does?
[*]What could be the reason the installation of Grub to the partition doesn't work? I expected this to work without any manual mucking about. Did I miss something? I haven't been able to try installing Ubuntu to the MBR, then writing it to the partition and replacing the MBR with Debian's Grub, as described above. If that works, fine. I would submit a bug report if the installation to partition turns out not to work as the designers expected, but I haven't determined whether I've discovered a bug.
[/LIST]

**Outlook**
Later on, I plan to make things even more complex, because I want to add FreeBSD to the mix... :-\"

---

### Post by youoneah on 2009-07-07
polite bump.

Last night I tried installing with the wifi/bluetooth switch off, and selecting Grub to install to the MBR. It finished installing and arrived at the live desktop. When I selected Restart, it didn't shut down—the screen went blank but the machine didn't halt, and I couldn't get to a console. I had to reboot using the power button. The Debian-managed Grub was *still* in the MBR!

For now, I think this has to turn into a "why doesn't Ubuntu install" thread. Any ideas? I'm at a loss here, given the known compatibility of the hardware?

Thanks

---

### Post by dstew on 2009-07-07
I just scanned your post, and I see something that might help. Grub counts partitions differently than linux. If /dev/sda3 is your extended partition, grub will number it (hd0,2) as you might expect. If you only have three primary partitions, with /dev/sda3 being your extended partition, then the first logical paritition in Linux will be /dev/sda4. However, the first logical partition in grub will be numbered (hd0,4) instead of (hd0,3). Grub counts logical partitions starting at (hd0,4). So if you have logical partitions /dev/sda4 to /dev/sda11, grub will number these (hd0,4) to (hd0,11), and your Ubuntu root partition will be (hd0,10), and not (hd0,9) as you used in the command. So, do you only have three primary partitions? An fdisk -l output would be helpful. See the [grub manual, section 2 "Naming Convention"]("http://www.gnu.org/software/grub/manual/grub.html#Naming-convention"). (I think the manual says "extended partition" but from other sources it seems that the first logical paritition is intended.)

---

### Post by youoneah on 2009-07-09
I'm fairly certain that I have four primaries, the fourth containing the logical partitions.  I recall that, after I had manually moved the Grub files to Jaunty's /boot/grub, the output in Grub shell of "find /boot/grub/stage1" did return (hd0,9). In any case, this is certainly worth checking out, I will do so this evening and provide a full "fdisk -l" output.

I will feel sheepish if this turns out to be my problem with trying to write Grub by hand, but I'm certain that it's not the problem with installing Jaunty—especially when specifying to write Grub to the MBR. Suppose I'll have to read up on troubleshooting installs.

Thanks very much for your reply!

---

### Post by youoneah on 2009-07-09
Here's the current setup:
```
# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb14cf090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10445    83891200    7  HPFS/NTFS
/dev/sda2           10446       10464      152617+  83  Linux
/dev/sda3           10465       10525      489982+  83  Linux
/dev/sda4           10587       30401   159163987+   5  Extended
/dev/sda5           10587       12422    14747638+  83  Linux
/dev/sda6           12423       12811     3124611   83  Linux
/dev/sda7           12812       12849      305203+  83  Linux
/dev/sda8           12850       14077     9863878+  83  Linux
/dev/sda9           14078       14320     1951866   82  Linux swap / Solaris
/dev/sda10          14321       16931    20972826   83  Linux
/dev/sda11          16932       17584     5245191   83  Linux
/dev/sda12          17585       20195    20972826   83  Linux
/dev/sda13          20196       20848     5245191   83  Linux
/dev/sda14          20849       30401    76734441    7  HPFS/NTFS

```

I used the installer to format the Jaunty partitions and use XFS. See the screenshot of GParted for a few extra details.

All this for reference at the moment. I fixed a few things on my Debian install tonight instead of trying to reinstall Jaunty, so I'll be back with more gory details in the coming days...


Edit:
Thought of a way to test how grub interprets partitions:```
grub> cat (hd0,9)/etc/fstab
cat (hd0,9)/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=299f83d7-618b-4a23-9d7a-1945f1a36a99 /               xfs     relatime        0       1
# /home was on /dev/sda11 during installation
UUID=d1845579-9d65-4ca5-b9a8-3d0caba69238 /home           xfs     relatime        0       2
/dev/sda9       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Since it finds /etc/fstab there, it appears that Grub interprets /dev/sda10 as (hd0,9) after all. Wish it would've been that easy though, even with egg on my face. :)

---

### Post by youoneah on 2009-07-11
The fresh installation of Jaunty worked this time. The only thing I did differently is to format the partition using ext4 instead of XFS. That means I again specified to write the boot loader to (hd0). The installation worked flawlessly, the shutdown went smoothly, and I eagerly anticipated seeing Ubuntu's bootloader screen.

Still no go.

Upon rebooting, I again got Debian's bootloader screen, meaning Ubuntu's Grub did not overwrite the MBR. So forget all the fancy-shmancy multi-boot stuff above, let's limit ourselves to the facts:
[LIST=1]
[*]The partitions are as listed in the previous post.
[*]I did a fresh install of Jaunty amd64 on this Dell M1330, mounting / on /dev/sda10 and /home on /dev/sda11.
[*]I selected to write the bootloader to (hd0), which normally would mean overwriting the MBR.
[/LIST]
I booted using the LiveCD and did [the following:]("http://ubuntuforums.org/showthread.php?t=224351")
```
[COLOR="DarkGreen"]ubuntu@ubuntu:/mnt$ sudo mkdir /mnt/root
ubuntu@ubuntu:/mnt$ sudo mount /dev/sda10 /mnt/root/
ubuntu@ubuntu:/mnt$ sudo mount -t proc none /mnt/root/proc/
ubuntu@ubuntu:/mnt$ sudo mount -o bind /dev /mnt/root/dev/
ubuntu@ubuntu:/mnt$ sudo chroot /mnt/root /bin/bash [/COLOR]
root@ubuntu:/# sudo grub
**sudo: unable to resolve host ubuntu**
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,2)
grub> quit
quit
root@ubuntu:/# pwd
/
root@ubuntu:/# cd boot/
[COLOR="Red"]root@ubuntu:/boot# ls
abi-2.6.28-11-generic	  memtest86+.bin		vmcoreinfo-2.6.28-11-generic
config-2.6.28-11-generic  System.map-2.6.28-11-generic	vmlinuz-2.6.28-11-generic[/COLOR]
root@ubuntu:/boot# sudo grub-install /dev/sda
sudo: unable to resolve host ubuntu
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/boot# grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> cat (hd0,9)/etc/fstab
cat (hd0,9)/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=ac51e0db-15e3-42e1-899a-34371f02cb55 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda11 during installation
UUID=b40fff5e-ab34-47b5-8bed-cc17cea03218 /home           ext4    relatime        0       2
/dev/sda9       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
grub> quit
quit
root@ubuntu:/boot# ls -lh
total 5.9M
-rw-r--r-- 1 root root 514K 2009-04-17 05:34 abi-2.6.28-11-generic
-rw-r--r-- 1 root root  89K 2009-04-17 05:34 config-2.6.28-11-generic
drwxr-xr-x 2 root root 4.0K 2009-07-11 19:17 grub
-rw-r--r-- 1 root root 126K 2009-03-27 21:12 memtest86+.bin
-rw-r--r-- 1 root root 1.8M 2009-04-17 05:34 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root 1.2K 2009-04-17 05:39 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 3.4M 2009-04-17 05:34 vmlinuz-2.6.28-11-generic
root@ubuntu:/boot# cd grub
root@ubuntu:/boot/grub# ls -l
total 4
-rw-r--r-- 1 root root 30 2009-07-11 19:17 device.map
root@ubuntu:/boot/grub# cat device.map 
(fd0)	/dev/fd0
(hd0)	/dev/sda
```

Unless I am mistaken, Grub is for whatever reason not correctly installing during a fresh install of Jaunty. After I chroot into the installation, it is clear that there is no /boot/grub directory---meaning no menu.lst is generated.

Also, is it now normal in Ubuntu that there is no initrd in /boot? I find the following link in the root directory:```
lrwxrwxrwx   1 root root    33 2009-07-12 03:13 initrd.img -> boot/initrd.img-2.6.28-11-generic
```
But as you see above, there is no such file in /boot, although vmlinuz is there.

This weirdness is clearly an installation issue, but Google isn't bringing me any closer to the reason why. I did find [something that was caused by a hardware conflict,]("http://ubuntuforums.org/archive/index.php/t-278786.html") but that obviously does not apply in my case.

**Why would Grub fail to install**---even failing to create /boot/grub and copy its files there? And why would Jaunty decide to not inform me about it during the installation process?

---

### Post by dstew on 2009-07-11
I was thinking more about your problems, and was about to post back to try ext3 or ext4 instead of XFS, but I see you did try ext4, with some improvement.

Still, ext4 might be causing a problem with the installer program on the Live CD. It seems that something in the installer is not working. If you are willing, try re-installing with an **ext3** format. The other guess is that the installer program has some flaw in it. Does the disk install OK on other hardware?

---

### Post by youoneah on 2009-07-11
Thanks dstew, I see you were suggesting this at the same time I was moving that direction.

Actually, I did already try a new install using ext3, for no other reason than Debian Lenny doesn't support ext4 yet without some effort, and these two are going to be living together. That install failed too.

I actually was blind to the failure of all of these installs; I was so focused on the bootloader that I didn't really notice the real problem was indeed in the installer. Ubiquity was crashing during the install. The CD checks out, so I think it's a basic conflict. I was ready to switch to the 32-bit version, but Googling indicated that the LiveCD can with some systems be less reliable, wheras the Alternate CD tends to have less problems, so I downloaded the Alternate CD amd64. I [installed it using Debian]("https://help.ubuntu.com/community/Installation/FromLinux") (a first for me, neat w/o the a CD), and everything is now working as desired. I did learn even more about Grub during this process, but the main thing I have learned over the past several days is not to take the Ubuntu installer for granted.

Thanks all for reading my docudrama. :popcorn:

---

### Post by dstew on 2009-07-12
Glad you pressed through to victory. Best wishes.

---

### Post by perspectoff on 2010-01-15
.

---


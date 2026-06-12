---
title: "Multi-Boot Partition Problems"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by StKunze on 2009-09-26
I've been using Ubuntu on my laptop for about a year or so now. Not a complete newbie but not a technical wizard either! More than capable of googling answers and I've done that in a search for answers here, tried a variety of things but got nowhere.

My disk was triple booted, partitions were as follows:
1. Primary Partition - NTFS/Windows
2. Primary Partition - ZFS/Solaris (Gparted reported this partition as 'unknown' format)
3. Primary Partition - Linux-Swap
4. Extended Partition containing
4a. Secondary Partition - /(Root)
4b. Secondary Partition - /Home
4c. Secondary Partition - FAT32-shared

As I was running out of space I decided to remove Solaris, so booting from a USB stick containing Ubuntu Jaunty, I used Gparted to delete the Solaris partition, move and resize the other partitions so that it looked like this (all apparently successful operations):

1. Primary Partition - NTFS/Windows
2. Primary Partition - Linux-Swap
3. Primary Partition - Linux /Home
4. Extended Partition containing
4a. Secondary Partition - Linux /(Root)
4b. Secondary Partition - FAT32-shared

The Root, Home and shared partitions automount fine, and windows still boots when selected from grub (I manually removed the solaris entry from grub). But the linux-swap does not appear to be on (used as swap), and I can't mount my windows disk at all.

[COLOR="Blue"]sudo fdisk -l[/COLOR] gives me this:
```
   Device Boot  Start      End      Blocks   Id  System
/dev/sda1   *       1     3823    30708216    7  HPFS/NTFS
/dev/sda2        3824     4217     3164805   82  Linux swap / Solaris
/dev/sda3        4218     5493    10249470   83  Linux
/dev/sda4        5494    12137    53367930    5  Extended
/dev/sda5        5494     7925    19535008+  83  Linux
/dev/sda6        7926    12137    33832858+   b  W95 FAT32
```

So, something appears to have gone wrong with no apparent error messages. 

Can somebody help me with these questions please?

1. why does the filesystem still report the swap partition as Solaris, when it's been reformated? And does it make any difference? (note the Solaris partition started at the same position but was much larger).

2. why does Gparted show me the linux-swap partition, but always give me the option to "swapon" (indicating that it's not currently being used as swap). [COLOR="Blue"]FSTAB[/COLOR] shows:
```
# Entry for /dev/sda9 :
UUID=6798e6b7-b7c1-4994-bc1c-ffb9783cb86a none swap sw 0 0
```
Which is another odd thing as Gparted reports it as sda2, but fstab shows it as sda9!

3. I cannot _not_ mount my windows partition either manually or automatically. I installed the NTFS configuration tool which added this line to [COLOR="Blue"]FSTAB[/COLOR]:
```
/dev/sda1 /windows ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```
which is all well and good, but it still doesn't mount. Which may be completely unrelated to the other problems but I just don't know.

(attachment screenprint from Gparted)

---

### Post by StKunze on 2009-09-26
Okay, reading [http://ubuntuforums.org/showthread.php?t=753815](http://ubuntuforums.org/showthread.php?t=753815)
I changed the swap partition line in [COLOR="Blue"]fstab[/COLOR] to:```
/dev/sda3   none   swap   sw   0   0
```(obviously having backed it up first).

On reboot, and checking through Gparted, it appears SWAP is being used now (well at least Gparted now only gives me the [COLOR="Blue"]swapoff[/COLOR] option).

However all the other issues remain (i.e. windows partition not mounting, and fdisk reporting the swap partition as swap/solaris.

---

### Post by awk on 2009-09-26
Maybe you could try another ntfs driver (ntfsprogs comes to mind) to replace ntfs-3g. If nothing works you can always mount the windows partition read-only:
```
*(sudo)* mount -t ntfs -o umask=000 /dev/sda1 /windows
```

---

### Post by oldfred on 2009-09-26
When in gparted you do not want anything mounted to allow editing of the partitions, but I believe you have to turn swap off on most liveCD as they will use the swap on the HD.
My swap shows solaris just like yours, it is the way it is shown.
When you edit/add/delete partitions you may end up renumbering them and possibly changing UUID and sdxy's. You also then have to edit grub's menu.lst and fstab to correct all the changes.

---

### Post by presence1960 on 2009-09-26
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by StKunze on 2009-10-27
This is one of these 'not really sure why' answers, but, the last remaining problem (that of the windows partition not automounting) appears to have been corrected by simply *manually* creating a mountpoint for it (/windows) and rebooting. I'm obviously embarrassed by the apparent obvious-ness of that, but in my defence, previously (before all my re-partitioning) it mounted fine (simply clicking on it in Nautilus) without the manual creation of a mountpoint </shrug>
Anyway, problem solved, and thanks for the advice.

---


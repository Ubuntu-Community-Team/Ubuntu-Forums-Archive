---
title: "Partitions and swap space"
date: 2008-06-20
forum: Hardware
---

### Post by Nemmasis on 2008-06-20
I recently reloaded my laptop with Vista and Xubuntu. I put them both in primary partitions but had to put the swap space on an extended partition (there is a 'service' partition for reloading Vista and I wanted to have a data partition for use by both OS's). I found my swap was been lost when I rebooted and figured it was because of the extended partition. I have copied my Xubuntu installation onto the extended partition but before I delete the original and resize the Extended partition I want to know how to boot into the copy. I am using EasyBCD to hand off to GRUB, which is on the Xubuntu partition. The results of fdisk are;

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         632     5073920   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         633        5731    40952520    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            5731        8162    19527480   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4            8162       19457    90727560    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            8162       10594    19535008+  83  Linux
/dev/sda6           10594       11232     5118088+  82  Linux swap / Solaris
/dev/sda7           11232       19457    66074368+  83  Linux


Xubuntu is sda3 and the copy is sda5. Any help would be appreciated, I would rather not reload Xubuntu if I don't have to.

---

### Post by logos34 on 2008-06-20
> **Nemmasis said:**
> I found my swap was been lost when I rebooted and figured it was because of the extended partition. I have copied my Xubuntu installation onto the extended partition but before I delete the original and resize the Extended partition I want to know how to boot into the copy. I am using EasyBCD to hand off to GRUB, which is on the Xubuntu partition. 
... Any help would be appreciated, I would rather not reload Xubuntu if I don't have to.

If the only problem you're having is that swap doesn't mount, then you should be able to fix that w/o reinstalling or transferring to another partition.  There's nothing wrong with having root on a primary and swap on a logical.  

What does Gparted show?  

If there's triangle with exclamation next to swap sda6, try to clear it by deleting it and making a new one in its place (type: 'linux-swap').  Note the new **UUID #** in 'show details' box underneath, then open fstab
[B]
gksudo gedit /etc/fstab[/B]

replace the old UUID with new one. Or just use the **/dev/sda6** format.

Then activate it with 

**sudo swapon -a **

or right-click on it in gparted>swapon

You might also consider fixing the partitions so they round to cylinder boundaries, using Testdisk

---

### Post by Odrodzona-Sarmacja on 2008-06-21
> **logos34 said:**
> 
[B]
gksudo gedit /etc/fstab[/B]

replace the old UUID with new one. Or just use the **/dev/sda6** format.

Then activate it with 

**sudo swapon -a **

Or with "sudo mount -a" and then "sudo swapon -s" to check if mount is working. :)

---

### Post by Nemmasis on 2008-06-22
I got rid of the copy of my xubuntu partition so now I have;

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63e16945

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         632     5073920   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         633        5731    40952520    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            5731        8162    19527480   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4            8162       19457    90727560    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            8162        8795     5080288+  82  Linux swap / Solaris
/dev/sda6            8795       19457    85647208+  83  Linux


Even though sda5 shows up as Linux swap, Gparted shows it as 'unknown'.This happens on a reboot or resume from hibernate (even though it goes through the motions hibernate seems the same as a reboot, taking me back to the Windows boot loader). I can't remount or swapon from the terminal, I can only reformat it and swapon in gparted. I actually noticed this problem because after losing the swap it would kick back into the OS from an attempt to hibernate.

fstab shows this;

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=fdb18c5b-9f42-4fdb-aa64-76376fe38dea / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda4 :
UUID=85ee2b19-9f5e-420a-91b2-da67744be279 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda2 /media/Vista ntfs-3g defaults,locale=en_CA.UTF-8 0 0

, with sda5 not even showing up.

I tried using Testdisk to clean things up but it started asking me to make decisions I wasn't comfortable with so I exited. When I restarted I had to run fsck to clean the discs up. I'll come back to this once I get the swap issue sorted.

I just tried a suspend and it appears to go down normally but won't come back and requires the power to be cycled. I'm not sure if these issues are related or not

---

### Post by Nemmasis on 2008-06-22
OK, I pasted this:

/dev/sda5   none   swap   sw   0   0

into fstab and it now works. I just need to get it mounting and reading my shared data partition and I'm laughing. Thanks to logos34 and Odrodzona-Sarmacja for their help.

---

### Post by logos34 on 2008-06-22
> **Nemmasis said:**
> Even though sda5 shows up as Linux swap, Gparted shows it as 'unknown'.This happens on a reboot or resume from hibernate (even though it goes through the motions hibernate seems the same as a reboot, taking me back to the Windows boot loader). I can't remount or swapon from the terminal, I can only reformat it and swapon in gparted. I actually noticed this problem because after losing the swap it would kick back into the OS from an attempt to hibernate.


I was having EXACTLY this problem back in Feisty, so I did like you and yanked the UUID from fstab and reverted to /dev/sd.. format (one reason for my dislike of uuids, which I've since changed my mind on).  Never did nail it down, but whatever it was didn't effect Gutsy, where I was able to use the UUID again.  

In your case, though, it may have something to do with the fact that partitions are not rounded to cylinders.  Maybe [this page ]("http://www.users.bigpond.net.au/hermanzone/p21.html")will make you feel more comfortable using testdisk.

As far as hibernation/suspend goes, do you have a 'resume=' option in the 'kernel' line in /boot/grub/menu.lst? If so, may need to change it

---


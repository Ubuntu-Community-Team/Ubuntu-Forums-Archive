---
title: "Install ubuntu but after restart no choice"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by shakewell2 on 2009-09-01
hey guys,

i just got done isntall ubuntu but after i removed the cd and i restarted the pc -- i went into the bios to make the HD the first boot device ..

now i cant see the menu to choose what OS to boot with.


how do i go about fixing that ?

---

### Post by raymondh on 2009-09-01
> **shakewell2 said:**
> hey guys,

i just got done isntall ubuntu but after i removed the cd and i restarted the pc -- i went into the bios to make the HD the first boot device ..

now i cant see the menu to choose what OS to boot with.


how do i go about fixing that ?

Wubi or straight up install?
Single boot or dual boot?
1 HD or multiple HD?
Where is GRUB installed (if multiple HD)?

Need more info please.  How did you install?  If you want, go boot into the live CD and in live session, access a terminal and type and copy/paste output of

```
sudo fdisk -l
```

small L not 1 nor I

---

### Post by ronparent on 2009-09-01
You probably only need to reset grub for a new boot order. Boot inot the live cd and open a terminal. In the terminal enter the following commands: 

**sudo grub**

and from the grub prompt enter the command:
[B]
find /boot/grub/stage1[/B]

using the location in the output from the above enter:

**root (hdx,y)** - x and y are the numbers in the above output
**setup (hdx)**

**quit** and restart

Everything should now present correctly on boot providing the boot disk is (hdx). Your work to install should now be complete. Enjoy.

---

### Post by shakewell2 on 2009-09-01
i installed it as a dual boot with xp - but a full installing, not within xp.

ill try these now and come back with results.

thanks

---

### Post by shakewell2 on 2009-09-02
it keep booting back into winxp .. not showing the boot order to go into ubuntu

---

### Post by stlsaint on 2009-09-02
please post sudo fdisk -l
Simply boot into the livecd...open a terminal and type
sudo fdisk -l
than post results here

---

### Post by shakewell2 on 2009-09-04
> **stlsaint said:**
> please post sudo fdisk -l
Simply boot into the livecd...open a terminal and type
sudo fdisk -l
than post results here


```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d166d16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       60801   385985722+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ea92ea8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38245   307202931    7  HPFS/NTFS
/dev/sdb2           38246      121601   669557070    f  W95 Ext'd (LBA)
/dev/sdb5           38246       95455   459539293+   7  HPFS/NTFS
/dev/sdb6           95456      120536   201463101   83  Linux
/dev/sdb7          120537      121601     8554581   82  Linux swap / Solaris

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd482d482

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdc2           12749       48641   288310522+   7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfbe9fbe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60800   488375968+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 



```

---

### Post by shredder12 on 2009-09-04
I believe you have 4 hard disks..
and linux is installed on the 2nd one i.e.sdb 
and your bios by default boots the 1st hard disk i.e. sda1 and its mbr doesn't contain grub..
so you will have to overwrite the mbr of first hard disk and install grub on it.
so jst follow this..
> **ronparent said:**
> You probably only need to reset grub for a new boot order. Boot inot the live cd and open a terminal. In the terminal enter the following commands: 

**sudo grub**

and from the grub prompt enter the command:
[B]
find /boot/grub/stage1[/B]

using the location in the output from the above enter:

**root (hdx,y)** - x and y are the numbers in the above output
**setup (hdx)**

**quit** and restart

Everything should now present correctly on boot providing the boot disk is (hdx). Your work to install should now be complete. Enjoy.

---

### Post by presence1960 on 2009-09-04
Let's be sure what you have with all those disks and lets see what is on MBR of each disk before you do anything.

Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---


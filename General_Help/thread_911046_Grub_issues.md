---
title: "Grub issues"
date: 2008-09-05
forum: General Help
---

### Post by freet on 2008-09-05
Hello there

Wanting to experiment a bit with this ubuntu release, i installed it on an empty partition, leaving my XP-partition (for the family) untouched. After the install only Ubuntu was in GRUB's menu.

My fdisk -l looks like this:

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           2       24321   195350400    f  W95 Uitgeb. (LBA)
/dev/sda5               2       16709   134206978+   7  HPFS/NTFS
/dev/sda6           16710       24196    60139296   83  Linux
/dev/sda7           24197       24321     1004031   82  Linux wisselgeheugen

(sorry it's in dutch)

following suggestions here i added this to my /boot/grub/menu.lst

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

but that didn't work obviously. Neither did (hd0,4) instead.

any suggestions guys?

thx, Freet

---

### Post by Crafty Kisses on 2008-09-05
You will need to edit your menu.lst file:
(Open a terminal, copy & paste one line at a time, press "enter" each time)
```

cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

The first line changes to the grub directory, the second line makes a backup of your menu.lst file, and the third line opens the menu.lst file using the gedit text editor.

Copy and paste the following lines above the line
```
###BEGIN AUTOMAGIC KERNEL LIST

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

If grub gives an error when rebooting, you can try rootnoverify (hd1,0) instead of root (hd1,0) in the second line.

Note: If you prefer Ubuntu to boot by default, you can copy & paste the above entry at the very end of your menu.lst, instead of above ###BEGIN AUTOMAGIC....

To automatically display the grub menu at bootup, find the line

```
hidden
```

and replace with


```
#hidden
```

To adjust the time grub is displayed at bootup, change the timeout(in seconds)...I'd suggest 10 seconds(default is 3).

Quit and save settings.

Note: If for some reason you need to restore your original menu.lst

```
cd /boot/grub
sudo cp menu.lst_backup menu.lst

```
Reboot your computer, it will automatically boot to Windows, unless you choose Ubuntu within the time grub is displayed.

If you want to uninstall Ubuntu, you can make the Windows drive primary master and reformat or unplug the Ubuntu drive.

If you want to remove Windows, then you can unplug the Windows drive or reformat it, then open menu.lst

```

gksudo gedit /boot/grub/menu.lst
```

and remove the Windows entry in grub.

Installing on a Dell Dimension 4550:
I tried the above method trying to set up a dualboot on my Dell Dimension 4550, but when I tried to boot into Windows, I got "Error 21:Selected disk does not exist".
I finally was able to get it to work by:
Boot into **Ubuntu**, open up a terminal:
```

sudo fdisk -l
```

The -l is a lowercase "L"

```
cat /etc/fstab
```

From these two commands, I was able to determine that hdb, which was the slave drive with windows actually had 2 partitions. The first partition was a 35 Mb Dell utility and the second partition was Windows, so I changed the Windows root from (hd1,0) to (hd1,1) in the /boot/grub/menu.lst. However, I continued to get the error21 message...I thought maybe the jumper settings on the slave drive were incorrect. Fortunately, I entered bios setup by pressing "F2" during bootup and found out that the Primary ide controller for hd1 was turned "off" by default...I changed it to "Auto" detect. Grub booted directly into Windows and I'm enjoying dualboot of Windows and Dapper on my Dell computer.

It is possible to set up a dualboot with Windows & Ubuntu on separate hard drives, with **both hard drives connected** during the install of Ubuntu:
[http://ubuntuforums.org/showpost.php?p=2195398&postcount=47](http://ubuntuforums.org/showpost.php?p=2195398&postcount=47)
if you want to be absolutely sure not to overwrite your Windows mbr, then disconnect your Windows drive during Ubuntu installation.

An excellent tool to download before installing Ubuntu is the Super Grub Disk:
[supergrub.forjamari.linex.org](supergrub.forjamari.linex.org)
the Super Grub Disk is capable of restoring Windows mbr or reinstall grub, and can boot either Windows or Ubuntu.

---

### Post by freet on 2008-09-05
this gives error 21: selected disk does not exist.
(btw originally it caused error 12)

ubuntu still boots correctly but with a lot of lag.. restoring the original menu.lst removes this latency.

i followed your instructions so what could be wrong?

---

### Post by Crafty Kisses on 2008-09-05
Could be a lot of issues, did you try SuperGRUB?

---

### Post by caljohnsmith on 2008-09-05
Codename's instructions didn't work because your Windows is not on another HDD, so you don't need to use (hd1,0) or do any mapping in Grub. :) I think the problem is:
```
Apparaat Opstart Begin Einde Blokken ID Systeem
/dev/sda1 * [COLOR="Red"]2 24321[/COLOR] 195350400 f W95 Uitgeb. (LBA)
/dev/sda5 [COLOR="Red"]2 16709[/COLOR] 134206978+ 7 HPFS/NTFS
/dev/sda6 16710 24196 60139296 83 Linux
/dev/sda7 24197 24321 1004031 82 Linux wisselgeheuge
```
Note that sda1 and sda5 overlap when they shouldn't, since both are primary partitions. It looks like sda1 should be an extended partition that contains sda5, sda6, and sda7. But even if you fix your HDD's partition table to make sda1 an extended partition, you will then have to go through a bit of trouble getting Windows to boot from a logical partition; Windows can be booted from a logical partition, but it is easier to boot Windows from a primary partition.

Do you remember what type of partitioning structure you set up when you installed Ubuntu? There is a program called "testdisk" that can probably help you fix your HDD's partition table, but it would help to know what you did when you installed Ubuntu.

---

### Post by freet on 2008-09-05
yup i saw this overlapping too but i dont know the cause of that..

when i installed ubuntu, i had an empty partition on my windows. i formatted this one and made an ext3-partition (logical, not primary) attached to / and a swap partition from it. I didnt touch the windows partition at all, thats why this overlapping is kinda strange to me.

if i get ur info right, my disk is like one big partition seperated in 3 smaller pieces? The * in this table should point at sda5 and not at sda1 i guess? 

Any clue how to change this? atm i'm burning a partition program cd to boot.

---

### Post by caljohnsmith on 2008-09-05
Do you remember exactly what your partitions looked like before you installed Ubuntu? Did you have the two following Windows partitions:
```
/dev/sda1 * 2 24321 195350400 f W95 Uitgeb. (LBA)
/dev/sda5 2 16709 134206978+ 7 HPFS/NTFS

```
Because I'm guessing what you really had was just sda5, which is your true Windows partition. Can you mount sda5 in Ubuntu and see all your Windows files OK? And when you mount sda1, does it give you some kind of error?

---

### Post by freet on 2008-09-05
while installing ubuntu those two partitions were already present, yes.
i'll try to mount both and edit in a second =)

ok.. /dev/sda5 has been succesfully mounted and i can access all the windows-files through it. sda1 failed with both -t ntfs and -t vfat in the mount parameters.

---

### Post by caljohnsmith on 2008-09-05
> **freet said:**
> while installing ubuntu those two partitions were already present, yes.
i'll try to mount both and edit in a second =)

ok.. /dev/sda5 has been succesfully mounted and i can access all the windows-files through it. sda1 failed with both -t ntfs and -t vfat in the mount parameters.
So before you installed Ubuntu, was the only partition with anything on it the Windows partition? Or did you have two partitions that weren't empty? (Maybe a data partition in addition to your Windows partition).

---

### Post by freet on 2008-09-05
prior to ubuntu installation i had:

C:\ -> used for windows and documents

I:\ -> NTFS-partition with nothing on it, This one i formatted and made 2 partitions of it: ext3 attached to / & a swap partition. I made the ext3 logical, not primary.

Googling and reading around here i used testdisk, this is its output:

[I]Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 E extended LBA             1   0  1 24320 254 63  390700800
[COLOR="Red"]No partition is bootable[/COLOR]
 5 L HPFS - NTFS              1   1  1 16708 254 63  268413957
   X extended             16709   0  1 24195 254 63  120278655
 6 L Linux                16709   1  1 24195 254 63  120278592
   X extended             24196   0  1 24320 254 63    2008125
 7 L Linux Swap           24196   1  1 24320 254 63    2008062
[/I]

i guess thats the core of the problem, no?

---

### Post by caljohnsmith on 2008-09-05
OK, I think then your partitioning problem will be easy to fix. From within Ubuntu, try this:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it will give. Then do "proceed", "N" to find Vista partitions, then "enter", select "search!" so it does a deeper search which will take a while. Once it finds your partitions, then mark your Windows partition (sda5 from your fdisk output) as the bootable partition (should have an asterisk) and mark both of your Ubuntu partitions as logical. If the sda1 partition or any other partitions are in that list, mark them as deleted. You can make sure the partition you are marking is what you think it is by comparing its start/stop points with what fdisk originally told you. Then "proceed" to next screen, make sure it is all correct, and then have testdisk write your new partition table to the HDD master boot record (MBR). Let me know how it goes or if you have any problems.

---

### Post by freet on 2008-09-05
hehe the search was already running :P

i'll follow your advice from there on and get back to you with results!

---

### Post by freet on 2008-09-05
this is the output

Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 16708 254 63  268430022
D HPFS - NTFS              1   1  1 16708 254 63  268413957
D HPFS - NTFS          16709   0  1 24320 254 63  122286780 [Data]
D Linux                16709   1  1 24195 254 63  120278592
D Linux Swap           24196   1  1 24320 254 63    2008062

original fdisk -l

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           2       24321   195350400    f  W95 Uitgeb. (LBA)
/dev/sda5               2       16709   134206978+   7  HPFS/NTFS
/dev/sda6           16710       24196    60139296   83  Linux
/dev/sda7           24197       24321     1004031   82  Linux swap

I think i should make 

D HPFS - NTFS              1   1  1 16708 254 63  268413957

as the bootable partition, both linux partitions as logic and the other two remain deleted.

Is that correct you think?

---

### Post by caljohnsmith on 2008-09-05
> **freet said:**
> this is the output

```
Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]D HPFS - NTFS              0   1  1 16708 254 63  268430022[/COLOR]
D HPFS - NTFS              1   1  1 16708 254 63  268413957
D HPFS - NTFS          16709   0  1 24320 254 63  122286780 [Data]
D Linux                16709   1  1 24195 254 63  120278592
D Linux Swap           24196   1  1 24320 254 63    2008062
```

I think that first partition, since it starts at 0 (the first cylinder for testdisk) is probably your windows partition, not the second one. And it is really important to include that first cylinder since it will contain the partition boot record (PBR) and other important file system stuff for Windows. Try using the "P" option in testdisk to actually list the files in that partition, and make sure it is your windows partition. If it is, I would use that one.

---


---
title: "RAID array gone, can't get it going again!"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by HAARP on 2006-06-18
Hello there
Iv'e got Ubuntu Dapper Drake installed on a normal PATA disk. I also have 2 SATA drives accessed by a SilRaid-Controller (Hardware-RAID deactivated because it's just a Fake-Software-RAID), which i wanted to use for a RAID-0 array.
They are **/dev/sda** and **/dev/sdb**
I set them up with **mdadm** (had to load module **md** first and set it to autoload at boot, also had to create a **/dev/md0** device). Formatted em with *ReiserFS*, worked fine so far. So i set them up in **fstab** to mount into the **/home** directory for me to use as a fast disk to keep my files, copied the home onto the array and deleted the old one in **/home**
Tried to reboot. Well, looks like the array refuses to mount and **mdadm** says it doesn't have anything in it's config files (it worked before reboot!)
So i tried the **--assemble** command to look if i could get the bugger going again. No, he can't do it, *there's no such file/directory **/dev/sda1*** he says. Huh? Because he can't use **sda**, he also says there's no *superblock* on it, which results in it not working.
Now I'm feeling kinda stupid for deleting my home and not being able to mount the array (which isn't a array anymore because mdadm won't work) #-o 
Why is **/dev/sda** non-existant to mdadm? The block-device is there, I checked it in mc. I can't post here with my Linux system because I'm afraid of what happens if i log into gnome with a non-existant home 
So I have to use my Windoze machine (ugh!). What can I do?
 I just want the array to work again. What could possibly be the reason? What information do you need?

---

### Post by therunnyman on 2006-06-18
Oh dear, another victim...

It's a bug, well documented, confirmed a million times, but the devs tell us not to expect a fix until Edgy.

This may help, brother:

[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)

[http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41](http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41)

Your pain is mine.

runny

---

### Post by HAARP on 2006-06-18
Thanks for answering so fast!
Well, the drive the OS is installed on is **hda2**, so that shouldnt matter.
I used the Bios-Raid of the Sil-card before, and got it working with dmraid, even after reboots. Why didn't **sda/sdb** vanish back then?
But performance was bad, so I decided to use a real Linux Software-Raid :)
But: The drives are connected to a addon-card which has only 2 ports. They have to be **sda/sdb**, because I don't have any other SATA-drives/controllers, not in a PCI slot, nor onboard.
Is my problem still the same problem you described?
I'm going to try out some other sdx now. Wish me luck :)

---

### Post by HAARP on 2006-06-18
Looks like **sda/sdb** completly vanished. But I rebooted several times after installing Ubuntu, without this happening. As soon as i managed to set up the **mdadm** Raid-array, they were gone after reboot.
Obviously **mdadm** is responsible for this. Did it damage **udev**? Any ideas?

---

### Post by HAARP on 2006-06-19
Sorry for triple posting, but now I know that to **sda/sdb** are still there and functioning. **hdparm** can read them just fine. But mdadm won't work:
```
Error opening device /dev/sda1: No such file or directory
```
However, **hda/hdb** work just fine when I try to access them via **mdadm**

What the hell?

---

### Post by HAARP on 2006-06-20
quadpost, well...
So now I know what the problem is: There are no partitions on **hda/hdb**. The whole partition table is gone! ](*,) 
I need that data! Recovery under Linux, from a RAID array which drives have a missing partition table, how do you do that?

---

### Post by HAARP on 2006-06-22
Fifth and last post:
I found a Windoze utility named Winhex which was able to connect both drives with a given chunk size and read the data without the partitions. 8) 
Oh my god, this took me 3 days to get going again :-?

---


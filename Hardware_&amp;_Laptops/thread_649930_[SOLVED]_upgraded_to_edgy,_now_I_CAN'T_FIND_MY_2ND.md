---
title: "[SOLVED] upgraded to edgy, now I CAN'T FIND MY 2ND HD!"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by rabbix2 on 2007-12-25
I just upgraded from dapper to edgy. Before rebooting I reconnected my 2nd hd, but now I can't find it among the files!  Before upgrading, I used both hd together without problems. The computer DOES know it's there, because I CAN find it through gparted. BUT I CAN'T USE IT!!!
What can I do?

---

### Post by taurus on 2007-12-25
You probably need to mount it first before you can access it.  Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
cat /etc/fstab
df -h
```

---

### Post by rabbix2 on 2007-12-25
I did what you said, and this is what I got. As I understand it, only info about my 1st hd.

root@gurkan-desktop:~# sudo fdisk -l <-- lower case letter l, not number 1
bash: --: Filen eller katalogen finns inte
root@gurkan-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=617eafa7-2029-4226-93cf-c6e230d830ac / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=3634532d-5b40-4b45-ab09-4195e22918ef none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
root@gurkan-desktop:~# df -h
Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/sda1              71G  3,5G   64G   6% /
varrun                633M   88K  633M   1% /var/run
varlock               633M  4,0K  633M   1% /var/lock
procbususb             10M  132K  9,9M   2% /proc/bus/usb
udev                   10M  132K  9,9M   2% /dev
devshm                633M     0  633M   0% /dev/shm
lrm                   633M   18M  615M   3% /lib/modules/2.6.17-12-386/volatile
root@gurkan-desktop:~#

---

### Post by taurus on 2007-12-25
Can you run the first command again but without the [COLOR="Blue"]<--[/COLOR] stuff behind it?

```
sudo fdisk -l
```

---

### Post by rabbix2 on 2007-12-25
Before using them together I did use my 2nd hd as the only one, with dapper. But then, after installing some software, it didn't boot anymore, no matter what i did. So then I started using the two hd together, booting hd1, dapper, and I could read and use all the material on hd2. But, as I said, that was before the upgrading (which I used with hd2 disconnected, to be sure nothing would happen to it - maybe that's the problem..)

---

### Post by rabbix2 on 2007-12-25
Sorry, computer hanged, had to reboot.
Here is the result, looks better, doesn't it!

root@gurkan-desktop:~# sudo fdisk -l

Disk /dev/sda: 80,0 GB, 80026361856 byte
255 huvuden, 63 sektorer/spår, 9729 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9729     3196935    5  Utökad
/dev/sda5            9332        9729     3196903+  82  Linux växling / Solaris

Disk /dev/sdb: 250,0 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1   *           1       29929   240404661   83  Linux
/dev/sdb2           29930       30401     3791340    5  Utökad
/dev/sdb5           29930       30401     3791308+  82  Linux växling / Solaris
root@gurkan-desktop:~#

---

### Post by rabbix2 on 2007-12-25
By the way, I want to delete Dapper from hd2, do I understand it right, that if I remove sdb2 and sdb5, I won't touch my other files on hd2?

---

### Post by taurus on 2007-12-25
By the way, it's not a good idea to log in as root but if you are, be real careful with it, okay.  For now, I assume you are logged in as a regular user, instead of root.

Edit /etc/fstab with

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
/dev/sdb5   none   swap   sw   0   0
```
Save the changes and close down gedit window.  Now, create a new mount point and mount /dev/sdb1 to /media/sdb1 and your swap partition, /dev/sdb5.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
free
```

---

### Post by taurus on 2007-12-25
> **rabbix2 said:**
> By the way, I want to delete Dapper from hd2, do I understand it right, that if I remove sdb2 and sdb5, I won't touch my other files on hd2?

Your PATA drivers are now known as SATA.  So, the first drive is /dev/sda and the second drive is /dev/sdb.  They're not /dev/hda & /dev/hdb anymore.

---

### Post by rabbix2 on 2007-12-25
What do I do now? In gparted it looks as if hd2 IS mounted..

---

### Post by taurus on 2007-12-25
What exactly are you planning to do?  Do you want to erase everything from the second harddrive?  What's the output of this command from a terminal?

```
df -h
```

---

### Post by rabbix2 on 2007-12-25
Yes I know, sorry if I'm sloppy with the naming. I still don't find sdb in the file list. What to do? And after I find it, I want toremove dapper from it, without removing my saved files..

---

### Post by rabbix2 on 2007-12-25
df -h only shows sda:

root@gurkan-desktop:~# sudo df -h
Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/sda1              71G  3,4G   64G   6% /
varrun                633M   88K  633M   1% /var/run
varlock               633M  4,0K  633M   1% /var/lock
procbususb             10M  136K  9,9M   2% /proc/bus/usb
udev                   10M  136K  9,9M   2% /dev
devshm                633M     0  633M   0% /dev/shm
lrm                   633M   18M  615M   3% /lib/modules/2.6.17-12-386/volatile
root@gurkan-desktop:~# 

About sdb: I want to erase DAPPER but keep all the SAVED FILES.

---

### Post by taurus on 2007-12-25
If you want to remove Dapper from your second harddrive, it means you probably need to reformat the partition, /dev/sdb1, so better mount it to /media/sdb1 and copy your stuff over to your first harddrive, /dev/sda1.  Then, reformat the second harddrive and use it as a storage space.

---

### Post by rabbix2 on 2007-12-25
This is the result of mounting sdb. But I still can't find it among the files. What now?

About saving my sdb-files to sda and then reformat sdb, THANKS, that DOES seem to be the best to do! After solving the above problem..

---

### Post by rabbix2 on 2007-12-25
Sorry, forgot to paste..


root@gurkan-desktop:~# gksudo gedit /etc/fstab
root@gurkan-desktop:~# sudo mkdir /media/sdb1
root@gurkan-desktop:~# sudo mount -a
root@gurkan-desktop:~# df -h
Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/sda1              71G  3,4G   64G   6% /
varrun                633M   88K  633M   1% /var/run
varlock               633M  4,0K  633M   1% /var/lock
procbususb             10M  136K  9,9M   2% /proc/bus/usb
udev                   10M  136K  9,9M   2% /dev
devshm                633M     0  633M   0% /dev/shm
lrm                   633M   18M  615M   3% /lib/modules/2.6.17-12-386/volatile
/dev/sdb1             226G   16G  200G   8% /media/sdb1
root@gurkan-desktop:~# free
             total       used       free     shared    buffers     cached
Mem:       1295240     401444     893796          0      57184     201860
-/+ buffers/cache:     142400    1152840
Swap:      3196892          0    3196892
root@gurkan-desktop:~#

---

### Post by taurus on 2007-12-25
Your second harddrive is now mounted to /media/sdb1.  What files do you want to save from your second harddrive?

---

### Post by rabbix2 on 2007-12-25
Computer hanged again! Rebooting, I got this message:
/dev/sdb1 was not cleanly unmounted, check forced

Happily, after logging in, sdb1 appeared on my desktop :)!

So now, saving files from sdb1:
I have a couple of music and film downloads, most of them not finished. If possible, I would like to save and continue them, because they took an awful long time to download.

---

### Post by taurus on 2007-12-25
> **rabbix2 said:**
> 
So now, saving files from sdb1:
I have a couple of music and film downloads, most of them not finished. If possible, I would like to save and continue them, because they took an awful long time to download.

Wait!  Are we talking about legal or illegal download here?  What application did you use to download them from Dapper?

---

### Post by rabbix2 on 2007-12-25
Ok, thanks a lot, I will mark this problem as solved :guitar:!
If you didn't go to sleep yet, any advice about restarting the downloads from sda? I use Azureus, and I understand, that I have to do a lot of renaming, but is there anything else I must do?
Nitynite!

---

### Post by taurus on 2007-12-25
Maybe you want to copy the contain of ~/.azureus from your second harddrive, /dev/sdb1, to your first harddrive, /dev/sda1, where new $HOME directory is.  Then, hopefully azureus will pick up where it left off.

---


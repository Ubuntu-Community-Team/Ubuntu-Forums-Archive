---
title: "[SOLVED] need assistance mounting external hdd"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by kavmac on 2008-01-07
i'm trying to mount my 250gb comstar external hard drive in gutsy, but have so far been unsuccessful.  looking for some assistance from anyone that is willing to help me out!

thanks in advance :)

---

### Post by kavmac on 2008-01-08
any thoughts or suggestions?

---

### Post by kavmac on 2008-01-08
only problem with that is, that it's an *external* hard drive (which is connected to my computer via usb), so it won't be either (or am i completely wrong there?)...

---

### Post by kavmac on 2008-01-09
any one have another suggestion?

---

### Post by taurus on 2008-01-09
Make sure the USB drive is plugged in and power on.  Then, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by kavmac on 2008-01-09
```
kris@kavmac:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd5bdd5b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19293   154970991   83  Linux
/dev/hda2           19294       19457     1317330    5  Extended
/dev/hda5           19294       19457     1317298+  82  Linux swap / Solaris

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeea7b994

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001    7  HPFS/NTFS

```

thanks for your quick reply!

---

### Post by taurus on 2008-01-09
Try

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sde1
sudo mount -t ntfs-3g /dev/sde1 /media/sde1
ls -la /media/sde1
```

---

### Post by kavmac on 2008-01-09
okay, once i got to the sudo mount, this is what happened
```
kris@kavmac:~$ sudo mount -t ntfs-3g /dev/sde1 /media/sde1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sde1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sde1 /media/sde1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sde1 /media/sde1 ntfs-3g defaults,force 0 0

```

so i went ahead and tried the ls -la /media/sde1 and this is the result
```
kris@kavmac:~$ ls -la /media/sde1
total 8
drwxr-xr-x 2 root root 4096 2008-01-09 18:45 .
drwxr-xr-x 5 root root 4096 2008-01-09 18:45 ..

```

do i really want to be force mounting my hard drive?

---

### Post by taurus on 2008-01-09
Well, you have two options:

1.  Maybe you want to hook that external drive to a windows machine and run scandisk on it.  Then, shutdown your windows cleanly, without unplugging the external drive first.

or

2.  You can just use the force option to mount it.

```
sudo mount -t ntfs-3g /dev/sde1 /media/sde1 -o force
```

---

### Post by Rowanmf on 2008-01-09
ok , i had the exact same problem , some time ago with my 100gig usb drive , try this -

in the software manager make sure all repo's are ticked and search for ntfs-config 
download and let it install , then plug your drive in and run the util from the menu link or go to a terminal and type - ntfs-config , tick appropriate boxes and exit .

i hope it works for you , any way it's 2am here now , will check back later in the morning to see if you had any luck ..


Rowan

---

### Post by kavmac on 2008-01-09
Since I don't have immediate access to a windows machine, I will go for option two.  However before I proceed, how much of a risk is it to force mount the hard drive?  I'm going to guess that it should (should being the key word here) be safe to mount it then transfer all of the files and then do a reformat, but that there are the obvious risks that i could end up with missing files, etc.  So with that said, the best option after doing the force mount would be to reformat, instead of continuing to use the hard drive as is - yes/no?

thanks again :)

---

### Post by kavmac on 2008-01-09
thanks for the tip!  however, it still won't let me mount it after :(

---

### Post by kavmac on 2008-01-10
i was able to get access to a windows machine... and it solved the problem.  thanks for your assistance!

---


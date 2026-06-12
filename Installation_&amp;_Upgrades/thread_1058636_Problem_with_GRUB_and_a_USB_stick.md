---
title: "Problem with GRUB and a USB stick"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by DavidFromCanada on 2009-02-03
So I wanted to run Super Grub off a USB stick so I followed these instructions:
```
Gnome
Unmount and unplug your pendrive device.
Open a terminal and run:
mount
Insert your pendrive. A window with pendrive contents should open.
mount
Now in the mount output you should see one more line than in the first run of mount:
/dev/sdb1 on /media/all type ext3 (rw,nosuid,nodev,uhelper=hal,data=ordered)
Now we have learnt that the USB device is called: /dev/sdb1 (From now on... you should continue the howto with your own USB device which might be /dev/sda1 or something similar).
Get the Super Grub Disk USB tar. Untar it in a temporary folder. Copy and paste the boot folder found in the USB tar so that when opening your pendrive you see: boot (You should not see super_grub_disk_0.9753 or something similar).
Close the pendrive window
Find your pendrive icon in your Desktop.
Right-click on it
Select Umount. Do not select Safe Extraction!!!
Get root permissions on the terminal
sudo su # in ubuntu
su # In other systems
sync
Now we will use the /dev/sdb (/dev/sdb is ther hard disk where /dev/sdb1 partition is located) device in grub to associate a virtual grub device (hd3) to it and work with it.
grub
grub>device (hd3) /dev/sdb
grub>root (hd3,0)
grub>setup (hd3)
You should see some messages with perhaps some normal errors.
 grub>quit
 sync
You can now unplug your pendrive.
```

But now I'm done with Super Grub so I wiped the USB stick clean. So I needed this USB stick to boot up a live image. So I made the live image using intrepid's tool and booted it up. I get a GRUB error 15 instead of a live image. I wiped the stick again and put the image on again. Same thing! So I put the Super Grub files back on it. It boots up Super Grub. How do I make GRUB stop thinking there's super grub on this USB stick? As well has anyone used the distro protech with an Eee PC? Thats what I'm trying to do.

---

### Post by caljohnsmith on 2009-02-03
How about reinstalling to the USB stick using Intrepid's program, and then download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
Of course make sure the USB stick is connected when you run the script. The script will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by DavidFromCanada on 2009-02-03
Solved I used another USB port so the drive was identified as sdd rather then sdb.

---


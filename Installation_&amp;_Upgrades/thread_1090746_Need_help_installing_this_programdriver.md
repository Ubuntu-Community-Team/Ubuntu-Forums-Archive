---
title: "Need help installing this program/driver"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by catdeerduck on 2009-03-08
Im trying to install this drivers onto my PC. The OS that im using is Ubuntu intrepid or 8.10.
The driver im trying to install is Linux_7703
Moschip 7703

This is how far i get

Cd Desktop
tar xzvf Linux_7703.tar.gz
This files then appear
Linux_7703/16C50.h
Linux_7703/mosinstall
Linux_7703/README
Linux_7703/usb-serial.h
Linux_7703/mos7703.h
Linux_7703/mos7703.c
Linux_7703/Makefile
Linux_7703/mosuninstall

After this what am i suppose to do.
When i type in ./configure it gives me this error-bash: ./configure: No such file or directory

IM NOT SURE WHAT IM SUPPOSE TO DO AFTER IT SHOWS THE FILES AND I NEED TO INSTALL THIS PROGRAM/Driver!!

---

### Post by neu2buntu on 2009-03-08
goto the readme with nautilus (file browser) and open it with gedit..this file will have all the install instructions.....

---

### Post by Neo_The_User on 2009-03-08
You can also use nano, vi or vim to open up the file.

---

### Post by neu2buntu on 2009-03-08
also are the files being extracted all seperately to the Desktop... if they are you will have to make a folder for them

---

### Post by catdeerduck on 2009-03-08
This is what it says in the read me file

This driver has been tested on FC4 kernel version 2.6.11.

Instructions for Installing the driver:



make load: To install the driver.



make unload: To uninstall the driver.



make install: To install the driver while kernel bootup.



make uninstall: Removing the installed driver while kernel bootup.

Files included in this release:

16C50.h
Makefile
mos7703.c
mos7703.h
mosinstall
mosuninstall
usb-serial.h
README

---

### Post by catdeerduck on 2009-03-08
> **neu2buntu said:**
> also are the files being extracted all seperately to the Desktop... if they are you will have to make a folder for them
I have the folder already but i don't know how to install it

---

### Post by Neo_The_User on 2009-03-08
...Try this

```

cd
mkdir driver && cd driver
tar zxf (put the driver compressed tar.bz2 file here.)

```

After extracting it in /home/whatever/driver check the output

```

ls

```

Now if you see a file named README or something like that type  in

```

gedit README

```

Replace gedit with whatever text editor you want to you use and replace README with whatever the README file is called. Good luck.

---

### Post by catdeerduck on 2009-03-08
> **Neo_The_User said:**
> ...Try this

```

cd
mkdir driver && cd driver
tar zxf (put the driver compressed tar.bz2 file here.)

```

After extracting it in /home/whatever/driver check the output

```

ls

```

Now if you see a file named README or something like that type  in

```

gedit README

```

Replace gedit with whatever text editor you want to you use and replace README with whatever the README file is called. Good luck.

it gives me this
Desktop/driver$ tar xzvf Linux_7703.tar.gztar: Linux_7703.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by Neo_The_User on 2009-03-08
Check the command you entered for spelling errors and or the extension (the .tar.gz string)

---

### Post by catdeerduck on 2009-03-08
This is what i did

-desktop:~$ cd driver
-desktop:~/driver$ tar xzvf Linux_7703.tar.gz
Linux_7703/16C50.h
Linux_7703/mosinstall
Linux_7703/README
Linux_7703/usb-serial.h
Linux_7703/mos7703.h
Linux_7703/mos7703.c
Linux_7703/Makefile
Linux_7703/mosuninstall
-desktop:~/driver$ ls
Linux_7703  Linux_7703.tar.gz
-desktop:~/driver$ gedit README

BUT THEN IT SHOWED MAC4LIN for Some reason


/home/homecomputer/.themes/Mac4Lin_MacMenu_Graphite_v0.4/gtk-2.0/gtkrc:2219: Unable to find include file: "icons/iconrc"

** (gedit:17592): WARNING **: Cannot extract frame (0, 0) from the grid


** (gedit:17592): WARNING **: Cannot extract frame (36, 0) from the grid


** (gedit:17592): WARNING **: Cannot extract frame (72, 0) from the grid


** (gedit:17592): WARNING **: Cannot extract frame (108, 0) from the grid


** (gedit:17592): WARNING **: Cannot extract frame (144, 0) from the grid


** (gedit:17592): WARNING **: Cannot extract frame (180, 0) from the grid


** (gedit:17592): WARNING **: Cannot extract frame (216, 0) from the grid


** (gedit:17592): WARNING **: Cannot extract frame (252, 0) from the grid

---

### Post by neu2buntu on 2009-03-08
here the way i would go about installing your driver from source 
1. right click on your tar.gz file > choose open with archive manager
2. click > extract > choose your username(home directory) > tick recreate-folders > extract
3.open terminal > cd name of the folder for driver
4. now you are in the driver folder do ```
sudo make install
```

normally you need make then make install, but i think this is the command you want to have the driver loaded every bootup

---

### Post by Neo_The_User on 2009-03-08
If you need something to be started up at boot, you'll need to set the installation directory to /usr (./configure --prefix=/usr) and then edit /etc/rc.conf and add it to DAEMONS located... I think... on the last few lines in between the parenthesis.

---

### Post by catdeerduck on 2009-03-12
I was able to install it but when i type lsusb it doesn't appear and it appears in dmesg. This is what it says 
This is dmesg
[ 9628.172019] usb 8-3: new high speed USB device using ehci_hcd and address 7
[ 9628.305367] usb 8-3: configuration #1 chosen from 1 choice
and it also says this
[ 9721.965020] usb 8-3: new high speed USB device using ehci_hcd and address 8
[ 9722.484021] usb 8-3: device not accepting address 8, error -71
[ 9722.540175] hub 8-0:1.0: unable to enumerate USB device on port 3
and in Lsusb it doesn't appear

---


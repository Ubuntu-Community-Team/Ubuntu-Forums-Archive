---
title: "USB Cradle not syncing to computer"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by tc10b on 2007-02-01
Hi.

I've been using my palm pilot with Ubuntu for a while now with the normal serial cradle and everything worked fine.
I then managed to break my serial cradle and have recently purchased a USB cradle.  I've tried using it with J-Pilot but it doesn't find it.

I've tried using several different paths, but it can't find any of them and gives the following output when I try to sync.

****************************************
 Syncing on device /dev/ttyusb1
 Press the HotSync button now
****************************************
pi_bind error: /dev/ttyusb1 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished
****************************************
 Syncing on device /dev/ttyusb0
 Press the HotSync button now
****************************************
pi_bind error: /dev/ttyusb0 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished
****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished
****************************************
 Syncing on device /dev/ttyUSB0
 Press the HotSync button now
****************************************
pi_bind error: /dev/ttyUSB0 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished
****************************************
 Syncing on device /dev/ttyUSB1
 Press the HotSync button now
****************************************
pi_bind error: /dev/ttyUSB1 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

Any suggestions?

Cheers

Tom

---

### Post by lsatenstein on 2007-07-22
Any clues? I tried to find the explanation for SYNC_ERROR_BIND

I will try /dev/ttyusb0 through /dev/ttyUSB6.

Who knows....

It is now July 20th, and I have no feedback as yet.

---

### Post by lsatenstein on 2007-07-22
I have a solution

first of all, create or verify  sudo gedit /etc/udev/rules.d/10-custom.rules

It should contain (on one line)

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="0666"

start jpilot and check this

file->properties-->settings for usb  should be      /dev/ttyUSB1

verify the other settings (name, etc.) and when satistified exit jpilot, go to the terminal prompt and do the following

sudo jpilot

This will start jpilot in root mode.

Now click on the palm pilot to start hotsync. 

Once you do that, click on the hotsync for jpilot. It should work. it worked for me. 

Now, we have to change some directories.

cd to /home/logonid/.jpilot
sudo chown logonid:logonid *
chmod 660 *
chmod +t *

The 660 is for owner and group to be able to read the palm backup files.
the  chmod +t is to preserve logonid as the owner, as you wish to be able to refer to the files without having to do a sudo jpilot

Hope that helps out. Eventually something will occur for the dynamic /dev/ttyUSB stuff. 

You could help by researching   man udev or info udev

please post answer here.

---

### Post by kgr132 on 2007-07-24
I had a similar problem with J-Pilot not being able to find my Palm on the USB cradle. I have a Palm Tungsten T and I'm using Feisty pretty much as it came off of the CD. I remembered that when I was trying to get my Palm to sync using gnome-pilot, it failed to find my Palm and the gnome-pilot setup suggested that I should use usb: in place of /dev/tty/USB* because of some missing kernel module or something. Since that suggestion worked with gnome-pilot, I set J-Pilot to use the same port as I used with gnome-pilot: usb: To set it up, I navigated to File...Preferences...Settings in J-Pilot and set the Serial Port to usb: instead of /dev/pilot, /dev/tty/USB1 or whatever. Now when I hit the Hotsync button in J-Pilot and the Hotsync button on my Palm, everything goes as it should. It's also a lot faster than when I sync with Palm Desktop on my Windows PC. J-Pilot rocks! Now...if only I could get my Palm to sync via BlueTooth. :confused:

-K-

---

### Post by lbravo on 2007-11-05
kgr132's method worked great for me.  Running Ubuntu 7.10 Gutsy Gibbon on a Sony notebook.  Sync'd a Palm T|X with no problems after changing to usb:  I had already tried everything else.  Also left the 10-custom-rules in my /etc/udev/rules.d directory from the previous suggestion.

Thanks so much for your help guys.  This was a new T|X I bought specifically because I use Ubuntu.  I was going to be so disappointed if I couldn't get it to work like my previous (lost) Clie.

LBravo
:guitar:
u roc

---

### Post by fadyek on 2008-05-09
Thank you so much kgr132. On Feisty I was able to sync using gpilotd and /dev/ttyUSB0. But since I upgraded to Hardy it didn't work for some reason. It just worked only using your method. Thanks again. You save me a lot of effort!!

---

### Post by Bruce M. on 2008-05-16
> **lsatenstein said:**
> I have a solution

first of all, create or verify  sudo gedit /etc/udev/rules.d/10-custom.rules

It should contain (on one line)

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="0666"

start jpilot and check this

file->properties-->settings for usb  should be      /dev/ttyUSB1

verify the other settings (name, etc.) and when satistified exit jpilot, go to the terminal prompt and do the following

sudo jpilot

This will start jpilot in root mode.

Now click on the palm pilot to start hotsync. 

Once you do that, click on the hotsync for jpilot. It should work. it worked for me. 

Now, we have to change some directories.

cd to /home/logonid/.jpilot
sudo chown logonid:logonid *
chmod 660 *
chmod +t *

The 660 is for owner and group to be able to read the palm backup files.
the  chmod +t is to preserve logonid as the owner, as you wish to be able to refer to the files without having to do a sudo jpilot

Hope that helps out. Eventually something will occur for the dynamic /dev/ttyUSB stuff. 

You could help by researching   man udev or info udev

please post answer here.

***Please NOTE:*** If you are going to "sudo" a GUI application the proper command is:
```
gksudo gedit /etc/udev/rules.d/10-custom.rules
```
you can however use:
```
sudo nano /etc/udev/rules.d/10-custom.rules
```

Another place to look at it: [PalmDeviceSetup]("https://help.ubuntu.com/community/PalmDeviceSetup"), I did what it said and still had problems ... reading further down I saw:

>     * I used these directions and they worked great. but after upgrading to gusty I had problems again. I seems that in gusty there is a udev rule already set up for palm devices that conflicted with this rule above. in the file "60-symlinks.rules" I commented out the rule that was for palm devices and my treo 650 syncs again like before. With the 2 rules together I was getting /dev/pilot becoming symlink to IT'S SELF. if you see some thing like this:

ls -l /dev/pilot lrwxrwxrwx 1 root root 5 2008-01-21 00:10 /dev/pilot -> pilot you might have a similar problem.

Fixed my problem, the "60-symlinks.rules" is there in 8.04 as well  :)

Have a nice day.
Bruce

---


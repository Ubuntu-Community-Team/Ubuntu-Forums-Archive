---
title: "Garmin Etrex H with Ubuntu 10.10"
date: 2011-06-11
forum: Hardware
---

### Post by david.flights on 2011-06-11
Hello ya'll - 

Trying to connect a Garmin eTrex H with Ubuntu 10.10. When I plug the device in with the USB cable there is no icon in my file manager (nautilus). 

I have read a few posts, and download some scripts for the terminal, with no luck. I have also read the Garmin manual.

I am trying to download tracklogs and waypoints.

Any help much appreciated. 

Thanks

---

### Post by coolclassic on 2011-06-11
I have the etrex vista hcx to connect using kubuntu is switch on etrex connect usb cable. In the etrex device goto settings > interface and accept mass storage device. Hopefully this will work for you.

OOPS! Sorry your device is serial. I don't think the above helps.

---

### Post by david.flights on 2011-07-14
Coolclassic - My device is USB. But I am running Ubuntu 10.10

Any help much appreciated

---

### Post by coolclassic on 2011-07-22
Have you set interface as suggested.

---

### Post by frogotronic on 2011-12-31
Hello,

  I have the same unit.  Apparently, it doesn't work anymore (since Karmic).  I have the INTERFACE I/O Format as Garmin.

  No luck either with or without garmin_gps blacklisted.

- CH

-----------------------------------------------------------------

The issue has been bug reported and there is a possible workaround: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661321](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661321)

Let me know if it works for you - will try later after a system backup is over.

---

### Post by frogotronic on 2012-01-01
Yep, that's the bug.

Here's the solution:

1) UN-Blacklist the garmin_gps model

```
$ sudo gedit /etc/modprobe.d/blacklist.conf
```

Find the line that looks like this:
```
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps
```

and change it to this:

```
# most apps now use garmin usb driver directly (Ubuntu: #114565)
# blacklist garmin_gps
```

2) Reboot

3) I've created a Menu Item under my GPS Menu (attachement #1).

4) The details for the newly created (manually) Menu Item (from the Menu app under System>Administration) are the following:

[INDENT]Type: **Application**[/INDENT]
[INDENT]Name: **Garmin etrex H Preload**[/INDENT]
[INDENT]Command: **gksu sh ./.garmin**[/INDENT]
[INDENT]Comment: **Workaround for pl2303 kernel bug**[/INDENT]
[INDENT][COLOR="SlateGray"]Icon Image: (see attached #2)[/COLOR][/INDENT]

5) Now make a script (attached #3) and save it in your home directory.  I usually make all these scripts as hidden; (that means put a "." before the file name; example "file.sh" will not be hidden, whereas ".file.sh" will be hidden).  Don't forget to make your script executable, right click and under permissions select "Allow executing as a program".

6) When you plug in your etrex H via the serial to USB cable the pl2303 module will load and not work.  Run the "Garmin etrex H Preload" and it should ask you for your password.  Enter it and then you should see nothing.

7)  Open gpsbabel-gui

[INDENT]```
sudo apt-get install viking gpsbabel-gui gebabbel
```[/INDENT]

8) In gpsbabel-gui (*from terminal type **gpsbabelfe**; If you want this as a menu entry, you'll have to create it manually as there's a bug in the installer in Maverick wherein no menu entry is created; let me know if you need help with this, or you can use the gebabbel (however, this gui is less intuitive than the gpsbabel-gui)*), select Device and Garmin, /dev/ttyUSB0.  Make sure your etrex H is set to Interface of "Garmin" and then output to a file (like "test") and try and retrieve your waypoint data.  You should get a "Transmission Successful!" message and a text file in your home directory with all your data.

Good Luck,
CH

P.S.  If this works for the original poster, please make this thread as solved.

---

### Post by bayer789 on 2012-07-24
Hello y'all!

I do have an eTrex H and Ubuntu 12.04 running and I encounter exactly the same problem: I plug in the device and nothing happens. Now I found this entry und tried the workaround:
 - un-blacklist garmin gps
 - reboot
 - plug-in the eTrex
 - switch it on (nothing happens)
 - open console and type "sudo modprobe -r pl2303" and "sudo modprobe pl2303" (nothing happens)
 - open Gebabbel and try to download GPS tracks
 - Gebabbel can't find eTrex. Message "  p, li { white-space: pre-wrapFound no Garmin USB devices."

Does anybody have an idea how to fix this? Any help is very much appreciated.

---


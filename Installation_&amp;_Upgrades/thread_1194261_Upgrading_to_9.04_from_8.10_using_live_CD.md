---
title: "Upgrading to 9.04 from 8.10 using live CD"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by hashan17 on 2009-06-22
Guys I have a problem. I got a ubuntu 9.04 ship-it CD from a friend and i wanted to install it. I tried the method which was on [Ubuntu official website]("http://www.ubuntu.com/getubuntu/upgrading") and [COLOR="Red"]it didn't worked[/COLOR]d. :confused: (It's given below) 
I want to get installed the new version and any geek out there pls provide me assistance on this issue.


Thanks guys,

----------

[COLOR="Blue"]Upgrading Using the Alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.

      Download the alternate installation CD
   2.

      Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.
          *

            If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

            sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0

   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"

Or in Kubuntu run the following command using Alt+F2:

kdesudo "sh /cdrom/cdromupgrade"

----------------------------[/COLOR]

---

### Post by Mighty_Joe on 2009-06-22
> **hashan17 said:**
> [COLOR="Red"]it didn't worked[/COLOR]d. :confused: 


What didn't work?  Which step of the process?  Did you get an error message?
My wild guess is you failed at step one:
> **hashan17 said:**
> 
   1.      Download the alternate installation CD


The disks available from Ship-It are [the desktop or server install CD]("https://shipit.ubuntu.com/").  The "alternate install" is a [different product]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by Spaceman7o on 2009-06-22
a bit late but dont you just run update manager and select upgrade to 9.04 jaunty? thats what i did when i had wubi before partitioning. maybe you werent meant to install over an already installed ubuntu??

---

### Post by bubbhasdance on 2009-06-22
Yeah, try to update straight from the manager, you shouldn't need a live CD to update Ubuntu, who knows what could happen? *scary face laughing*

---

### Post by Aaron44126 on 2009-06-22
I've upgraded with the CD before.  *You do not use the Live CD.*  The instructions you posted say to use the alternate install CD (which is different than the Live CD).  You just insert the alternate CD while logged on to your Ubuntu install and you will be prompted to upgrade.

---

### Post by hashan17 on 2009-06-22
Yes I was using the Live CD for Desktops. I didn't use the alternate "install cd". The error was there were no option to upgrade. The only option there was is to do a clean install. 

So as you guys told, i have to upgrade either online or by the "alternate CD"... 
The internet connection i use is has limit for downloads (5GB Max per month). That's what bothers me ;-)

Well guys thanks for your kind help, and if you have further info about this issue pls post them.

---

### Post by Aaron44126 on 2009-06-25
If you have a limited monthly bandwidth, you should upgrade through the update manager, unless you need to update several machines.

This way, only updates to the packages you have installed will need to be downloaded.  This will probably save you some bandwidth.

If you use the alternate CD or DVD to upgrade, it still goes online to download the latest packages (for either packages you have installed but are not included on the disc, or for packages that have been updated since the disc image was made) --- so you might end up using extra bandwidth that way.

---

### Post by philcamlin on 2009-06-25
update manager is what ive used

---


---
title: "Install Ubuntu Server Sparc on Sun Ultra 5"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by rocketmanx on 2009-05-19
[SIZE=2]Hi,

I'm trying to install Ubuntu 9.04 server sparc on an Ultra 5 using the cdrom.

I downloaded the ubuntu-9.04-server-sparc.iso 
from: [http://cdimage.ubuntu.com/ports/releases/9.04/release/](http://cdimage.ubuntu.com/ports/releases/9.04/release/)
and verified the md5sum.

I burned the iso to a cdrom disc and verified the md5sum on the cdrom disc.

I enter the OBP during initialization by pressing the keys Stop A.
I boot with: boot cdrom
At the Welcome to Ubuntu jaunty! screen I start the install with: install
I select install language.
I select the country.
I select keyboard model: Sun Type 5 
I select keyboard origin: USA
I select keyboard layout: USA

Then the installer displays a banner with the message: Detecting hardware to find CD-ROM

Then a banner is displayed with the message: No common CD-ROM drive was detected.

The banner mentions that I can install drivers from removable media or I will be given the option to manually select CD-ROM modules. The banner provides these options:

Load CD-ROM driver from removable media? Yes   No

When I select No the install does not go any further. It does not give me the option to manually select CD-ROM modules. It installer hangs and continues to display this banner.

When I select Yes with a blank floppy in the drive the install searches the floppy for the cdrom drivers.

Can someone tell me where can I get/download the cdrom drivers to put on a floppy?
Are there any special instructions for installing the drivers on a floppy?


Thanks :)

Ken
[/SIZE]

---

### Post by rocketmanx on 2009-05-19
[quote=rocketmanx;7309530][SIZE=2]Hi,

I'm trying to install Ubuntu 9.04 server sparc on an Ultra 5 using the cdrom.

--------------

Is there an alternate solution for this Ultra 5 installation problem similar to this one for the Power PC?
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)


Thanks :)

Ken
[/SIZE]

---

### Post by forcefullpower on 2009-06-08
I am having the same issue. Where you able to find a resolution to the CDROM driver issue?

---

### Post by rocketmanx on 2009-06-08
I did not find the cdrom drivers.

What I did was download Ubuntu 6.06.2 server sparc LTS and burn it onto a cdrom. During install the cdrom drive was found and there were no problems with the install.

After the install from cdrom I downloaded and installed all the upgrades for this release. Then I installed the ubuntu-desktop (this step is optional). The server install and desktop are working good. Later I will upgrade to 8.04.1 server sparc LTS.

Once you have Ubuntu 6.06.2 server sparc LTS installed and all of the upgrades for this release installed, 
you can upgrade to the next release 8.04.1 server sparc LTS. If you are going to upgrade to 8.04.1 it may be easier to do so before before installing additional packages on 6.06.2 otherwise the upgrade may complain that it can not compute a solution for the upgrade and recommend that you remove non-standard packages.

Cheers,

Ken

---

### Post by rgururaj on 2009-06-18
I tried installing on Ultra 10 still says "No Common Cdrom drive detected".
I also tried doing modprobe. Nothing seems to detect the cdrom.
I do see "none and cdrom" after selecting cdrom it asks for a device file with /dev/cdrom which doesn't exist. Tried scanning all devices under /dev no success. Stuck with "No Common CDROM". 

Please someone help.

---

### Post by rgururaj on 2009-06-19
Thanks Ken, Installing 6.06.2 on ultra 10 worked. I detected the cdrom from /cdrom. Not sure why jaunty doesn't detect cdrom from /.

---

### Post by forcefullpower on 2009-06-21
Any chance they will fix the 9.04 so that it will detect the cdrom drive on ultra machines.

---


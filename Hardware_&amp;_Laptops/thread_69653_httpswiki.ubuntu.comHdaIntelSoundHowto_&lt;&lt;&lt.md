---
title: "https://wiki.ubuntu.com/HdaIntelSoundHowto &lt;&lt;&lt; WHO MADE THIS!!! need HELP"
date: 2005-09-27
forum: Hardware &amp; Laptops
---

### Post by narmenia on 2005-09-27
i followed everything... honest!!! :rolleyes: 
> Here are the steps:

(The # means you should do this as root, so either use the root-console or "$ sudo su -")

# apt-get install alsa-source

# apt-get install linux-headers-2.6.10-5-686

# apt-get install kernel-package ## installs make-kpkg

# apt-get install ncurses-dev ## I am not sure if this is really needed

$ less /usr/share/doc/alsa-source/README.Debian

# dpkg-reconfigure alsa-source ## choose azx as driver

# apt-get install fakeroot

# cd /usr/src

# tar jxf alsa-driver.tar.bz2

# cd linux-headers-2.6.10-5-686

# make-kpkg --rootcmd=fakeroot --append-to-version=-5-686 modules-image

# dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb 

the last COMMAND line gives me an error...
> root@ws09:/usr/src/linux-headers-2.6.10-5-686 # dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb
dpkg: error processing alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb

doing "cd /usr/src" before the last command gives also an error...
> root@ws09:/usr/src/linux-headers-2.6.10-5-686 # cd /usr/src
root@ws09:/usr/src # dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb

(Reading database ... 72343 files and directories currently installed.)
Preparing to replace alsa-modules-2.6.10-5-686 1.0.8-4ubuntu4+10.00.Custom (using alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb) ...
Unpacking replacement alsa-modules-2.6.10-5-686 ...
Setting up alsa-modules-2.6.10-5-686 (1.0.8-4ubuntu4+10.00.Custom) ...
FATAL: Could not open '/boot/System.map-2.6.10-5-686': No such file or directory
so i went to /boot and found out there was no System.map-2.6.10-5-686 only System.map-2.6.10-5-386...

DANG!!! LINUX IS SOOOOOOOO HARD!!! GRRRRRRRRRRR!!! :mad: 
no wonder people stick to windosed... imo :cool:

---

### Post by kelean on 2005-09-27
Please give us a little info.  What kind of computer, sound card, and what the exact problem is?  With the info someone should be better able to offer some help.

---

### Post by narmenia on 2005-09-27
intel d6915GAV

[http://www.intel.com/design/motherbd/av/](http://www.intel.com/design/motherbd/av/)

Celeron D 2.66
512MB RAM
80GIG HD
using on-board graphics and sound

Linux Ubuntu 5.04
sound is intel HD audio

current setup = no audio (almost a week now)
video is almost crap = only a few resolutions to choose from with stupid refresh rates (ex. 0 Hz, 86 Hz, 87 Hz)

1st im fixing my audio... next is the grapics... that is if i can fix my audio... :roll:

---

### Post by kelean on 2005-09-27
First thing to check is your /etc/modules file to see if your sound card is listed. 
That was my problem.  

Try this thread, it might help.  Search the fourms for sound problems.  Sorry I could not be more help.

---

### Post by kelean on 2005-09-27
Oops!! 
[http://www.ubuntuforums.org/showthread.php?t=21211&highlight=sound+problems](http://www.ubuntuforums.org/showthread.php?t=21211&highlight=sound+problems)

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---


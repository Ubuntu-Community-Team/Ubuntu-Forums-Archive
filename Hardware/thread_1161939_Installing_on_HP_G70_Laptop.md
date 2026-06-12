---
title: "Installing on HP G70 Laptop"
date: 2009-05-17
forum: Hardware
---

### Post by Majorflam on 2009-05-17
I am currently downloading the latest version of Ubuntu (9.04) and I intend to install on a HP G70-120EM Laptop. The laptop has Windows Vista Home Premium installed, and I will be setting up Ubuntu to dual boot.

Are there any known hardware issues?

If I changed my mind, could I just insert my HP recovery disks and go back to just a fresh install of Windows Vista?

Here is a full [system spec](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01602875&lc=en&dlc=fi&cc=fi&product=3826106&lang=fi)

TIA

---

### Post by jerrrys on 2009-05-17
why not just run the live cd without installing? see if it works for you...

---

### Post by Majorflam on 2009-05-17
Hi,

I'm running it now, and all seems fine. It's really the installation process that concerns me. Also, I need to know if my recovery disks would totally undo any changes.

---

### Post by jerrrys on 2009-05-17
ok...you got the live cd up and running, so i would say no hardware problems...i do not run recovery disk, but im guessing its not necessary...when you install ubuntu it will allocate disk space and should not mess with windows...however its always a good idea to have a backup...also you need to do a defrag and with vista there was something about restore points that is an issue...dont have the link, dont run vista...

found it...

[http://ubuntuforums.org/showthread.php?t=1149077](http://ubuntuforums.org/showthread.php?t=1149077)

---

### Post by Majorflam on 2009-05-17
OK, I've got the dual boot going and all looks well so far.

First major problem is that Ubuntu hasn't allocated itself enough disk space. I'm trying to apply an update but it says there is less than 110MB of space left. How can I allocate more space to the ubuntu filesystem?

---

### Post by jerrrys on 2009-05-17
hummm...that shouldnt be...how much disk space (total disk space) did ubuntu free up during install?

if your not sure, go to home folder, right click on any folder and go to  properties...is should tell you how much free space you have

---

### Post by Majorflam on 2009-05-17
> **jerrrys said:**
> hummm...that shouldnt be...how much disk space (total disk space) did ubuntu free up during install?

if your not sure, go to home folder, right click on any folder and go to  properties...is should tell you how much free space you have

Hi,

Ubuntu only allocated 3gb for itself. I have used Gparted and managed to extend the ubuntu partition to 20gb, which is fine... however, I seem to have lost 20gb of my total hard disk space. 

Windows is showing as having 120gb, and ubuntu has 20gb. My hard disk is 160gb!

Can anyone help me determine if my partition is OK?

TIA

---

### Post by jerrrys on 2009-05-17
ubuntu will create 4 partitions when installing...if you have just one 20gig partition, thats not right...

that missing 20gig is probably just unused space...

i would suggest looking at these before moving on...

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

[http://linuxplanet.com/linuxplanet/tutorials/3174/1/](http://linuxplanet.com/linuxplanet/tutorials/3174/1/)

[http://ubuntuforums.org/showthread.php?p=5004671#post5004671](http://ubuntuforums.org/showthread.php?p=5004671#post5004671)

---

### Post by Majorflam on 2009-05-17
Hey, everythings working fine after i upped the partition to 20gb. I think maybe I'm just not understanding the partition directory/tree properly.

Thanks for all your help dude, it's really appreciated.

---

### Post by jerrrys on 2009-05-17
):p

---

### Post by Majorflam on 2009-05-18
OK, I have a slight problem. I have my laptop hooked up to my LCD TV via the HDMI out port. However, When I set up the settings using the NVIDIA driver, it won't save the x configuration file. It's as if the file may be unwritable or something? It means I have to detect the display and set up the resolution every time I boot up, which is a real pain.

---


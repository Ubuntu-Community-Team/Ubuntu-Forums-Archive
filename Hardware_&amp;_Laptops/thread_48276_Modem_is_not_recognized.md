---
title: "Modem is not recognized"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by rebalde on 2005-07-11
OK, I'm as new to linux as one can possibly be.  I got the ubuntu cd's and installed 
them on a clean 20 gig HD.  Sound works, printer works, screen resolutions work, but the installer didn't recognize my "Broadxent" modem.  I searched through just about everything I could find in ubuntu, but I still have absolutely no idea how to either configure, or install or whatever you do for a modem in ubuntu linux.

I hate to ask for hand holding, but that is what I need.  I would be greatful for any help I can get.

rebel

---

### Post by jasmuz on 2005-07-11
[QUOTE=rebalde]OK, I'm as new to linux as one can possibly be.  I got the ubuntu cd's and installed 
them on a clean 20 gig HD.  Sound works, printer works, screen resolutions work, but the installer didn't recognize my "Broadxent" modem.  I searched through just about everything I could find in ubuntu, but I still have absolutely no idea how to either configure, or install or whatever you do for a modem in ubuntu linux.

I hate to ask for hand holding, but that is what I need.  I would be greatful for any help I can get.

rebel[/QUOTE]
 Head over to [www.linmodems.org](www.linmodems.org) to see if they have anything that might help your modem up.

---

### Post by az on 2005-07-12
[https://wiki.ubuntu.com/forum/hardware](https://wiki.ubuntu.com/forum/hardware)

Look under modem

---

### Post by rebalde on 2005-07-12
[QUOTE=jasmuz]Head over to [www.linmodems.org](www.linmodems.org) to see if they have anything that might help your modem up.[/QUOTE]

I had to download the scanModem.gz to a floppy.  Now my problem is I cannot find my floppy drive inorder to copy it to a directory and run it.

Helpfull info:
I got the cd's from ubuntu and installed Ubuntu on a clean 20 gig HD.  This was necessary because my windows HD MBR is already messed up with a copy of Sun Microsystems, JDS.  I have no idea how to edit Gurb to get rid of the JDS boot up, and no one at Sun Micro could tell me how to uninstall their dammed program without formatting my "C" drive and losing all my windows info..  So to go to ubuntu, I simply power down, unplug my windows HD, then plug in my Ubuntu HD. Takes a little more time, but it works and its clean.
 
So how do find my floppy and copy scanModem.gz to a linux directory. Also which is the best directory to copy it to.

rebel

---

### Post by az on 2005-07-12
Places - Computer- Floppy.

Drag and drop.

---

### Post by rebalde on 2005-07-14
[QUOTE=jasmuz]Head over to [www.linmodems.org](www.linmodems.org) to see if they have anything that might help your modem up.[/QUOTE]
 Thank you jasmuz for the link to linmodems.  I finally got scanModem.gz downloaded to a floppy.  I don't know if other newbies would have the same problem that I did, but I will mentioin it here and maybe it will save someone else some time and frustration.  When I downloaded the scanModem.gz to the floppy, the name was shortened to scanmo~1 and that is how it showed up in my desktop dir in Ubuntu.  well the linux command gunzip scanmo~1.gz  didn't produce any results.  Finally I found that I had to urn  "cp scanmo~1.gz scanModem.gz.  Then it did the unzip and I was able to run the " chmod +x scanModem" and then . /scanModem and obtain the needed files to email to linmodems.org.  I am now waiting an answer from them.   Thanks much.

rebel

---

### Post by rebalde on 2005-07-18
OK, once again I find myself chasing my tail in circles.

I swapped modems and this Diamond Super Max LE has two linux drivers on the accompaning CD.  They are in a .gz format.  I tried moving them into my "Desktop" dir from the CD where I could decompress them, but when I tried to drag and drop them into the desktop dir, I got an error saying I needed permission.  How do I get su permissions when working in the file mgr.  I can use the root terminal  but I'm unable to mnt the CD drive. Since I can't mnt the CD drive, I am unable to move them and therefore unable to decompress them.   I need some very basic help.

rebel

---


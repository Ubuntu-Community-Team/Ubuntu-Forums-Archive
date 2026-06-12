---
title: "New to Ubuntu, and first install has problems"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Apophisjon on 2009-10-17
Well, i finally got fed up with Windows and decided to switch to ubuntu. I put the version 9.04 Jaunty on a disc and popped it in my computer. it went into the screen where it asks you too install ubuntu and various other options. i chose install ubuntu, and sat there as it started up. to my surprise the screen displayed black then lots of white lines and blocks, as well as multi colored lines on the screen.

After the 2 seconds that was displayed, it went through another sequence (i assume it is initilizing or something) and then it rushes some quick lines of information at me all in white except one line has at the end FAIL in red, something to do with gnome(i think).

anyway, then it gets to a stereotypical welcome screen and  the mouse and keyboard is unresponsive, a counter logs me in under a generic acount (as i still have to install) and then two errors occur.

Initialization of Hal failed :internal error
&
indicator applet failed to initialize

i have no choice but to hold the power button down to shut off the computer because i cannot input anything via the keyboard of mouse.

i really want to have this fixed asap but i have no knowledge of unbuntu and only know how to troubleshoot a windows (which probably won't help me)


Do i have to change my hardware? (i hope not)
Do i need a new disc, perhaps its corrupt?
Do i need to give anymore information? (probably)

---

### Post by Apophisjon on 2009-10-17
Also im going to hit the hay, and will check back in morning. maybe there will be a reply...:confused:

---

### Post by .nedberg on 2009-10-17
> **Apophisjon said:**
> 

Do i have to change my hardware? (i hope not)

Probably not, but give some information of what you have it might indicate some cause of the problems

> **Apophisjon said:**
> 
Do i need a new disc, perhaps its corrupt?

This might indeed be the problem. At the first screen you can check the disk for defects. Try that. If it fails or shows errors, then download a new image and burn at low speed (4x).

> **Apophisjon said:**
> 
Do i need to give anymore information? (probably)
Information about your HW would be nice.

Also, a newer version of Ubuntu will be out in a couple of days (on October 29th). You might want to wait for that (a release candidate is due on October 22nd, if you feel adventurous).

---

### Post by Kevbert on 2009-10-17
Welcome to Ubuntu Linux.
What are your system specifications, in particular processor, RAM, video adapter ?
Have you downloaded the correct file for your PC (32 bit or 64 bit, hardware dependent) ?
Have you done a checksum on the downloaded ISO file ? See [this]("https://help.ubuntu.com/community/HowToMD5SUM"). If this is wrong you have got a corrupted download.
When you burn the CD, generally the slower the burn speed the better. Software for this is [here]("https://help.ubuntu.com/community/BurningIsoHowto").
Next, it's good to check the CD integrity as you may get burn errors. You can do this via the CD start menu.
Finally perform a memory test via memtest86+ in the CD start menu.
Good luck.

---

### Post by gsuccess on 2009-10-17
Am new to the ubuntu family. I got Ubuntu Cd mailed to me,but I still don't know how to install it.Can someone give a hint on the basic installation steps.:)

---

### Post by Kevbert on 2009-10-17
> **gsuccess said:**
> Am new to the ubuntu family. I got Ubuntu Cd mailed to me,but I still don't know how to install it.Can someone give a hint on the basic installation steps.:)

You need to be able to boot from CD. This may need to be set via the PC setup menu (by pressing F2) or something similar as the PC starts up. You should set the CD drive to be the first boot device.
You then need to run the CD on boot-up and check that your PC memory is OK via the CD memory test menu option (memtest86+) and then run the disk integrity check via the CD menu again (occasionally bad disks get through or damaged in the post).
The installation will ask you a load of questions on how you wish to install. Do you want to dual boot with Windows ?

---

### Post by tpjk on 2009-10-17
> **gsuccess said:**
> Am new to the ubuntu family. I got Ubuntu Cd mailed to me,but I still don't know how to install it.Can someone give a hint on the basic installation steps.:)

welcome to the forums - glad you asked;]

go here:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

that should get you started.

or, alternatively, if you want to set up a dual boot system, go here:

[http://members.iinet.net.au/~herman546/index.html]("http://members.iinet.net.au/%7Eherman546/index.html")
[http://gwos.org/udsf/doku.php/core:dualbooting:ubuntu](http://gwos.org/udsf/doku.php/core:dualbooting:ubuntu)

i also suggest you play around with your live cd a bit (if you haven't already) before actually installing ubuntu; that'll give you an idea of what you'll be dealing with and whether or not your hardware works 'out of the box' with ubuntu.

if you have any specific questions just open another thread.

cheers!

---


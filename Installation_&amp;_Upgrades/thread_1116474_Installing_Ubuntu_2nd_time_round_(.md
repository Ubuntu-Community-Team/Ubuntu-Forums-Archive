---
title: "Installing Ubuntu 2nd time round :("
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by tenpoundbear on 2009-04-04
My secondinstallatio n attempt at getting xp and ubuntu installed :(

Basically my plan is to have xp, install ubuntu (and get it working) and than install gentoo.

I have 3 SATA drives.

sda = contains my junk files... video, pitures, docs etc...
sdb = contains my xp
sdc = blank... I've partition this drive like this, sdc1 = swap, sdc2 = /boot, sdc3 = / (root), sdc4 = Future gentoo installation goes here.

BTW... what is the /boot parition used for? I thought that is where GRUB gets installed to?

The first time I installed... when I got to the last step I modified the setting for boot loader in the advance option.... its default was (hd0) I changed it to sdc2 because as you can see above that is where I have my boot partition.

After installation and restart I get the aweful error

Loading GRUB stage 1.5 Please wait....

Error 17


Or something like that... so here I am reinstalling it again.

Should I just leave it as the default setting, (hd0), this time? Where is (hd0)? Shouldn't I use the boot partition?

I don't want to loose xp cause I have stuff on it.

Ohh btw... the reason I wanted to have a separate boot partition is because I heard that GRUB will override xp MBR... I was worried that if I uninstall ubuntu than I wouldnt be able to boot xp again... hence why the boot partition seemed like a good thing to have... plus I want to have gentoo too down the track.

Thanks guys and sorry about the long post... and my inexperience.

---

### Post by Bakon Jarser on 2009-04-04
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

That link will help you solve your error.  The boot partition isn't really necessary although may come in handy when you install gentoo.  Your mbr will still be overwritten but can be restored later if you need to.  Any time you are messing with partitions or installing another os you should back up any important data.  Even if your not doing that you should keep a backup of important data.  Operating systems do occasionally have errors that require reinstallation.

---

### Post by tenpoundbear on 2009-04-04
Yeh I have actually read that thread...

Rather than messing around with stuff I thought I just do another installation.

Am I getting the error 17 due to changes I made to the boot loader option during installation time or will everyone just the get error 17 regardless and than have to go and do all those fiddly things mention in other thread after installation?

I rather do a new installation if I can.

Should I keep the default settings this time maybe, (hd0)?

Thanks for the help too :)

---

### Post by tenpoundbear on 2009-04-05
OK 2nd installation...
In the boot loader option I choose sdc and now Ubuntu boots :)

I can see the GRUB screen and and boot into Ubuntu.

Yay for me :)

P. S. Maybe someone can explain why this worked for me? So for newbies can understand linux better rather than just accept that it works.

Is it because of the way Ubunto starts to counts things at zero?

---


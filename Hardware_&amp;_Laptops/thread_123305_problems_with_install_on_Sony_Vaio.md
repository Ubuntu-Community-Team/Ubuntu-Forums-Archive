---
title: "problems with install on Sony Vaio"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by jonpartybody on 2006-01-29
Hey all,

I'm a newbie that tried installing Ubuntu on my Sony Vaio at the recommendation of a friend and ran into a few problems. The initial installtion went smoothly all the way up until the cd ejection and reboot, where the system hangs and cannot reboot itself. After a hard-reboot Ubuntu comes back up and attempts to continue the installation, however when I get to the "installing packages" portion of installation the system hangs with an error message:

[4294776.027000] ata1: BUG: timeout without command

I've tried installing it again and the same thing happened. Any help anyone could offer would be greatly appreciated.

Thank you in advance,

Jon

---

### Post by holr on 2006-02-03
I have the same issues too, running a sony vaio s570p here. I found the solution was to throw the ubuntu cd in the bin, and install fedora core 4 instead.

Seriously, I have tried so many distros, the only finished one that works is fedora core 4, debian testing works, but it is the testing stage.

---

### Post by linxi on 2006-02-16
I am having the same problem with my Vaio.

No idea how-to fix this.

Fedora Core 4 didn't install either.

---

### Post by holr on 2006-02-20
im suprised to hear that you were having troubles with fedora core 4, that one went on so easy for me. Im still having hair-pulling problems with ubuntu though. I have had better luck with the dapper drake one, but that crashes as soon as the x server is loaded. 

The only thing I had to do with fedora was hit i for interactive boot mode and disable the pcmcia from working. There is a hack around this though, to get it working again.

---

### Post by linxi on 2006-02-21
It just hang-up when it started to copy files.

Same error as in Ubuntu.

I think this is some small adjustment to hdd-driver cause it can partition the hdd and even copy files to it (in ubuntu).

I am using Sony Vaio S5H

---

### Post by kniteshade on 2006-03-04
I have a brand new VGN-S58GP with the exact same problem (twas purchased for the sole purpose of running linux on it - so I hope theres a solution)

When i tried to install Hoary it would lock up in the 'starting pc card services' section of the hardware detect stage.

---

### Post by kniteshade on 2006-03-06
After having spent most of today at work watching various ubuntu installs on this laptop (its okay, i had some wet paint to watch to keep myself interested) i managed to get 5.04 Hoary to work.
 
Breezy gives the ata1 error.

The latests beta release of Dapper kernel panics at about the same spot as breezy breaks - no amount of kernel options make them work either (noapic, nolapic, pci=noacpi etc)

Hoary does work on this laptop (Sony Vaio VGN-S58GP). I had to turn of pcmcia detection (Press <F3> at the install first screen for the option) which would usually cause the auto hardware detect to fail - and it installed fine after that.

Hope this helps some others out


Hopefully this SATA stuff is all fixed when Dapper is finally released - dont like the idea of having to run Hoary forever

---

### Post by glenndavy on 2006-03-06
Hey all - just hoping on the band wagon to say that my new friend an companion the, gorgeous vaoi TX17GP - has the same problem. 

Whats odd though is this is the second time I've installed it -the first time, it was fine.

---

### Post by dodgeman79 on 2006-03-06
I have Badger on a PCG-GRS100 that works great short of trying to get the ATI drivers to work.  I don't play games but just want to install the drivers to have them.

I just put in a new HD after the original one crashed, and put in XP then Badger.  No problems with dual boot either with GRUB.  this is my first attempt at something linux but not my first exposure to it.  i can try to help if I can

---

### Post by cyfdecyf on 2006-03-10
[COLOR="Blue"][/COLOR]I've got the same error message while installing Breezy on my friends vaio. (It's a VGN-S58CP/B.) It happens after the first reboot when the installation continues to install the packages. And when powered down and reboot again it displays those message when it begin to fsck the file system.

ata1: error occurred port reset
ata1: BUG: timeout without command

After that I tried to use the liveCD to boot into the system and fsck the partion so that the file system is clean and then successfully mounted the partion. I also tried to create some file in the partion and also succeeded. 

[COLOR="blue"]So it seems that when using the liveCD everything goes well, including the SATA hard driver. [/COLOR](Am I right?) And then I began to think whether we can do something with the liveCD to set up the system? For example, use chroot to enter the system and then continue the installation. Or change some settings so that the system can boot up and continue the installation correctly.

This is just my thought and it maybe wrong. I really hope I can set up the system and in fact I've been searching help for about a week.
Really need help...

---

### Post by mattoman on 2006-03-11
Hi All, Dapper runs great on my VGN-S560P

Minor Problems do exist:

1.) fnkey+f3,f4 is volume control, sure their is OSD action, but it doesn't actually change the volume

2.)fnkey+f5,f6 is the change the contrast, no dice.

If any of you have like problems, including hibernations problems, check out this thread, and its containing links, no luck for my self yet, if anyone has any ideas... i'm open for them.

[http://www.ubuntuforums.org/showthread.php?t=88611](http://www.ubuntuforums.org/showthread.php?t=88611)

Matt

---

### Post by et_the_beta_tester97 on 2006-03-11
Get a different laptop dude..sony vio's are S***. 

some other possible causes are:
Scratch in the cd
CD not communicating properly with computer
hardware malfunctioning

---

### Post by et_the_beta_tester97 on 2006-03-11
dude..get a different laptop..sony viao's are s***.

some other possible causes:
CD not communicating wiht the computer properly
scratch in cd
hardware malfunctioning.

---

### Post by et_the_beta_tester97 on 2006-03-11
Dude, get a different laptop..sony viao's are s*** :mad: 

some other possible cuases:
CD not communicating properly wiht the computer
Hardware malfunctioning
scratch in cd

---cj

---

### Post by NikoC on 2006-03-13
I have to make a small remark on those last 3 (identical) posts: as for me I have a Vaio S4HP and it does not suck at all, it just doesn't work well with linux and Sony is to blame for that! They don't release drivers or give support to linux users, the hardware however in my machine is excellent and works like a charm with an OS which name i'm not goin' to mention here! ;)

---


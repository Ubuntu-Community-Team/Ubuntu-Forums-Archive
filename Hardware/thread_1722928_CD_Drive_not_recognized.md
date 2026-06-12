---
title: "CD Drive not recognized"
date: 2011-04-06
forum: Hardware
---

### Post by complicatedbreathing on 2011-04-06
Hi,
Sorry if this is already posted or if I'm posting in the wrong category, but I think I'm in the right place.
Total Newbie to Ubuntu, just installed 10.10 maybe a month ago and everything has been fine except that my laptop will not recognize my cd drive. I put a CD in and it spins around for a couple seconds and then stops, but nothing happens on my computer. Nothing shows up under my 'Places' tab at the top, nothing shows in the main computer window besides my internal file system and external hard drive. Rhythmbox and Movie Player don't recognize anything in my cd drive, and I'm fairly sure it's not just a problem of me not using the correct application to play a dvd or cd. I think the problem is that my cd drive is just not being recognized for some reason.
Tried using the terminal to mount the drive and got mount: can't find /media/cdrom in /etc/fstab or /etc/mtab - Not sure what that means or if it helps at all, but figured it couldn't hurt. 

Please help me out if you've got any suggestions at all, or if I need to give more information please let me know. Thanks!
-cb

---

### Post by complicatedbreathing on 2011-04-24
Okay guys, I see I've got 50 views but no answers... no one's run across this problem before? Seriously? I really need your help, ubuntu community! Can you at least tell me where i can find more information about these kinds of problems? 
Any help is appreciated!!

thanks,
-cb

---

### Post by KegHead on 2011-04-24
Hi!

You mentioned you installed about a month ago.

Have you run an update since then?

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

Advise.

KegHead

---

### Post by complicatedbreathing on 2011-04-26
Thank you, KegHead. I ran the updates as you suggested and am not seeing anything different. Is there anything else I can run or do to try to fix this?

-cb

---

### Post by KegHead on 2011-04-26
Hi!

I think this might work;

mkdir /media
mkdir /media/cdrom
mount /dev/cdrom /media/cdrom

[COLOR="Red"]Can one of the more senior folks look at this before it's used?[/COLOR]

Just being sure!

KegHead

---

### Post by zozza on 2011-04-26
I appear to have an identical problem: [http://ubuntuforums.org/showthread.php?t=1739782 ]("http://ubuntuforums.org/showthread.php?t=1739782")

Can the OP try inserting a CD then type dmesg and paste the output.



Also I have read that one solution is to add all_generic_ide=1 to  /etc/defaults/grub then update-grub.  I did this and rebooted but obtain  the same errors. 

When I did this I just typed all_generic_ide=1.  It was not preceded by anything - should it have been?

---


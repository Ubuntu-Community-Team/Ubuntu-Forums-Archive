---
title: "I need to burn an ISO and make it bootable"
date: 2008-11-12
forum: General Help
---

### Post by Mecharuva on 2008-11-12
Should I use growisofs?
I was thinking the command would be:
```
growisofs -Z /dev/cdrom -speed=4
```
Just in case you need to know, it's a WinXP iso file.
I had Nero on CD somewhere but it's gone without a trace now.
Any help is much appreciated.

---

### Post by phidia on 2008-11-12
Check out "man wodim". wodim is the commandline burning tool.
You probably want one of the -raw options with that.

---

### Post by SuperSonic4 on 2008-11-12
graphical programs would be k3b or brasero. Double click and burn

---

### Post by Shwefty on 2008-11-12
I hope I'm not misunderstanding the issue here.

All I had to do, in 8.10, is right click on the .iso, and click "Write to Disc".  Then I chose the lowest write speed.

Apologies if this is a tad simplistic.

By the way, this is bootable too.  This is how I created my Live CD for a reinstall of 8.10 (from 8.10...I was having some nasty issues).

---

### Post by Mecharuva on 2008-11-12
Wodim doesn't want to work for me :/
Says "Trying to use high-speed medium on low-speed writer" and quits.
I know this isn't a low-speed drive.  It's not even a year old.

-edit-
None of the graphical writing programs I have will work.
They all quit with an error.
I have an NRG file that I got the ISO from, but I have yet to find something other than Nero that can burn it, and I can't find my Nero installer CD anywhere...

---

### Post by taurus on 2008-11-12
How did you convert the .nrg to .iso?  See if you can mount it first.

```
sudo mkdir /media/iso
sudo mount -t iso9660 filename.iso /media/iso -o loop
ls -la /media/iso
```
And if you want to unmount it, just run

```
sudo umount /media/iso
```

---

### Post by Mecharuva on 2008-11-12
Here's what I get for the mount and ls, taurus:
```
root@ubuntu:~# ls -la /media/iso
total 1662
dr-xr-xr-x 1 root root     564 2004-08-04 08:00 .
drwxr-xr-x 5 root root    4096 2008-11-12 20:11 ..
-r-xr-xr-x 1 root root     110 2004-08-04 08:00 autorun.inf
dr-xr-xr-x 1 root root     124 2004-08-04 08:00 docs
dr-xr-xr-x 1 root root    1574 2004-08-04 08:00 dotnetfx
dr-xr-xr-x 1 root root  255818 2004-08-04 08:00 i386
-r-xr-xr-x 1 root root   34301 2004-08-04 08:00 readme.htm
-r-xr-xr-x 1 root root 1314816 2004-08-04 08:00 setup.exe
-r-xr-xr-x 1 root root   85792 2004-08-04 08:00 setupxp.htm
dr-xr-xr-x 1 root root     106 2004-08-04 08:00 support
dr-xr-xr-x 1 root root     238 2004-08-04 08:00 valueadd
-r-xr-xr-x 1 root root      10 2004-08-04 08:00 win51
-r-xr-xr-x 1 root root      10 2004-08-04 08:00 win51ip
-r-xr-xr-x 1 root root      10 2004-08-04 08:00 win51ip.sp2

```
Looks alright to me...

---

### Post by taurus on 2008-11-12
How did you convert .nrg to .iso?  Did you use nrg2iso?

---

### Post by Mecharuva on 2008-11-12
No, apparently this guy found out that NRG2ISO just cuts off the first 300KB of data or something, and then re-tags it .iso.  (apparently he found it in the source code).
Then he pasted down a terminal command to convert it to ISO so I ran that and it worked.
A lot of people said it worked for them too.
It worked for me, but it won't burn for some reason...

---

### Post by phidia on 2008-11-12
You may need to use genisoimage (man genisoimage) that command is referenced from man wodim too.

---

### Post by RobOrr on 2008-11-12
I use Brasero for iso burning and AcetoneISO2 for conversion stuff, as well as mounting ISOs. It's a lot easier if you don't want to remember terminal commands, and with all the other stuff it can do its my main goto program for DVD stuff, like ripping to avi etc.

---

### Post by Mecharuva on 2008-11-14
Alright well I still haven't managed to burn this disc (or find my Nero disc...)
But I got KDE4 and I have K3b now.
I tried using "Burn CD Image" and it worked, but the disc won't boot...
Am I doing something wrong..?
I know my PC will boot from discs still, that's how I ended up with a bad WinXP in the first place.

---

### Post by taurus on 2008-11-14
To make sure the disc is burnt right, can you try to boot from your new Ubuntu CD from another computer?  If another computer is able to boot from that CD, then there is something wrong with your computer.  But if the other computer still can't boot from the CD, then chances are there is something wrong with the CD or burn.

---

### Post by Mecharuva on 2008-11-14
I don't have an Ubuntu CD.  This is a Wubi install...
But I know it can boot, I have another bootable WinXP CD, but it's pirated...
I have a legit file now, but I can't use it yet.

---


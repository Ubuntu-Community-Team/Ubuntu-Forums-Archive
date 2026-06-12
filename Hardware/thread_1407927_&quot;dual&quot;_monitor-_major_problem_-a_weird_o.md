---
title: "&quot;dual&quot; monitor- major problem -a weird one"
date: 2010-02-15
forum: Hardware
---

### Post by acornbrain on 2010-02-15
Hi there, here's a strange one for you:
 
I am using an old (almost junk) Dell Latitude laptop with a busted screen. (No picture at all on laptop screen)...in order to see anything, I have an old monitor hooked up to the laptop...and so I've been using this external monitor as my main viewing screen. I've been running Ubuntu Jaunty in this manner for months, and everything was working fine...
 
...Until yesterday when the external monitor stopped working- no display at all. I boot the laptop, I can tell Ubuntu is trying to load, but no signal reaches the external monitor. And since the laptop's own display is also broken, I don't really have any idea what Ubuntu is trying to display.
 
I popped in the Live CD, and I got it to boot from the CD, and the monitor worked again! Removed the CD, tried to boot from hard drive...nothing again.
 
What's going on here? And will I be able to fix this using the Live CD, since that is the only way I am going to be able to use the laptop until I do fix it.
 
In case this is a clue, I was also having problems with Add/Remove yesterday, just BEFORE the monitor crashed:
 
[http://ubuntuforums.org/showthread.php?t=1406986](http://ubuntuforums.org/showthread.php?t=1406986)
 
Argh
 
-Brian

---

### Post by zeroseven0183 on 2010-02-15
Hi! Please use the LiveCD, boot from it and open a Terminal. Now, type the command below to recreate the deleted partial folder: ```
mkdir /var/cache/apt/archives/partial
``` 

When you type, ```
cd /var/cache/apt/archives
```
You'll see there the .debs you used to install applications.

Then run to delete ```
sudo apt-get clean
```

You may check first what's in the archives folder by typing ```
ls
```

Type again ls after sudo apt-get clean and see if it deletes the files.

Note: I posted the same instruction on your other thread.

Let us know what happens.

---

### Post by acornbrain on 2010-02-15
thank you, Zeroseven, I will try this and let you know.
 
Do you think this will also sove my monitor problem, though?
 
-brian

---

### Post by acornbrain on 2010-02-15
OK, 
 
I couldn't mkdir because it said the file already exists.
 
when I cd to the folder and ls I get: "lock partial"
 
nothing happens when I sudo apt-get clean. (ls afterwards, and still says "lock partial")
 
Also, not sure this is doing anything about my display problem.
 
-brian

---

### Post by acornbrain on 2010-02-15
more "clues" regarding the display problem:
 
neither ctrl-alt-f1 nor ctrl-alt-f7 have any effect.
 
I am hoping there is some combination of keystrokes that will bring back the display, because I'm basically flying blind. Or perhaps a solution can be achieved using the Live CD, which seems to work fine.

---

### Post by acornbrain on 2010-02-17
here is some of my flailing about trying to fix this situation:
this is me booting liveCD than mounting my hard drive, and switching to it's root. trying to get apt-get to upgrade/clean/update etc, blocked at every turn...

```
cubuntu@ubuntu:~$ sudo chroot /media/disk
root@ubuntu:/# apt-get update
E: Archive directory /var/cache/apt/archives/partial is missing.
root@ubuntu:/# mkdir /var/cache/apt/archives/partial
mkdir: cannot create directory `/var/cache/apt/archives/partial': Input/output error
root@ubuntu:/# rm /var/cache/apt/archives/partial
rm: cannot remove `/var/cache/apt/archives/partial': Input/output error
root@ubuntu:/# cd /var/cache/apt
root@ubuntu:/var/cache/apt# ls
apt-file  archives  partial  pkgcache.bin  srcpkgcache.bin
root@ubuntu:/var/cache/apt# cd archives
bash: cd: archives: Input/output error
root@ubuntu:/var/cache/apt# cd/var/cache/apt/archives
bash: cd/var/cache/apt/archives: No such file or directory
root@ubuntu:/var/cache/apt# mkdir archives
mkdir: cannot create directory `archives': Input/output error
root@ubuntu:/var/cache/apt# apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (5 Input/output error)
E: Unable to lock the download directory
root@ubuntu:/var/cache/apt# apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (5 Input/output error)
E: Unable to lock the download directory
root@ubuntu:/var/cache/apt# mkdir -p /var/cache/apt/archives/partial
mkdir: cannot create directory `/var/cache/apt/archives': Input/output error
root@ubuntu:/var/cache/apt# cd /var/cache/apt/archives
bash: cd: /var/cache/apt/archives: Input/output error
root@ubuntu:/var/cache/apt# mkdir /var/cache/apt/archives
mkdir: cannot create directory `/var/cache/apt/archives': Input/output error
root@ubuntu:/var/cache/apt# pkill synaptic
Cannot find /proc/version - is /proc mounted?
root@ubuntu:/var/cache/apt# apt-get update
E: Archive directory /var/cache/apt/archives/partial is missing.
root@ubuntu:/var/cache/apt# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/var/cache/apt# apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (5 Input/output error)
E: Unable to lock the download directory
root@ubuntu:/var/cache/apt# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/var/cache/apt# apt-get update
E: Archive directory /var/cache/apt/archives/partial is missing.
root@ubuntu:/var/cache/apt# cd /var/cache/apt/archives
bash: cd: /var/cache/apt/archives: Input/output error
root@ubuntu:/var/cache/apt# ls
apt-file  archives  partial  pkgcache.bin  srcpkgcache.bin
root@ubuntu:/var/cache/apt# cd var/cache/apt/partial
bash: cd: var/cache/apt/partial: No such file or directory
root@ubuntu:/var/cache/apt# cd var/cache/apt/archives
bash: cd: var/cache/apt/archives: No such file or directory
root@ubuntu:/var/cache/apt# mkdir archives
mkdir: cannot create directory `archives': Input/output error
root@ubuntu:/var/cache/apt# rm /var/cache/apt/archives/lock
rm: cannot remove `/var/cache/apt/archives/lock': Input/output error
root@ubuntu:/var/cache/apt# 
```

still researching online, but so far I have not found anyone with the exact same problem as me, so none of their solutions are working...

-brian

---

### Post by Sef on 2010-02-17
Locked.  Continued [here]("http://ubuntuforums.org/showthread.php?t=1409640").

---


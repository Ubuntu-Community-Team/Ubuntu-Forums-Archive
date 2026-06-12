---
title: "Is hard drive causing ubuntu to freeze"
date: 2011-02-02
forum: Hardware
---

### Post by Mechanimal on 2011-02-02
So, as the thread title states, my system is freezing. I had no issues with my other hard drive running Ubuntu, and wanted to use a larger drive. Anyway, I've tried installing several debian/ubuntu distributions, and freezes occur while transferring data, or installing updates. It seems to not freeze ever while idling for long, but any transfers will cause it. I am pretty certain it's a hardware issue, but I want to figure out if it's my hard drive, or anything else doing it.

If anyone could help me figure out how to diagnose the problems; either which log files to check, or any applications that can do thorough hard drive stability tests, or other similar things.

Thanks for any help.

---

### Post by JayKay3OOO on 2011-02-02
Simple Answer: Put the old drive back in and transfer some large files. If it freezes then you will know it's the new drive.

---

### Post by Mechanimal on 2011-02-02
> **JayKay3OOO said:**
> Simple Answer: Put the old drive back in and transfer some large files. If it freezes then you will know it's the new drive.Both drives are still in, as I have an older Ubuntu version on the old one, and that still transfers fine, showing no freezing.

I just want to find a way to confirm 100% that it's the hard drive

---

### Post by IWantFroyo on 2011-02-02
Computer specs please?
I'm going to assume the computer isn't new.
I see this a lot with some old computers in the house. I'd recommend a variation of Ubuntu that doesn't use the GNOME desktop. It's resource heavy, and computers run faster without it.
Try glxgears in terminal or Desktop Cube+Desktop Rotate+Internal Gears with second transparency slider at 0 in Desktop cube. If it doesn't work, its your graphics card.

---

### Post by Mechanimal on 2011-02-02
> **IWantFroyo said:**
> Computer specs please?
I'm going to assume the computer isn't new.
I see this a lot with some old computers in the house. I'd recommend a variation of Ubuntu that doesn't use the GNOME desktop. It's resource heavy, and computers run faster without it.
Try glxgears in terminal or Desktop Cube+Desktop Rotate+Internal Gears with second transparency slider at 0 in Desktop cube. If it doesn't work, its your graphics card.glxgears showed me 375 frames in 5 seconds = 74-75 FPS, while desktop cube and other settings moved flawlessly. So, I'm guessing that it's not a graphical issue.

EDIT: PC is not new, most definitely: 

If you need more info, I can open it up...
Board: Asus A7V8X-X
CPU: AMD 1.7GHz (I think it's Athlon)
Memory: 512 MB DDR 400 (PC3200), or it may be DDR333(PC2700)
Video: Radeon 9000 128MB
Hard Disk (one that this is on) Western Digital Caviar (IDE) 160GB

I feel like I'm missing something...hrmmm

---

### Post by JayKay3OOO on 2011-02-02
Well - 'Disk utility' in gnome will give you the SMART data on the drive (basically the drives own self check) to tell you if it's functioning ok. If all the smart data comes back ok then we'll have to think of something else.

---

### Post by Mechanimal on 2011-02-02
> **JayKay3OOO said:**
> Well - 'Disk utility' in gnome will give you the SMART data on the drive (basically the drives own self check) to tell you if it's functioning ok. If all the smart data comes back ok then we'll have to think of something else.I did that disk utility long test, and it gave me no errors. 

I'm at a loss for what could actually be causing the problem.

EDIT: Everything on this drive has been using the ext4 filesystem. I don't suppose that could be the culprit? Also, after checking some log files, I couldn't find anything that was logged around the time of the crash. I checked: 
/var/log/messages
/var/log/syslog
/var/log/daemon.log

I did a transfer, and checked the exact seconds, so I could check logs for what happened around then, but I couldn't find it in the few log files I checked. Maybe there's somewhere else?

---

### Post by Mechanimal on 2011-02-03
It took a while, and loads of troubleshooting, but I found my problem. 

I decided ctrl-alt-f1 to go to the prompt, and see if it gave me info on errors while transferring, and what came up was:

BUG: soft lockup - CPU#0 stuck for 61s [ntos_wq:651] and a whole load of hex before and after.

I looked it all up, naturally, and came across reference to ndiswrapper. It clicked there, because it all happened after my wireless windows driver was installed. I took it out, uninstalled the inf file, and plugged in another wireless adapter that had native linux drivers, and it worked off the bat, updating, transferring, and everything else.

I'm thinking maybe wireless support was lost after a certain kernel. Either way, I'm going to stick to the other wireless adapter.

Also, is this the kind of thing that I should post a bug report for?

---

### Post by matt_symes on 2011-02-03
Hi

Check to see if a bug report has been raised for it in launchpad. If not raise one with your spec's and logs and as much detail as possible etc. If one has been raised you can confirm it.

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Nice work BTW tracking that down.

Kind regards

---

### Post by daniel-strae on 2011-05-03
Hi all!

Sorry to raise this thread, but i guess i have the same problem.

My office pc used to work great til yesteday, but today it freeze every application as soon as i do something relevant with the disk.
While the freezes occour, my cpu's looks like arent used, they are both under 10% oof work.

Im running Lucid 10.04.02, and the apt history show only those updates yesterday:
```

Start-Date: 2011-05-02  09:22:51
Upgrade: ubufox (0.9~rc2-0ubuntu11~mfs~lucid1, 0.9-0ubuntu1~mfs~lucid1), php5 (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), python-dockmanager (0.1.1~bzr91-0~10.04~dockers1, 0.1.1~bzr94-0~10.04~dockers1), firefox-globalmenu (4.0+nobinonly-0ubuntu1~mfs~lucid1, 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1), libapache2-mod-php5 (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), php5-gd (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), firefox-branding (4.0+nobinonly-0ubuntu1~mfs~lucid1, 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1), firefox (4.0+nobinonly-0ubuntu1~mfs~lucid1, 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1), xulrunner-1.9.2 (1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1, 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1), xul-ext-ubufox (0.9~rc2-0ubuntu11~mfs~lucid1, 0.9-0ubuntu1~mfs~lucid1), dockmanager (0.1.1~bzr91-0~10.04~dockers1, 0.1.1~bzr94-0~10.04~dockers1), ubuntu-tweak (0.5.10-1~maverick1, 0.5.12-1~lucid1), php5-mysql (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), php5-cli (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), php5-common (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), firefox-gnome-support (4.0+nobinonly-0ubuntu1~mfs~lucid1, 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1)
End-Date: 2011-05-02  09:23:36

```I was using 2.6.38 kernel, i tryed to switch back to 2.6.32, but nothing change...

I've done smart test on the disk, even with GSmart from a live cd, but the disk looks ok.
Now im running memtest, to avoid the doubt that the problem is the ram.. but i know it is not.

Any idea?
[]("http://ubuntuforums.org/member.php?u=521392")
Mechanimal, what command did you use to show the error in the tty?

---

### Post by Mechanimal on 2011-05-03
> **daniel-strae said:**
> Hi all!

Sorry to raise this thread, but i guess i have the same problem.

My office pc used to work great til yesteday, but today it freeze every application as soon as i do something relevant with the disk.
While the freezes occour, my cpu's looks like arent used, they are both under 10% oof work.

Im running Lucid 10.04.02, and the apt history show only those updates yesterday:
```

Start-Date: 2011-05-02  09:22:51
Upgrade: ubufox (0.9~rc2-0ubuntu11~mfs~lucid1, 0.9-0ubuntu1~mfs~lucid1), php5 (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), python-dockmanager (0.1.1~bzr91-0~10.04~dockers1, 0.1.1~bzr94-0~10.04~dockers1), firefox-globalmenu (4.0+nobinonly-0ubuntu1~mfs~lucid1, 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1), libapache2-mod-php5 (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), php5-gd (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), firefox-branding (4.0+nobinonly-0ubuntu1~mfs~lucid1, 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1), firefox (4.0+nobinonly-0ubuntu1~mfs~lucid1, 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1), xulrunner-1.9.2 (1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1, 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1), xul-ext-ubufox (0.9~rc2-0ubuntu11~mfs~lucid1, 0.9-0ubuntu1~mfs~lucid1), dockmanager (0.1.1~bzr91-0~10.04~dockers1, 0.1.1~bzr94-0~10.04~dockers1), ubuntu-tweak (0.5.10-1~maverick1, 0.5.12-1~lucid1), php5-mysql (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), php5-cli (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), php5-common (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), firefox-gnome-support (4.0+nobinonly-0ubuntu1~mfs~lucid1, 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1)
End-Date: 2011-05-02  09:23:36

```I was using 2.6.38 kernel, i tryed to switch back to 2.6.32, but nothing change...

I've done smart test on the disk, even with GSmart from a live cd, but the disk looks ok.
Now im running memtest, to avoid the doubt that the problem is the ram.. but i know it is not.

Any idea?I forgot to mention that I fixed this issue completely, but my issue was with windows drivers with ndiswrapper, and not playing nice with the new kernel. I would recommend starting your own thread.

---

### Post by hubertofliege on 2013-02-06
I have a similar problem: my computer freezes when I try to transfer files from a hard drive.  Its an ASUS laptop running 12.10.

I didn't understand the solution.

A) How did you trouble shoot this.  I've looked at my system log, but its gibberish to me.  What am I looking for?

B) How can I determine if I have a problem with ndiswrapper?

Thanks.

---


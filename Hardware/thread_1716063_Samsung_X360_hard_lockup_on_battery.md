---
title: "Samsung X360 hard lockup on battery"
date: 2011-03-27
forum: Hardware
---

### Post by cavilling_elite on 2011-03-27
I have what seems to be a power management issue. Whenever I am on battery my computer will lock up HARD. I think it is part of a power management in the kernel, but I do not  currently know how to debug the kernel once it locks up this bad.

I first thought it had to do with the hard drive shutting / spinning down. When I had a regular HD I set the spin down to 0. I have since bought a SSD, but it hasn't stopped. 

If I can guess what it coincides with I would say that every time the power reaches 20 minutes or some "warning" limit it would lockup. Since 10.10 it seems to lock up all the time. (ironically it locked up while i was on battery writing this :( ) 

If I can, I'd like to walk through a way to debug what is going on here and hopefully help find the snag with this issues. 

I am an advanced user.

---

### Post by cavilling_elite on 2011-04-10
watching:

/var/log/dmesg
/var/log/syslog
/var/log/daemon.log
/var/log/kern.log

give no output post or pre lockup. I have run watchdogd but it doesn't reboot after 60 seconds. SO I would classify this as a hard lockup.

Any kind of help would be wonderful. I would argue that it "lasts" longer if it isn't doing anything. And has more probability of lockup when doing stuff like running Inkscape (3 minutes) browsing the web (15 minutes) -- all approximated. 

I have used `bum` to remove all power daemons. But I don't suspect it will help. Really trying to isolate this problem.

---

### Post by cavilling_elite on 2011-04-10
I should mention, it isn't Ubuntu specific. But it IS linux specific. And I am running the kernel in debug mode by adding "debug" to grub file.

---

### Post by cavilling_elite on 2011-04-10
I have installed the Boot Up Manager (pkg: bum) and removed all instances of power management. My computer has been up and running for 2 hours without issue.

---

### Post by cavilling_elite on 2011-04-10
After running without issues for 2.5 hours, closing the lid and letting it suspend, opening the lid and after a few minutes it locked up. 

After reboot it locked up right away. Once I plugged the power in, no problem.

I'd really like to be directed to some decent howto's for kernel debugging and perhaps even Xorg debugging. 

My suspicion is it is in the power management code.

---

### Post by cavilling_elite on 2011-04-10
Interestingly enough, there seems to be the same problem with Windows machines using Windows7 and Vista.

[http://forum.notebookreview.com/samsung/436440-x360-34p-freeze-up-randomly-please-help-if-you-owner-samsung-x360.html](http://forum.notebookreview.com/samsung/436440-x360-34p-freeze-up-randomly-please-help-if-you-owner-samsung-x360.html)

[http://forums.techarena.in/portable-devices/1363076.htm](http://forums.techarena.in/portable-devices/1363076.htm)

Some insight: 
"I think the problem I had on my E6400 was fixed when I changed a setting  for write combing in the graphics driver. However, I can't find where  that setting is."

---

### Post by cavilling_elite on 2011-04-10
Found this: Trying now

>  					Originally Posted by **sobachkin** 					[[IMG]http://forum.notebookreview.com/images/Notebook/buttons/viewpost.gif[/IMG]]("http://forum.notebookreview.com/samsung/436440-x360-34p-freeze-up-randomly-please-help-if-you-owner-samsung-x360-4.html#post6592246") 				
 				Russian guys at ixbt.com found  interesting way to resolve it  - ????? some questions but i think after  the half of year without any work on battery - this method may be brings  a hope...
-switch on in BIOS - **EDB (Executive Disable Bit**) **to Enable **
-switch on in BIOS - **Low Power Mode** **to Enable**
trying......  
BIOS version 09LM
[http://forum.ixbt.com/post.cgi?id=attach:17:34019:662:1](http://forum.ixbt.com/post.cgi?id=attach:17:34019:662:1)
Additionaly - guys think that always depend from wrong battery...


---

### Post by chaplincap on 2011-04-10
Yes my Samsung x360 does exactly what is described above: lockup after a period of use, particularly during more demanding tasks. I am running Vista myself but I would like to know more about this issue, as it seems not to be connected to a specific OS.
By the way, one cannot change the write combing in the graphics driver in Vista.

---

### Post by washakie on 2011-04-11
I had the same problem, eventually had to give up, since the computer was old enough to justify getting a new one at work. Here is a bug report on a similar problem, but I do think my problem was specific to the X360. Does your screen flicker like mad when it locks up?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659705](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659705)

---

### Post by cavilling_elite on 2011-04-11
My screen doesn't flicker...

I have just successfully gone without locking up completely through the battery.

The solution seems to be a BIOS thing:

> 
-switch on in BIOS - **EDB (Executive Disable Bit**) **to Enable **
-switch on in BIOS - **Low Power Mode** **to Enable**


I do not understand it, but everything works. I put back on all of the power management daemons and it still runs just fine.

---


---
title: "Battery discharging popup and draining battery"
date: 2011-08-02
forum: Hardware
---

### Post by baboo on 2011-08-02
I am using 10.04 lts 64 bit. My battery status is always battery is discharging even when plugged into ac. If I run on battery it drains very quickly. 

1. I have never had this problem with Ubuntu until I did an update.
2. I have searched the forum for same problem but none of the proposed solutions have worked.
3. The battery discharging popup is constantly poping up.

any help out there? 
 
thanks

---

### Post by omelette on 2011-08-02
Any chance the update/battery problem is a coincidence?  It sounds like you have a hardware problem to me.  If the battery is physically discharging with the AC adapter plugged in - ie. not just a s/w glitch - then you must have a h/w problem.  I have a laptop as well (with Fedora14 though) and twice have had it stop charging.  The problem in both instances was a solder dry-joint with the AC adapter connector in the laptop itself. Luckily I know which is the hot end of a soldering iron pretty well. :)

Just unplug the adapter and see how long it takes to power down to eliminate h/w being the fault.

---

### Post by baboo on 2011-08-02
thanks for the reply. I will try that, however I had slackware installed on laptop and it did not have the problem.

I will post back the results.

thanks

---

### Post by baboo on 2011-08-02
Well, acpi indicated the battery had two hours left and that's what it ended up being. I really think this is a software issue. I installed debian with kernel 2.6.35.8 and it does not have this issue. Could it be a bug in power management in kernel?

---

### Post by baboo on 2011-08-02
bump:  I really think this is a bug. I installed 10.04 on my wifes new laptop and its doing the same thing.

I have a fully charged battery and the ac cord is plugged in. But the battery popup keeps saying there is only 3 minutes left on battery. Same thing on wifes. Although not the exact same time.

does anyone have a clue?

---

### Post by omelette on 2011-08-09
If you're still in trouble you might consider upgrading the kernel with a rc version;

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Ubuntu tends to play-safe and not be too adventurous with kernel version and I twice had to switch from Ubuntu because of this regarding the laptop - hence the reason I'm writing this on Fedora, not Ubuntu!  And wouldn't you know it, it has happened again, this time with another of my Ubuntu-based PC's - but this time a network problem. (see my posts in another thread).  Someone suggested the problem was the kernel and this proved to be the case.  Incidentally, I'm after installing Fedora 15 on yet another machine and it has the very same network bug as Ubuntu with the 'standard' kernel supplied.  However Fedora is less cautious about its kernel-releases and have a current 2.6.40 already in the repositories - no pissy release-candidate and it fixes the problem.

Might be a solution to your problem too...

---


---
title: "Hardy: Hibernate works, then restarts"
date: 2008-04-30
forum: Hardware
---

### Post by betamike on 2008-04-30
I was extremely pleased to see that hibernate (suspend to disk) works on my laptop with Hardy Heron.  There is just a strange quirk that I'm not sure how to start troubleshooting.

After hibernating, the computer will restart ~75% of the time.  The other 25% of the time, the computer will shut off like it should.

I'm using the ATI fglrx driver, and I know it has caused trouble with hibernate in the past; could it be related to that?

Anyone else experiencing this issue?

---

### Post by garyedwardjohnston on 2008-04-30
Not sure, have you tried tweaking power management?

---

### Post by betamike on 2008-05-01
I took a look at the power management dialog, but none of the options really fit the issue.  I'm not sure what I should have been looking for anyway.

Since my first post I've hibernated twice, once it worked properly and just shutdown, the other time it hibernated and then restarted.

When hibernating (before the one that restarted) the flgrx driver seemed to throw some kind of error.  I didn't have anything to write down the message, so the following is from memory.  Next time I hibernate I'll try to jot down the whole thing:

Something to the effect of:
> FGLRX failed to set pat_2, pat_2 is already set.

Again that is from memory so it's not 100% accurate.

Both times, the computer recovered from hibernate fine.  The issue is more annoying than non-functional.

---

### Post by excogitation on 2008-05-02
I just had the same problem using s2disk.

If I "accidentially" fall over the solution - I'll report back.

---

### Post by betamike on 2008-05-03
Thanks excogitation, I'll do the same.

---

### Post by Paul S on 2008-05-03
> **betamike said:**
> I was extremely pleased to see that hibernate (suspend to disk) works on my laptop with Hardy Heron.  There is just a strange quirk that I'm not sure how to start troubleshooting.

After hibernating, the computer will restart ~75% of the time.  The other 25% of the time, the computer will shut off like it should.

I'm using the ATI fglrx driver, and I know it has caused trouble with hibernate in the past; could it be related to that?

Anyone else experiencing this issue?

Yes, similar problem here.  I just started testing out suspend and hibernate.  So far I've had 4 successful suspends but only 2 successful hibernates.  After the 2 good hibernates, the next 3 have all failed to go off and just recycle back to the operating system.

Also using ATI fglrx driver on hardy.

regards,

---

### Post by excogitation on 2008-05-03
Did you try if today's fglrx update changed anything?
(I'm always hesitant installing a new fglrx version due to the problems
I had with that - but I will next time I need to reboot).

---

### Post by Paul S on 2008-05-03
Yes, I am using the latest version.

The only thing I find that helps is if I turn off Desktop Effects (compiz).  Then it works every time, so far.

---

### Post by tpscan on 2008-05-03
Hibernate and suspend also fail for me.
Using Hardy 8.04 -64bit
ATI X1600 with fglxr
AMD 64x2 3800, 1GB DDR Ram
nVidia 6150 based MB (FoxConn)
160 GB hdd, 1.5 GB=swap, /= 15GB linux ext3

Trying either option appears to work,
with services stopping, xserver shutsdown
LCD screen reports "no signal"
but instead of powering down, the system effectively restarts
and after a few moments we're back at a login RESUME screen

dmesg appears to indicate ACPI found and working
I've attached lspci -vnn and dmesg

---

### Post by excogitation on 2008-05-22
There's another post on 
> random numbers.random numbers [fglrx: KCL_Enable_Pat] *ERROR* Pat entry 2 is already configured 
[hibernating issue: pat entry 2..?]("http://ubuntuforums.org/showthread.php?p=5019757")

[and I started a bug report.]("https://bugs.launchpad.net/ubuntu/+bug/234125")

s2disk still works sometimes
(I mean it works every time saving the desktop session
- it just restarts ~75% of  the time -
pressing power 4secs while in grub isn't an acceptable workaround)

I don't know if we're (I?) talking cross purposes here:
I have the Pat entry 2 problem with Hardy's inbuilt hibernation,
but the restarting issue with s2disk from uswsusp.

btw the problem still persists with the latest uswsusp 0.8,
but the included s2ram works flawless - at least as far as I can tell.

---

### Post by pgilmon on 2008-07-13
It happens the same to me. I have nvidia, so I don't think it's something specific to ATI drivers. Did anyone find a solution to this?

---


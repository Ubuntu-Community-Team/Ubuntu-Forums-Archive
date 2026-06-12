---
title: "System keeps freezing (a potentially serious bug)"
date: 2008-09-15
forum: General Help
---

### Post by theyain on 2008-09-15
For some reason my computer keeps freezing at the most random times.  To the point that hitting num lock won't do anything. 

At first I thought it was my new psu, but until just now I wasn't sure because I was never able to catch it in the act of freezing up.  When it did start to happen, the computer started to slow down really quickly.  However I was able to hit ctrl alt backspace, thus restarting X. Once X was restarted, I didn't notice any slowdown problems.

I'm not sure if this strictly an x.org problem or if its something related to x.org, but it seems odd that X would be able to freeze my computer to the point that num lock would not respond.


I don't know how to view x.org logs, so I can't be sure.  Any help on diagnosing this problem?

---

### Post by 3rdalbum on 2008-09-15
System > Administration > System Log

Check out Xorg.0.log, and also look at the kern.log.  I think X *can* freeze to the point that Num Lock won't respond, but you'd probably find all the interesting information in the kernel log.

If no logs show anything wrong, try disabling your graphics card driver by using the Screens And Graphics program to switch to a 2D driver. (If you have an Nvidia card, use the "nv" driver. If you have an ATI card, use the "ati" driver).

---

### Post by theyain on 2008-09-15
There is a problem with switching over to an open source driver.  the nv driver doesn't have support for the tv out port.  And right now a TV is the only thing I have to use as a monitor.  

*checks the logs*

Hmmm, the x.org log doesn't show anything out of the ordinary (if you can call my x.org activity normal)...

However it seems klauncher segfaulted around the time everything went to hell.  

Sep 15 04:57:11 oh kernel: [ 5654.510201] klauncher[6362]: segfault at 00000095 eip b74b7ee7 esp bfca6620 error 4

But I can't find the time when the last freeze happened to confirm its klauncher

On a side note, is there anyway to figure out what "cooling device [f7c43f18]" is?  'cause I keep getting my logs flooded with this message:

Sep 15 11:52:39 oh kernel: [21077.121531] ACPI: Unable to turn cooling device [f7c43f18] 'on'

---

### Post by theyain on 2008-09-16
Bump


help please.

---

### Post by theyain on 2008-09-16
Bump again

---

### Post by theyain on 2008-09-18
bump again

---


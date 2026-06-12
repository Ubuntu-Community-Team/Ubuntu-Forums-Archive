---
title: "Suspend fails in ubuntu 10.10 sometimes"
date: 2010-10-16
forum: Hardware
---

### Post by ubuadmire on 2010-10-16
I recently upgraded from 10.04 to 10.10 (both 64-bit) in my lenovo T400 laptop. Suspend used to work totally fine before in 10.04, but now suspend fails sometimes. The half moon keeps blinking and the system is unresponsive. It seems it fails either 5th or 10th time I tried to suspend. 

I tried suspend from login screen and it also fails after trying it for more than 5 times. I tried without wireless with no change, and it does not matter what applications I open or close, the same problem exists.

I also tried this workaround from ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998/comments/30](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998/comments/30))
create files : /etc/pm/config.d/00sleep_module and /etc/pm/config.d/unload_module
add line to files : SUSPEND_MODULES="xhci-hcd"
with no success,

I really appreciate any suggestions. I do not want to switch back to 10.04 but if there is no option I will have to.

---

### Post by regiss on 2010-10-18
T400,4GB
Hi mate have same issue, here is some workaround for lenovo. [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9974877](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9974877)

What you have to do is create file let says in your home dir. Call it suspend and paste in:
*sudo acpitool -s && gnome-screensaver-command --lock*
and make it executable 

This will suspend and lock screen on resume.

Only problem is that I don't know how to overwrite suspend button so it could run without manualy executing that script. Any help would be appreciated on that.

Cheers Regiss

---

### Post by ubuadmire on 2010-10-19
Thanks for the response. But the manual suspend did not really fix my problem, instead switching back to a older kernel did.

I am using now 2.6.32 instead of  2.6.35 and suspend works like before. I am really not sure how it fixes the problem. Hopefully some one can use this info and figure out to find a fix for the latest kernel version.

---

### Post by MountainX on 2010-11-07
I'm having similar suspend failures with Ubuntu 10.10. 

Sometimes it will suspend. When it suspends, it resumes fine.

Sometimes it fails to suspend. A typical error I see is something like this:
```
Freezing of tasks failed after 20.01 seconds (1 tasks refusing to freeze)
```
In these cases, the system immediately resumes, never fully going to sleep.

I think I have narrowed it down to a could potential causes:
1. it seems that the hardware sensors and/or system monitor applets in the gnome panel may prevent suspending in 10.10. (They didn't in prior releases, afaik.)

2. it seems that if I have Nautilus open to an NFS share location, suspending may not work.

Reproducing this behavior takes a lot of time. I don't want to completely trash my system either, so I am testing carefully. But so far I think I can get it to suspend reliably when I don't have any NFS shares open in Nautilus and I don't have those two applets in the panel.

If I am logged in under another user account that doesn't have any of my settings, suspend/resume seems to work reliably. (I need to test more.)

---

### Post by pouriaba on 2010-12-07
this fix works for me on a Dell mini 1012 running ubuntu 10.10 32 bit 

alt-f2 for gconf-editor

/apps/gnome-power-manager/lock/suspend

uncheck : blank_screen
check   : gnome_keyring_hibernate
uncheck : gnome_keyring_suspend
check   : hibernate
uncheck : suspend
uncheck : use_screensaver_settings
 

you wont have the security a lock screen upon wake from the suspend, but you will have a convenient sleeping and waking suspend. the choice is yours. 

i'll mark this as solved. but consider it a partial solution. 

scratch that. cant even find it.


**UPDATE** 
I closed my netbook feeling satisfied I had solved my problem. The next day i opened it up hoping to fire off a quick email before work and the problem had REAPPEARED! le sigh.

---

### Post by kooldino on 2010-12-16
Found this solution for my Dell Mini 1012.  Thank God it works:

[QUOTE="Petri K"]Hi!

This problem affects not just the Lenovo T400 but also for example the new Dell Latitude E4200, HP EliteBook 2530p, Sony Vaio VGN-TT1, Toshiba R600, or anything else with the "Mobile Intel® GM45 Express Chipset" or X4500. I have exactly the same symptoms on my E4200 running intrepid.

The bug most certainly resides in the xserver-xorg-video-intel code. The fact that is manifests itself only with gnome desktop and not with KDE or text mode gives some clue. It is not compiz related as disabling compiz has no effect. I would say that this is a classical multiprocessor concurrency control problem! Disabling all but one core makes the bug disappear.

Here is my suggestion for a workaround. Save in /etc/pm/sleep.d/00CPU with 755 permissions. Note that it has to be called 00CPU so that it gets executed before and after anything else.
```

Code:
#!/bin/sh
# Workaround for concurrency bug in xserver-xorg-video-intel 2:2.4.1-1ubuntu10.
# Save this as /etc/pm/sleep.d/00CPU

. "${PM_FUNCTIONS}"

case "$1" in
	hibernate|suspend)
		for i in /sys/devices/system/cpu/cpu*/online ; do
			echo 0 >$i
		done
		;;
	thaw|resume) 
		sleep 10	# run with one core for 10 secs
		for i in /sys/devices/system/cpu/cpu*/online ; do
			echo 1 >$i
		done
		;;
	*)
		;;
esac

```
Please report if this works for you! The sleep period can easily be made longer if necessary.

Petri K[/QUOTE]

---

### Post by Laarmans on 2010-12-18
this (Petri K's solution above) worked for me - thanks! This is on Dell Latitude E6510

---

### Post by Joliea on 2010-12-20
I can't find the "OOCPU" file in the /etc/pm/sleep.d/ :( Anyone?

---

### Post by johanbove on 2010-12-21
Confirmed to be resolved on my Sony Vaio VPC-EB2Z1E running Linux Mint 10 (64) after updating the xserver-xorg-video-intel driver from version 2:2.12.0-1ubuntu5 to version 2:2.12.0-1ubuntu5.1

Using the Linux Mint Update Manager this update required me to set the visibility of updates with security level 4 to true.

---

### Post by pouriaba on 2011-02-24
confirmed to work on a Dell Mini 1012 running Ubuntu 10.10 x86

---

### Post by elatre on 2011-02-25
I read the following in the file /usr/lib/pm-utils/sleep.d/99video (maverick):

# Handle video quirks.  If you are having suspend/resume issues,
# troubleshooting using this hook is probably the best place to start.
# If it weren't for video card quirks, suspend/resume on Linux would be 
# a whole lot more stable.

So I (backup'd and) deleted the files 99video and 98video-quirk-db-handler in that directory /usr/lib/pm-utils/sleep.d

Now suspend works fine. 

Is it save to delete these two files or should I restore them? What are they suposed to be for?

____________

Added:
Sorry, I wrote this message too soon. It doesn't work. After some times failed suspend again.

---

### Post by GaryH on 2011-04-11
I just discovered I also have this issue with my brand new Lenovo S10-3 running 64 bit 10.10. Does anybody out there have or know of a solution? I'll be glad to test it and publish my results.
Thanks,
Gary

---

### Post by djolk on 2011-04-14
Try 'sudo apt-get install hibernate'

it fixed it for me.

---

### Post by djolk on 2011-04-14
Try 'sudo apt-get install hibernate'

it fixed it for me.

---

### Post by chefebe on 2011-05-24
Works for me on Lenovo T400 in Ubuntu 10.10  (yeah)

I followed the Petri K (kooldino) solution above, creating a new file /etc/pm/sleep.d/00_cpu  and adding the contents he posted.

My system went to sleep when shutting the lid and resumed normally to a login screen when opening lid.  Previously I would just get a flashing moon and couldn't resume or sleep.  I would have to hard power off.

I tried twice so far so the results are inconclusive but it seems to be working.  I loaded the following:
   Firefox w/youtube video running.  Volume muted.
   Qt Creator w/app loaded and deployed to a running QEMU VM.
   soffice slideshow presentation
(this is the set of things needed for a recent conference talk where I desparately wished I had sleep/resume fix)

Thanks Petri!

---

### Post by chronos00 on 2011-07-15
> **djolk said:**
> Try 'sudo apt-get install hibernate'

it fixed it for me.

Thank you djolk! That worked flawlessly for me!

On the other hand, I have the feeling that the underlying problem that leaded to suspension failure is still present... But at least it is not as critical as before.

Regards!

---

### Post by chronos00 on 2011-07-16
> **chronos00 said:**
> Thank you djolk! That worked flawlessly for me!

On the other hand, I have the feeling that the underlying problem that leaded to suspension failure is still present... But at least it is not as critical as before.

Regards!

Once again, I jumped to conclusions too soon...
Suspension is definitively working better, but it is still failing quite often.

---

### Post by pedro314 on 2011-10-14
I am having the same problem on a Portégé R600: suspend and hibernate work but take about 5 minutes(!) to complete. 

Am currently using 11.10 but the problem has existed since 10.04.

I have tried the various suggestions above without any luck.

If anybody managed to make suspend work on the R600 I'd really appreciate a description of what to do.

Best regards

---


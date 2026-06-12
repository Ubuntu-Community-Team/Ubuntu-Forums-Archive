---
title: "Laptop suddenly freezes after a period of use"
date: 2011-04-11
forum: Hardware
---

### Post by papillion on 2011-04-11
I've had this problem for about six months now and I can't seem to pinpoint what's going on or get a definitive answer from the mailing list or forum so I thought I'd throw this out there just in case anyone might have some advice:

LAPTOP: Acer 5150
LINUX:  Ubuntu 10.10
RAM:    3Gb

DESCRIPTION OF PROBLEM(s):

After an arbitrary period of use the laptop will suddenly freeze and completely stop responding to both mouse and keyboard events. The condition will remain until the system is hard rebooted. Most of the time, after a hard reboot, the system will boot, load the desktop, then immediately freeze and sometimes "stripe screen" (see attached picture) and must be rebooted 3-5 times. 

Additionally, after playing ANY Flash based video, the system begins to respond more and more sluggishly until it eventually crashes and must be rebooted. Other video formats (avi, mpg, etc) have no yet been tested to determine whether they cause a freeze or not.

MY THEORY ON THE PROBLEM:

I believe the first problem is caused by either an incompatibility or mis-setting in regards to the video card OR an incompatibility or mis-setting in the wireless card. 

The second problem, I believe is caused by a severe memory leak in regards to Adobe Flashplayer. I believe that the crash is caused by Flash Player consuming more and more memory until the system crashes.

Can anyone help? I'm attaching the syslog file if anyone cares to take a look at it. If you need any other log file, please let me know and I'll post it. I am now desperate to get this problem solved as I'm now routinely losing work due to these freezes.

Thank You,
Anthony

---

### Post by Joe of loath on 2011-04-11
How hot is it getting before it crashes?

---

### Post by papillion on 2011-04-11
> **Joe of loath said:**
> How hot is it getting before it crashes?

Pretty hot. Could that be the cause?

---

### Post by Joe of loath on 2011-04-11
Yes, sounds like overheating to me.

How averse are you to opening up the bottom and clearing the dust out?

---

### Post by papillion on 2011-04-11
> **Joe of loath said:**
> Yes, sounds like overheating to me.

How averse are you to opening up the bottom and clearing the dust out?

Not averse at all. I'll do it tomorrow. Thank you!

---

### Post by washakie on 2011-04-11
I had a similar problem with a Samsung X360. It was a great computer, and all worked well, but it eventually started to have a problem whereby it would 'freeze' only to be fixed by a hard reboot / power cycling. The key issue was that when it would freeze, the screen would flicker madly. I never found a fix. There's a thread with other folks having similar problems here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659705](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659705)

---

### Post by machinehead11 on 2012-01-02
[FONT=Arial][SIZE=2]Assuming you've cleaned all the dirt and dust our from the fan and the heat sink (best done by removing the fan motor), all drivers up to date, memory and hdd checked out ok, you might find, like I have, that the GPU (Graphics processor) is overheating.   Acer and some others use a pad to conduct the heat from the GPU to the heat sink.  This either seems to shrink or dry over time and then does not take the heat away from the GPU.  After about 45 mins in my case the screen would stripe and the computer most times would freeze.[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2]There are copper shims available to replace the pad, and reassemble the heat sink on to the processor and GPU using fresh thermopath and you’ll hopefully have a fully working laptop again!  I found the shim for £1.50 on a well known auction site and Maplins sell the thermopath for £2.99.[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2]I searched and search for this solution, which was tucked away in a thread on another forum somewhere, so thanks to the OP, but wanted to repost this to hopefully help someone else out.[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]

---


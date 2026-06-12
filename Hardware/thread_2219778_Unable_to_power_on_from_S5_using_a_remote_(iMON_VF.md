---
title: "Unable to power on from S5 using a remote (iMON VFD)"
date: 2014-04-25
forum: Hardware
---

### Post by uhud2003 on 2014-04-25
Hey everyone,
first off I hope I am posting in the right subsection of the forum if not please feel free to move the thread to the appropriate section.

As the title already says I am having problems powering on my HTPC from S5 state using the remote (RM200 that was supplied with the display) if I performed the shutdown using Linux (Xbmcbuntu in my case).
If I shutdown the PC using Windows powering on with the remote is just working as it should (power button on the case it self is working in both cases).

I did some research on my own e.g found [this thread ]("http://www.vdr-portal.de/board/thread.php?threadid=57645")(it's in german) saying voltages on the usb port differ between Linux and Windows but i couldn't reproduce the findings when measuring on my system.
Also found [another thread]("http://forum.xbmc.org/showthread.php?tid=110326") stating that kernel prior to 2.6.38-10 worked but neither downgrading the kernel nor trying an older version of Ubuntu(11.04) did the trick for me.

I have come to an dead end and hoped someone on this forum has encountered this problem and has perhaps found a way to solve it.
 If anyone needs any extra information i am more than happy to post them.

Thanks in advance.

EDIT:

Solved thanks to [this]("http://ubuntuforums.org/showthread.php?t=2219778&p=13185172#post13185172") post 

Edit your /etc/init.d/lirc file and change the line:

DISABLE_KERNEL_SUPPORT=true

to

DISABLE_KERNEL_SUPPORT=false

---

### Post by tgalati4 on 2014-05-13
```
man acpitool
```

Post the output of:

```
acpitool -w
```

You need to make sure you keep power to part of the bus that controls the infrared receiver.  Otherwise your remote won't get detected.

---

### Post by uhud2003 on 2014-05-13
Thank you for your answer.
As far as I can tell the receiver is getting powered in S5 since the display which is attached to it is working to (and I measured the output of the ports via a multimeter).

Here is the output of acpitool -w
>    Device       S-state   Status   Sysfs node
  ---------------------------------------
  1. GLAN         S4    *enabled   pci:0000:00:19.0
  2. EHC1         S4    *enabled   pci:0000:00:1d.0
  3. EHC2         S4    *enabled   pci:0000:00:1a.0
  4. XHC          S4    *enabled   pci:0000:00:14.0
  5. HDEF         S4    *disabled  pci:0000:00:1b.0
  6. PEG0         S4    *disabled  pci:0000:00:01.0
  7. PEGP         S4    *disabled
  8. PEG1         S4    *disabled
  9. PEG2         S4    *disabled


---

### Post by Nimanic on 2014-05-14
Hi,

i have the same problem.

Using Ubunto 12.04 (XBMCUbuntu12) i had no problems, i could simply boot up my PC by using the Power button on the remote.
Booting up Windows7 once (dualboot) i can after shut down also boot up the PC again once with the remote.

Since i have installed Ubuntu 14.04 (same with 13.10) i can use the IR Remote to control XBMC and shut down the PC, but i can not start the PC.

From my point of view it is not a Hardware problem.

It looks like that Ubuntu is doing what ever trick with the device, to turn it off, or make it sleep.
There is something differnet in the handling compared to Ubuntu 12.xx.

Thanks for what ever idea, to make Ubuntu 14.04 handling that situation better.


Thanks for the help and best regards.

Nimanic

---

### Post by mhatt on 2014-05-22
I also have this problem since I upgraded from mythbuntu 12.04 to 14.04,  I now cannot turn on my antec fusion media centre pc from the powered off state, this worked fine in 12.04?

---

### Post by User-007 on 2014-10-12
Hi,

I confirm the issue. I have an Antec Fusion Remote Max case with iMon IR receiver. Remote boot from S4 works fine but nothing happens when trying to remote boot from S5. I have managed to boot remotely from S5 only once after detaching the case and modifying hardware. Using 14.04.

This seems clearly to be a linux-related bug (not sure how linux handles shutdown vs Windows). Something different, thats sure. IR is always on, thats clear to see thanks to its backlight.

However, I cannot file a bug for a some reason. Could someone else file a bug?

---

### Post by jerry-zimmerman on 2014-12-05
> **User-007 said:**
> Hi,

I confirm the issue. I have an Antec Fusion Remote Max case with iMon IR receiver. Remote boot from S4 works fine but nothing happens when trying to remote boot from S5. I have managed to boot remotely from S5 only once after detaching the case and modifying hardware. Using 14.04.

This seems clearly to be a linux-related bug (not sure how linux handles shutdown vs Windows). Something different, thats sure. IR is always on, thats clear to see thanks to its backlight.

However, I cannot file a bug for a some reason. Could someone else file a bug?

Any developments on this matter? I'm experiencing the same issue. And it's anoying :-(
Maybe a workaround? I'm using Kodi on a 14.04 minimal installation, and all works great except for the wake-up. An indeed, it works once every time once the unit has been detached from electrical power.

Any help is appreciated,
Cheers,
Jerry

---

### Post by evanelion-infinite on 2014-12-11
Wooooa! Finally after one week of work and investigate finally I can poweron my HTPC (OrigenM10 with 15c2:0036 VFD+Remote). This annyioing bug is very easy to fix. Edit your /etc/init.d/lirc file and change the line:

DISABLE_KERNEL_SUPPORT=true

to

DISABLE_KERNEL_SUPPORT=false

Everything is working perfect now! :)

---


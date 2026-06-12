---
title: "How to diagnose random freeze"
date: 2008-12-16
forum: Hardware
---

### Post by jbtito03 on 2008-12-16
Hi there...

I installed a new (old) system, which runs well. It is a Athlon64 3000+ with an EPOX (nforce3) 8KDA motherboard and a nVidia 7600GS card running Ubuntu 8.10 Interpid.

So most of the time its all good but now and them (totally randomly) i get system wide lock-ups which only let me reset the computer and start all over. It is getting quite annoying and the problem is that I cannot (don't know how) diagnose the problem.

I checked the system logs which say nothing and the only thing i can say for sure is that I get the number 19 on the mainboard (an build-in led display). I ran the memory thet and ruled out the possibility of faulty RAM. Also, changed the BIOS to fail safe settings and it still happens. 

Has anyone got any idea how to proceed - i still dont know if it is a software or hardware problem. 

Cheers...

D.C.

---

### Post by albinootje on 2008-12-16
I've seen freezes like that due to powermanagement problems with the screensaver.
What happens when you boot with the "noapic nolapic" parameters appended to the kernel line in the grub config ?

What about the CPU cooling ? Is that still OK ?

---

### Post by jbtito03 on 2008-12-17
No.. it does not help.

Actually i got a freeze while bios was booting. 

Any idea?

Cheers

D.C.

---

### Post by jbtito03 on 2008-12-17
Okey... i just found something that might be of use:

Dec 17 19:53:43 MarviN ntpd[5991]: ntpd exiting on signal 15
Dec 17 19:54:13 MarviN ntpd[8289]: ntpd 4.2.4p4@1.1520-o Wed Dec 17 07:46:30 UTC 2008 (1)
Dec 17 19:54:13 MarviN ntpd[8290]: precision = 1.000 usec
Dec 17 19:54:13 MarviN ntpd[8290]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Dec 17 19:54:13 MarviN ntpd[8290]: Listening on interface #1 wildcard, ::#123 Disabled
Dec 17 19:54:13 MarviN ntpd[8290]: Listening on interface #2 lo, ::1#123 Enabled
Dec 17 19:54:13 MarviN ntpd[8290]: Listening on interface #3 eth1, fe80::204:61ff:fe52:22c#123 Enabled
Dec 17 19:54:13 MarviN ntpd[8290]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Dec 17 19:54:13 MarviN ntpd[8290]: Listening on interface #5 eth1, 192.168.1.102#123 Enabled
Dec 17 19:54:13 MarviN ntpd[8290]: kernel time sync status 0040
Dec 17 19:54:13 MarviN ntpd[8290]: frequency initialized -73.804 PPM from /var/lib/ntp/ntp.drift
Dec 17 19:57:26 MarviN ntpd[8290]: synchronized to 193.2.4.2, stratum 1
Dec 17 19:57:26 MarviN ntpd[8290]: kernel time sync status change 0001

That's always the last massage as long as I can tell in the daemon logfile before the freeze.

Did not hear about the ntp service being the cause for such random freezes but.. lets hear.

Cheers

D.C.

---

### Post by niller on 2008-12-18
I can confirm this, I have exactly the same issue here (I hope the developers see this !)

It started 2 hours ago, it's really weird!

First time I rebooted, the progressbar stopped about 12% in the boot up and the system freezed.

The only way I could start up my system was to boot up with the install CD and then choose "Start up with first harddrive".

When up and running, the User switcher applet was disabled the first time. The second time it came up properly though.

Second time I tried it stopped at the Grub screen (which I have enabled).

Third time I didn't even get to BIOS boot screen.

I have a system similar to yours:
Processor:AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
Motherboard: ASUSTek A8NE-FM
Videocard: Nvidia GeForce 6600 GT
Kernel: 2.6.27-9-generic
Ubuntu: 8.10 Interpid Ibex

I have installed the Nvidia BETA video driver 180.06, but I dont think this is the problem ?

It could be an issue with the screensaver, as it was active when it happened.

I now have disabled the screensaver, hope it works :/

But it would be nice to know which logfile is the right one to diagnose this ??

---

### Post by albinootje on 2008-12-18
> **niller said:**
> I can confirm this, I have exactly the same issue here (I hope the developers see this !)


Check [http://launchpad.net/](http://launchpad.net/) for bug-reports and the like.
On the ubuntuforums.org there are normally no active Ubuntu-developers is my impression.

---

### Post by niller on 2008-12-18
> **albinootje said:**
> Check [http://launchpad.net/](http://launchpad.net/) for bug-reports and the like.
On the ubuntuforums.org there are normally no active Ubuntu-developers is my impression.

Looking at it right now :)

Thanks,

---

### Post by albinootje on 2008-12-18
> **niller said:**
> 
But it would be nice to know which logfile is the right one to diagnose this ??

In this case i would first check /var/log/kern.log

---

### Post by niller on 2008-12-18
I've reported this bug on Launchpad.
[https://bugs.launchpad.net/ubuntu/+bug/309377]("https://bugs.launchpad.net/ubuntu/+bug/309377")

Thanks,

---


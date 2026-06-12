---
title: "high hd-activity after resume from standby"
date: 2008-11-19
forum: Hardware
---

### Post by Bazon on 2008-11-19
hello!

after every 3rd or 4th resume from stranby, my 8.10 on my laptop has such a high harddrive-activity that it is nearly unuseable. even switching to tty1 is very slow and running commands there takes a long time.

any ideas how to avoid that?

---

### Post by Bazon on 2008-11-22
up

---

### Post by habtool on 2008-11-22
It could be 'tracker' if you have that enabled?

---

### Post by sdennie on 2008-11-22
When the high disk activity starts, try:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Then:

```

tail -f /var/log/syslog

```

That should tell you what is causing the disk activity.  Once you have all the data you need use the following to turn off the log spam:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

---

### Post by GrumpyBob on 2008-11-22
This happened to me recently, and I ran system monitor to identify the culprit,  It seemed to be vbetool.

Hasn't repeated itself lately, though.  (I had been playing with video drivers in an attempt to get compiz working again, and out it down to that).

Robert

---

### Post by Bazon on 2008-11-24
The problem is:
The high hd-activity starts before I'm able to log in!

But recently, I tried another strategy and hadn't that (before irregular appearing) problem since:

I disabled both the apmd service (since the acpid service is running, too) and the kdm service (since i use gdm).
Running both apmd and acpid and gdm and kdm services was default (kdm since i installed kubuntu-desktop), i hadn't changed it before.

but i'm not absplutly sure whether that really helped, i need to test it some days....

---

### Post by Bazon on 2008-11-26
OK, proplem re-appeared, so I tried that:

> **vor said:**
> When the high disk activity starts, try:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Then:

```

tail -f /var/log/syslog

```

That should tell you what is causing the disk activity.  Once you have all the data you need use the following to turn off the log spam:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

with starting the monitoring before going to standby, as the computer is unusable after that. (terminal doesn't respond on keyboard inputs, it doesn't even display them....)

so most of the reports were 
**kswapd0 WRITE**
and
**firefox READ**

(although having only 4 tabs open in firefox....)

The Gnome-System-Monitor-Applet shows 100% for IOWait.
the process with highest CPU usage is "dd" with about 10%.

Any ideas?

---

### Post by Bazon on 2008-11-26
(PS:
The computer stayed in that state of high hd-activity and unusablitly for more than 20minutes, when i switched it off.)

---

### Post by Bazon on 2008-11-26
Further tests show:
It's definitely related to the swap.
When the swap is empty, resume from standby works instantly, if the swap is not empty, the strange hd-activity starts.....

---

### Post by mtinman on 2008-11-27
I have the same problem with my Toshiba Satellite A135-S2246 laptop. This problem is driving me nuts, because it takes about 25 minutes or so from the time I resume until the time I can start using the laptop. I wonder if there is a way that we could issue a command, or write a script that would purge the swap file before initializing the suspend or hibernate mode? Just a thought. How much RAM do you have in your Ubuntu PC?

---

### Post by Bazon on 2008-11-30
I have 1024MB RAM.

You can switch off swap with *sudo swapoff -a * (and switch it on again with *sudo swapon -a *) but whyever, for me that didn't help:

After resuming there was still the hd-activity, and the display of my computer stayed dark.

---

### Post by Bazon on 2008-11-30
OK, i have enough, this is drivin me mad!

Can someone please help me to file a good bug report?
In what package does this belong, and what additional data can I supply?

---

### Post by GoogleGuy on 2008-12-01
> **Bazon said:**
> OK, i have enough, this is drivin me mad!

Can someone please help me to file a good bug report?
In what package does this belong, and what additional data can I supply?

I think your best bet is to submit a bug report at ttp://bugzilla.kernel.org, under "Power management", as this is definitely kernel-related. For starters, just describe the problem, or link to this thread. The kernel people should tell you which logs to provide. Also, I think it's important to know which suspend/resume method you're using (uswsp, tuxonice.)

BTW, what's the kernel version you're running (uname -r)?

---

### Post by GoogleGuy on 2008-12-01
Also, I found this issue in Launchpad, looks related to your problem:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/15372](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/15372)

There's a chance the problem may be fixed by updating to the latest stable kernel 2.6.27. You can try this and see if this helps.

---

### Post by GoogleGuy on 2008-12-06
This could also be related to ATI proprietary drivers going nuts:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/190585](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/190585)

One of my laptops occasionally has this problem, and it does have an ATI Radeon Xpress 1100. Toshiba Satellite A135-S2246 also comes with ATI video.  Bazon, what's the video card on your laptop?

I'll try disabling 3D acceleration and see if the problem comes back. Problem is, it doesn't happen often with me, maybe once or twice a month, so maybe one of you guys could try disabling 3D and see if this solves the problem.

---

### Post by Bazon on 2008-12-06
Uh,that seems to match!

In fact I use the flglx driver with an ATI card.
Thanks for that info, GoogleGuy, I subscribed to that bug. 

I'll check on my Laptop the next days whether disableling 3D helps...
(testing takes some time for this bug, first I have to extend memory use before this problem occurs, and that lasts a while after a restart..)

---

### Post by GoogleGuy on 2008-12-07
> **Bazon said:**
> Uh,that seems to match!

In fact I use the flglx driver with an ATI card.
Thanks for that info, GoogleGuy, I subscribed to that bug. 


No problem. You test it on your end. In the meantime, I'm testing a Debian 2.6.27 kernel *with* 3D (in case 2.6.27 fixes it), and a 2.6.24 kernel *without* 3D.

What kernel do you have (uname -r) that exhibits this problem?

---

### Post by mtinman on 2008-12-12
> **GoogleGuy said:**
> No problem. You test it on your end. In the meantime, I'm testing a Debian 2.6.27 kernel *with* 3D (in case 2.6.27 fixes it), and a 2.6.24 kernel *without* 3D.

What kernel do you have (uname -r) that exhibits this problem?

My kernel is 2.6.27-9-generic, I have not tried disabling the 3D yet, because I have never had to do it in Ubuntu before (I migrated from Fedora). What is the best method of disabling 3D in Ubuntu? BTW, I'm using the proprietary ATI driver(fglrx).

---

### Post by GoogleGuy on 2008-12-14
I don't have a Ubuntu laptop on me right now (I'm sure you can look around the Gnome menu for Administration or Restricted Drivers Management and such, and disable it via GUI), but you can just rename the driver's file.

Something like this:

# sudo updatedb
# locate fglrx | grep `uname -r`

...should output:

/lib/modules/2.6.27-9-generic/kernel/drivers/char/drm/fglrx.ko

That's the driver's file responsible for 3D. Now just get it out of the way:

# cd /lib/modules/`uname -r`/kernel/drivers/char/drm/
# sudo mv ./fglrx.ko ./fglrx.ko.bak

Now run depmod and restart X, or just reboot (easier.)



Whichever way you use to disable it, log into X again, and verify there's no 3D:

# xdpyinfo| grep -i dri

The above should produce no output with 3D disabled.

---


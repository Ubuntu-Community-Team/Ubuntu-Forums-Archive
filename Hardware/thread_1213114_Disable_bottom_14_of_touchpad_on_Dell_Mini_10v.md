---
title: "Disable bottom 1/4 of touchpad on Dell Mini 10v"
date: 2009-07-14
forum: Hardware
---

### Post by moofbong on 2009-07-14
I just got a Dell Mini 10v, and installed Jaunty on it.  Everything works great except for the touchpad.  Since the buttons are built into the touchpad and are themselves touch sensitive, it's basically impossible to drag something.  Is there a way to disable the bottom 1/4 or the bottom two corners of the touchpad?  As far as I know, it has the same hardware as the Mini 9, but I can't seem to find anything about this.

People seem to be having the same problem over at [http://mydellmini.com/forum/dell-mini-10v-discussion/9552-10v-linux-trackpad-driver.html](http://mydellmini.com/forum/dell-mini-10v-discussion/9552-10v-linux-trackpad-driver.html) but there hasn't been a solution yet.  There's also a bug for this issue on Launchpad: [https://bugs.launchpad.net/ubuntu/+bug/395515](https://bugs.launchpad.net/ubuntu/+bug/395515) but there hasn't been any activity.

Thanks!
Brandon

---

### Post by moofbong on 2009-07-15
It looks like enough people had this problem that somebody patched the synaptics drivers.  Add this PPA to apt, and install the xfree86-driver-synaptics package that's in the repository: [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/) .  I recommend disabling the repository once you're done so you don't end up getting all the other updates.

There are actually 2 changes in this driver package:  one makes the trackpad less jumpy and one allows you to disable everything below a certain y-value.  The jumpy patch seems to have fixed all of my woes, and I didn't need to disable the bottom part of the trackpad after all.  If you still want to, I recommend starting with a MovementBottomEdge value of 4000 and playing with it from there.

```
synclient MovementBottomEdge=4000
```

---

### Post by (pr) on 2009-08-26
Could someone please tell me, step by step, how this is done? I'm new to Ubuntu (for real this time, I've tried it a few times in the past), just bought a Dell 10v to work with it, but the touchpad isn't my best friend. Help is greatly appreciated.

---

### Post by fallingleaf on 2009-08-27
I added the PPA (in Intrepid) and and did apt-get update but when installing I got this:

```
$ sudo apt-get install xfree86-driver-synaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting xserver-xorg-input-synaptics instead of xfree86-driver-synaptics
xserver-xorg-input-synaptics is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

So, why is it switching to a different package name, and where is the updated version?

---

### Post by cmgossett on 2009-09-11
I need help too!
I added the PPA, ...pretty sure the proper driver is installed.
i still don't get it.

I need a step-by-step please.

I have a 10v and the trackpad is driving me crazy.

thanks!

---

### Post by Tyrathect on 2009-09-19
I started a new thread with the instructions:

[http://ubuntuforums.org/showthread.php?t=1270382](http://ubuntuforums.org/showthread.php?t=1270382)



                           [                 ]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x9468D6EF04D8F0B0224766F6F195D85099C0198F&op=index")

---


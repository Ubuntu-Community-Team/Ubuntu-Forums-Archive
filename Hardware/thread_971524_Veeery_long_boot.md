---
title: "Veeery long boot"
date: 2008-11-05
forum: Hardware
---

### Post by okke on 2008-11-05
I'm on a fairly new laptop and I've had a pretty long boot time for some time now and was hoping it'd fix itself with intrepid. :p

It turns out it's just gotten worse, it now takes 4:09 to boot according to bootchart. There's probably more than one thing wrong here so attached the bootchart png and maybe someone could point out what might be the problems.

---

### Post by ravl on 2008-11-05
well, I´ve been trying Kubuntu 8.10-RC and I also get a strange boot. Things stop until I press a key, then continues boot and gets snagged on something else, so I keep hitting the spacebar until the system finally boots up.

I will try Kubuntu 8.10 final release tonight and see if it is still booting like this.

---

### Post by okke on 2008-11-05
> **ravl said:**
> well, I´ve been trying Kubuntu 8.10-RC and I also get a strange boot. Things stop until I press a key, then continues boot and gets snagged on something else, so I keep hitting the spacebar until the system finally boots up.

I will try Kubuntu 8.10 final release tonight and see if it is still booting like this.


The key-pressing doesn't help me. :(

The boot stays longer in some parts such as: "Loading hardware drivers", "Configuring network interface" and "Starting MTA". They might be a part of the problem.

I recently removed network-manager and installed wicd, could that be causing the stall at "Configuring network interface"? Can anyone help?

---

### Post by okke on 2008-11-08
Anyone? 4 mins is a bit too long.

---

### Post by okke on 2008-11-09
:( ?

---

### Post by fendres on 2008-11-09
What I can see is that there is something messed up with networking, since dhclient3 is runnung several times and is waiting half a minute for reply. But that seems not to be the main problem...

---

### Post by okke on 2008-11-10
> **fendres said:**
> What I can see is that there is something messed up with networking, since dhclient3 is runnung several times and is waiting half a minute for reply. But that seems not to be the main problem...

I tried disabling a lot of network-related (and probably others :) ) startup scripts and it did speed up the boot quite a bit. Now it's up to about a half, 1:52 as can be seen on the pic attached. It's still a tad too long, any idea what else could be causing this?

---

### Post by okke on 2008-11-14
Anyone? Still seem quite long, stalls for some time at loading hardware drivers and it doesn't seem to be doing anything there. Any ideas what could be causing it?

---

### Post by starcannon on 2008-11-14
I think you may be suffering from the same thing as this poster, and will possibly find his solution useful:
[http://ubuntuforums.org/showthread.php?t=822493](http://ubuntuforums.org/showthread.php?t=822493)

GL keep us posted on your progress

---

### Post by okke on 2008-11-17
> **starcannon said:**
> I think you may be suffering from the same thing as this poster, and will possibly find his solution useful:
[http://ubuntuforums.org/showthread.php?t=822493](http://ubuntuforums.org/showthread.php?t=822493)

GL keep us posted on your progress

Thanks, not sure if removing the MTA helped much, maybe somewhat but the main problem is still there. A lot of the boot time is still spent on the "Loading hardware drivers" part. :(

---

### Post by okke on 2008-11-20
Loading hardware drivers... 


How could I see what's causing the delay here or anyplace else?

---

### Post by Martje_001 on 2008-11-20
Let's find out!
```
sudo apt-get install bootchart -y
```
Then reboot and look in /var/log/bootchart

---

### Post by okke on 2008-11-21
> **Martje_001 said:**
> Let's find out!
```
sudo apt-get install bootchart -y
```
Then reboot and look in /var/log/bootchart

That's what I did. :)

I attached the file in the first post, it's gotten a bit better but something's still wrong so I'll attach the latest one now. Any idea what could be taking so long in the boot?

---

### Post by Martje_001 on 2008-11-21
As you can see. From 40 seconds to 80 seconds it's practically doing nothing. I think the process 'udevadm' is causing the problem.

I think you should file a bug report, so that the problem can be fixed. See [Launchpad](https://bugs.launchpad.net/).

---


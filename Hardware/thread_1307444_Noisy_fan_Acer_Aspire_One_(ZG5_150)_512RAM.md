---
title: "Noisy fan Acer Aspire One (ZG5 150) 512RAM"
date: 2009-10-31
forum: Hardware
---

### Post by IanB2 on 2009-10-31
I've been trying to figure out which thread I should be following (in the community documentation) to fix a noisy fan on my friend's AOA 150 ZG5.

Having just intalled UNR 9.10 (which looks really great and seems to perform brilliantly on the acer one) the only potential 'show stopper' is that the fan runs continuously, which drains the battery and is distracting.

I've tried the fix listed under the 110L model (but not surprised it didn't work)
**Fan Control module is now part of the kernel, but is not enabled by default. To enable it for the running session type: "sudo echo -n &#8220;enabled&#8221; > /sys/class/thermal/thermal_zone0/mode". To automatically enable it at boot, create &#8220;/etc/modprobe.d/acerhdf.conf&#8221; and add the line: options acerhdf kernelmode=1**
But that just returned **bash: /sys/class/thermal_zone0/mode: No such file or directory**

So then tried the 'acerfand' fix, but this also fails to make any difference to the fan (sudo acerfand)

Any suggestions as to how to control the fan? Other than that, UNR seems to be superb.

---

### Post by Happibun on 2010-01-30
I have the same problem, although I am using an Aspire One ZG5 1gig RAM and 160GB hard disk.

I have a horrid feeling that the fix involved flashing the BIOS with an update, and to do that requires a windows partition (according to Acer). I'm running Linux only now, so that leaves me in a bit of a hole :-(

Does anyone have any idea how to do this without Windows?

Thanks.

---

### Post by NetTechGuy on 2010-05-12
Well in my perspective, I have the same Happibun. I dont believe you have to update bios if your running one of the latest bios available. The whole problem is related with the kernel your running and the acerhdf module controlling your fan speed. I would look into changing the cpu frequent scaling to accomodate for best performance.. 
[http://wojox.homelinux.org/?p=58]("http://wojox.homelinux.org/?p=58")

---

### Post by Fir3chi3f on 2010-05-12
I was thinking that maybe to perform the changes in the original post one must be the super user (or whatever its really called) 

That is instead of 
```
sudo *command*
```

It would be
```
sudo su
*commands as super user*
```

Just something to try

---


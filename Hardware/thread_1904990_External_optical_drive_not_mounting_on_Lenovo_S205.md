---
title: "External optical drive not mounting on Lenovo S205 in 11.10"
date: 2012-01-05
forum: Hardware
---

### Post by BigBaka on 2012-01-05
I recently purchased a Lenovo S205 mini notebook after my girlfriends long lasting iBook G4 died. Not wanting to go back to Windows I installed Ubuntu 11.10 and am now trying to deal with the various teething problems that seem to always happen when installing Ubuntu for the first time.

One of these is that the external Samsung DVD optical drive have doesn't mount in ubuntu despite registering in the bios. When I plug into the usb ports it makes all the right sounds so power is going into the drive, but it simply doesn't mount into ubuntu.

Any advice would be welcome.

Thanks
BB

---

### Post by hansdown on 2012-01-05
Hi, BigBaka.

Please open a terminal(ctrl+alt+t).

Type

```
lsusb
```

This should show all usb devices.

---

### Post by BigBaka on 2012-01-06
The readout was as follows

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0489:e00d Foxconn / Hon Hai

It says this whether the optical drive is connected or not.

---

### Post by BigBaka on 2012-01-06
A quick update, I just realised that the actual problem is that only one of the 3 usb ports seem to work on any device. I can actually get the optical drive running on one of the usb ports but not the other 2. Is that consistent with the previous readout?

BB

---

### Post by hansdown on 2012-01-06
Strange. Do you know the exact model of the optical drive?

---

### Post by BigBaka on 2012-01-06
Bb

---

### Post by BigBaka on 2012-01-06
> **hansdown said:**
> Strange. Do you know the exact model of the optical drive?

It's a Samsung External DVD Writer Model SE-S084.

But it's definitely an ubuntu issue because I  have the exact same problem with a WD external hard drive (only works when plugged into one of the 3 usb ports), and also it is possible to boot from the optical drive on all 3 usb ports, indicating that ubuntu is not recognising the ports.

BB

---

### Post by hansdown on 2012-01-06
I agree with you.

I've looked at a lot of posts, and that model works.

There has been a large number of posts, involving lots of different drives.

Some people find, that rebooting with it plugged in helps, others don't.

---

### Post by BigBaka on 2012-01-06
> **hansdown said:**
> I agree with you.

I've looked at a lot of posts, and that model works.

There has been a large number of posts, involving lots of different drives.

Some people find, that rebooting with it plugged in helps, others don't.

Have been looking at some of the posts, seems like it could be a grub 2 issue? Trying to remove grub2 and replace with grub. But am getting the following error.

rodelita@rodelita-Ideapad-S205:~$ grub-install -v
grub-install (GRUB) 1.99-12ubuntu5
rodelita@rodelita-Ideapad-S205:~$ sudo apt-get purge grub-pc 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

That seems weird. It says it's there but then says it isn't.

BB

---

### Post by hansdown on 2012-01-07
I've seen this with grub3, also,so it probably is not the problem.

The threads I was following, all went dead, so not sure what to advise.

My 10.04 install sometimes does not see my dvd drive, but rebooting makes it work.

---


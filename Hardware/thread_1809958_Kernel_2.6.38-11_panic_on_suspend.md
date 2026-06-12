---
title: "Kernel 2.6.38-11 panic on suspend"
date: 2011-07-22
forum: Hardware
---

### Post by lolwhites on 2011-07-22
Since updating to the most recent kernel, attempting to suspend leads to a kernel panic. I tried suspending before logging in, and the same thing happened.

The machine suspends normally when I fall back to 2.6.38-10.

---

### Post by ST.x on 2011-07-24
I have the same issue with caps-lock led blinking (dell xps m1330) when the laptop lid is closed. But I am using 2.6.38-10-generic-pae #46-Ubuntu SMP Tue Jun 28 16:54:49 UTC 2011

---

### Post by Mystic-Mirage on 2011-07-24
Same for my generic-pae 2.6.38-10 kernel

---

### Post by dcordeiro on 2011-07-24
I'm having exactly the same with my Dell D630.
:(

> **ST.x said:**
> I have the same issue with caps-lock led blinking (dell xps m1330) when the laptop lid is closed. But I am using 2.6.38-10-generic-pae #46-Ubuntu SMP Tue Jun 28 16:54:49 UTC 2011

---

### Post by dcordeiro on 2011-07-24
I just filled a bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/815594](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/815594) . Hope that help.

---

### Post by Sergius14 on 2011-07-26
I have exactly the same issue with 2.6.38-10-generic-pae.

Asus UL30A.

It happens suddenly in the past few days. First, I though that was right after I installed the following updates released on 24/7:

linux-headers-2.6.31-10-rt (2.6.31-10.153)
linux-rt-headers-2.6.31-10 (2.6.31-10.153)


I uninstall them today, but still failing (and IDK why doesn't asked again to reinstall them).

I'm using Ubuntu 10.04 LTS with 2.6.38 backport.

---

### Post by Sergius14 on 2011-07-27
Today I booted with non pae kernel and can confirm that this issue is not happening.

2.6.38-10-generic #46~lucid1-Ubuntu SMP is not affected

generic-pae does.

---

### Post by Sergius14 on 2011-07-27
When this happens, after the forced reboot, the network are disabled.

At the systray I have to put a checkmark to "Enable Networking"

---

### Post by lolwhites on 2011-07-28
Am now able to suspend and reawaken normally. Don't know what changed, but long may it last...

---

### Post by Sergius14 on 2011-07-28
Yes!, me too!

Now is working fine again.


Yesterday I upgraded this packages:

dbus (1.2.16-2ubuntu4.2) to 1.2.16-2ubuntu4.3
dbus-x11 (1.2.16-2ubuntu4.2) to 1.2.16-2ubuntu4.3
libdbus-1-3 (1.2.16-2ubuntu4.2) to 1.2.16-2ubuntu4.3
libpng12-0 (1.2.42-1ubuntu2.1) to 1.2.42-1ubuntu2.2

Then nothing has changed... even I used very little my laptop.

---

### Post by miesogeno on 2011-08-01
for me it was virtualbox 4.1 kernel module.

disable it from starting up by default (I didn't even know it was there), or simply disable them before you suspend.

---

### Post by satya_461 on 2011-08-04
> **miesogeno said:**
> for me it was virtualbox 4.1 kernel module.

disable it from starting up by default (I didn't even know it was there), or simply disable them before you suspend.



u r right.. after uninstalling virtualbox, the kernel panic on suspend stopped.

many thanks to you..

---

### Post by da7oom on 2011-08-05
same thing happen on my x220 thinkpad 

u r right.. after uninstalling virtualbox 4.1, the kernel panic on suspend stopped.

thanks guys

---

### Post by divajsz on 2011-09-08
Hi guys!

Have a look at this : 

Changelog for VirtualBox 4.1
VirtualBox 4.1.2 (released 2011-08-15)

This is a maintenance release. The following items were fixed and/or added:
.......
Linux hosts: fixed random kernel panics on host suspend / shutdown (4.1.0 regression; bug #9305)
.......

You can use Virtual box again!

Tamas

---


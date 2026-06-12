---
title: "ASUS EeePC 1001PX, hard disk clicking"
date: 2010-11-10
forum: Hardware
---

### Post by MeanEYE on 2010-11-10
Hello everyone,

I just received my EeePC today and installed 10.10 on it. Apart from internal Mic not working everything is like it should be. As the day moved on I found out that hard disk makes some weird clicking noise from time to time. This happens only when system is not on AC power (battery powered).

At first I thought that was Ubuntu trying to spin down hard disk in order to preserve battery but after disabling that option (in System -> Preferences -> Power Management) clicking is still present.

Anyone had any experiences with this?

---

### Post by w2ge on 2010-11-10
Sure it's not just the ominous "clicking" of your hard drive head hitting the disk signaling imminent failure? (Danger Danger!!)  It's possible that after all the stress of running, installing the new OP sys, that it pushed your 'already on the brink of about-to-fail' HDD over the edge?  I'd be very wary....

---

### Post by MeanEYE on 2010-11-10
> **w2ge said:**
> Sure it's not just the ominous "clicking" of your hard drive head hitting the disk signaling imminent failure? (Danger Danger!!)  It's possible that after all the stress of running, installing the new OP sys, that it pushed your 'already on the brink of about-to-fail' HDD over the edge?  I'd be very wary....

I thought about that too. But once I plug in the power cord clicking stops. Also, I did whole bunch of disk tests and everything went well. Netbook is like 12h old, so it's unlikely that hard disk is about to fail.

---

### Post by Demask on 2010-11-11
If it only makes that noise when on battery power you should check your power settings (click System --> Preferences --> Power manager, I think) and check if your hardrive is set to "Spin down when possible". The click you're hearing might be the read/write head-thingy "parking".

---

### Post by MeanEYE on 2010-11-11
> **Demask said:**
> If it only makes that noise when on battery power you should check your power settings (click System --> Preferences --> Power manager, I think) and check if your hardrive is set to "Spin down when possible". The click you're hearing might be the read/write head-thingy "parking".

I am pretty sure clicking is the head trying to park. The thing is, I already tried disabling it. That didn't solve the clicking. 

Anyone has any ideas or similar experience.

---

### Post by aryehbeitz on 2011-02-08
This works for me.

sudo hdparm -B 255 /dev/sda
now i need a solution for windows 7, same problem there even when the power is connected

---

### Post by MeanEYE on 2011-02-08
> **aryehbeitz said:**
> This works for me.

sudo hdparm -B 255 /dev/sda
now i need a solution for windows 7, same problem there even when the power is connected

Heh, didn't remember looking at hdparm. Thanks, that really did stopped clicking sounds. I hope Ubuntu team fixes it in the next version.

Thanks again!

---


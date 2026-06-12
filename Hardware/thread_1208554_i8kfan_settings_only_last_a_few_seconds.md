---
title: "i8kfan settings only last a few seconds"
date: 2009-07-09
forum: Hardware
---

### Post by EricDB on 2009-07-09
Hi all,

I have a Dell XPS m1210 laptop and the fan is (almost) permanently on when running Jaunty.

I have installed i8kutils and want to specify that the fan only comes on if the CPU reaches X degrees C - which I have done. However, it only has effect for a couple of seconds.
I can manually execute "i8kfan - 0" to turn the fan off (there's only one), but after a couple of seconds it comes right back on. The same applies if I use i8kfan to turn the fan up to max - it only runs high for a couple of seconds, then back down to medium.

I think it's because something else is controlling the fan (ACPI?) - how can I find this out and disable it, so that only i8k governs the fan?

Thanks
Eric

(This is copied nearly verbatim from an archive post which didn't receive any replies)

---

### Post by neoncode on 2009-07-09
I have a Dell Studio 15 with exactly the same problem. I haven't tried using i8kfan to control the fan but it's stuck on full all the time. In Vista the fan works fine and scales according to what I'm doing.

---

### Post by ischliky on 2009-07-18
i have the exact same problem with an inspiron 1720

regardless of what i set i8kfan to do, it only lasts for a few secs.

if i have i8kmon run as a daemon it will turn off and on constantly every 2 or 3 secs, which im afraid is going to burn the fan out extra fast.

---

### Post by EricDB on 2009-07-20
> **ischliky said:**
> if i have i8kmon run as a daemon it will turn off and on constantly every 2 or 3 secs, which im afraid is going to burn the fan out extra fast.

Yeah, exactly the same thing here.  It's terribly annoying, too...I can't get any work done with that kind of distraction.

---

### Post by ischliky on 2009-07-26
anyone had any luck fixing this? im dreading having to change my OS because of this, but it makes the computer hardly useable sometimes

---

### Post by mts280 on 2009-08-08
Hi all,

I have the same problem and filed a bug: 
[https://bugs.launchpad.net/ubuntu/+source/i8kutils/+bug/410596](https://bugs.launchpad.net/ubuntu/+source/i8kutils/+bug/410596)

please feel free to confirm

---

### Post by Cableless on 2009-08-22
I can confirm the bug on Dell XPS M1310 running jaunty.

---

### Post by ed_qta on 2010-03-20
Same problem on Inspiron 6400

---

### Post by foxhead128 on 2011-10-11
Same issue, Ubuntu 10.04.3 32-bit

---

### Post by overdrank on 2011-10-11
Please start a new thread with your issues. Thread closed.

---


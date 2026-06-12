---
title: "Fan error only when I restart, not when I shutdown and boot (Ubuntu 18.04)"
date: 2020-07-10
forum: Hardware
---

### Post by ericashenden on 2020-07-10
Hello,
  I have read many threads with similar problems but none seem to only happen when the system is restarted, they always seem to happen on every boot. So here's my system and its background, it is a Lenovo T470 and it used to have windows 10 enterprise, but has since been changed to Ubuntu 18.04 LTS desktop. The fan error never happened when I was using windows 10 (right before changing to ubuntu), but the moment I switched its OS to ubuntu I noticed a fan error immediately (during updates). It does happen before the ubuntu splash screen appears, but I'm skeptical it just suddenly failed the moment I switched OSes because like the title says it only happens when I choose restart. If I shutdown then immediately (or wait) boot it then I get no error. The fan still runs fine as I keep an eye on its RPMS and the laptops temperatures using HardInfo System Profiler and Benchmark. I've looked around bios and don't see any settings that might cause this, or anything that is out of the ordinary. I also looked through the boot.log and did a grep "fan" /var/log/* to see if anything come up, but I didn't see anything in the logs. Has anyone seen anything like this before, or do they have a suggestion for something to try? Thank you in advance.

---

### Post by ericashenden on 2020-07-16
Sorry if this bothers anyone, I'll only do this once. Bump

---

### Post by Yellow Pasque on 2020-07-16
Dies it have latest BIOS version?
Does the same thing happen with a LiveUSB of 20.04?

---

### Post by ericashenden on 2020-07-17
Thank you for your help! Yes bios is the latest version. I have not tried 20.04 live boot yet, but I'll try that tonight and get back to you. I'm a little skeptical because once it restarts, I believe it will no longer be booting into the 20.04. Regardless, that is a good step I didn't think of, so I'll definitely be trying it tonight. Thanks again Yellow Pasque, I'll report back tomorrow!

---

### Post by Yellow Pasque on 2020-07-17
You should be able to restart without removing the USB, and you probably already have BIOS set to boot USB before hard disk (or you can manually select it on the reboot).

---

### Post by ericashenden on 2020-07-17
Good to know! I don't really boot live very often. I'll make sure my boot order has usb before my disk. Thank you

---


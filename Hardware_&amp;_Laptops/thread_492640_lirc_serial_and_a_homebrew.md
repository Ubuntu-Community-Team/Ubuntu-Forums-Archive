---
title: "lirc_serial and a homebrew"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by oiper on 2007-07-04
Ok, I'm not a complete dummy when it comes to lirc. I've built a couple of homebrew receivers and set up lirc under Gentoo numerous times. Now, when migrating my Gentoo server to Ubuntu, getting my lirc serial device working seems impossible.

I've followed two how to's on the matter. The most recent being here [http://ubuntuforums.org/showthread.php?t=163496](http://ubuntuforums.org/showthread.php?t=163496) Everything builds, installs, and executes fine except the receiving of a signal. "mode2" just sits there staring at me when it should be outputting signal lines.

I've setup lirc for COM's 1-4 with no luck on any COM. dmesg says
```
[100105.084541] lirc_serial: auto-detected active high receiver
[100105.084557] lirc_dev: lirc_register_plugin: sample_rate: 0

```

I just don't know what else to try. This has had me stumped for days now. I am about to conclude that my device simply broke coincidentally between the hour I shutdown Gentoo and installed Ubuntu. 

So, anyone out there with lirc_serial working with Feisty?

EDIT: I broke out my voltmeter and cracked open my IR device. It's still working.

---

### Post by noof on 2007-07-08
I have a semi-working homemade serial receiver in feisty. irrecord works nicely but irw just sits there and prints nothing. mode2 outputs lots of stuff for me. Do you have /dev/lirc or /dev/lirc0?

---


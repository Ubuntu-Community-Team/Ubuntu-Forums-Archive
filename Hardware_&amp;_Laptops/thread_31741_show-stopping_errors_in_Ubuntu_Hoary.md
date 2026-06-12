---
title: "show-stopping errors in Ubuntu Hoary"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by tanimislam on 2005-05-04
Hello:

I am having insanely unusual, show-stopping errors in running Ubuntu Hoary. Where to begin? Here are the two most severe ones:

1. modprobe does not work properly. I run "modprobe b44 && ifup eth0" from the command line. Shouldn't ubuntu run this automatically? When I restart ubuntu, this setting is "forgotten" -- why? I am using a broadcom BC4401 ethernet card.

2. /dev/input entries are not created. In fact, the directory /dev/input is not created at all, so I cannot run my mouse, and in fact my X server borks b/c it cannot detect the mouse at /dev/input/mice. Again, if I restart ubuntu these entries are forgotten. Why?

I have checked /var/log/messages to get an idea of what occurs. No dice. If possible, could people who have gone through similar or the same errors as the above reply to this message? Thank you.

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=tanimislam]Hello:

I am having insanely unusual, show-stopping errors in running Ubuntu Hoary. Where to begin? Here are the two most severe ones:

1. modprobe does not work properly. I run "modprobe b44 && ifup eth0" from the command line. Shouldn't ubuntu run this automatically? When I restart ubuntu, this setting is "forgotten" -- why? I am using a broadcom BC4401 ethernet card.

2. /dev/input entries are not created. In fact, the directory /dev/input is not created at all, so I cannot run my mouse, and in fact my X server borks b/c it cannot detect the mouse at /dev/input/mice. Again, if I restart ubuntu these entries are forgotten. Why?

I have checked /var/log/messages to get an idea of what occurs. No dice. If possible, could people who have gone through similar or the same errors as the above reply to this message? Thank you.[/QUOTE]
 I can't explain why eth0 was not brought up automatically - but I can explain why what you are doing is not remembered. "modprobe..." is not a setting, it is a command. It is executed - and that's it. If you want it to be executed at each login, you need to change appropriate config files (IIRC, /etc/modules.conf ?)

---


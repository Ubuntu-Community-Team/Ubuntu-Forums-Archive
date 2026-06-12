---
title: "Random lag/freezes in wireless keyboard and mouse"
date: 2014-02-24
forum: Hardware
---

### Post by Jason Pierce on 2014-02-24
Hi. I'm experiencing lags and freezes with my wireless mouse and keyboard. I haven't detected a pattern yet, but when it starts to happen is very annoying. Even toggling on and off the devices doesn't help too much, because after some time the problem appears again.


So far I've tried without success:

[LIST]
[*]Review Xorg.log and kern.log. To my knowledge there's no clear evidence of the cause
[*]Install the latest stable Nvidia driver
[*]Put the USB receiver in another slot
[*]Wait for a kernel update that solves the problem.
[/LIST]


My configuration:

[LIST]
[*]Ubuntu 12.04
[*]Kernel 3.2.0-59
[*]Nvidia 331.20
[*]Logitech MK 250 wireless keyboard and mouse
[/LIST]


I have no idea of what path should I follow to find the causes.




Thanks!

---

### Post by varunendra on 2014-02-25
These wireless devices operate within the same frequency band as the normal wireless network adapters and bluetooth (2.4 GHz). Therefore suspecting a mutual interference, have you tried to use them with both wireless and bluetooth turned off? Does that even make any difference at all?

Have you also taken a look at /var/log/syslog? Obviously we can't do much but guessing if there are no suspicious messages in any of these logs.

---

### Post by Jason Pierce on 2014-02-26
Well, I'm using wifi networks for years and this is the first time I see this kind of problem. I believe we can discard that option.


I've been looking at /var/log/syslog just after one freeze and I haven't seen anything of importance. For now it has happened most times when intensively switching between virtual desktops. Even in the unlock screen I've noticed heavy delays when typing. Maybe it's related with compiz or lightdm somehow.


If you want, I can attach some logs just in case I had passed over the errors.


Thanks!

---


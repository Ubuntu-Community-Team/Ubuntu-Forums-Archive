---
title: "Wifi/WLAN on PackardBell Easynote R1100 with Feisty"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by Frando on 2007-09-05
Hey everyone.

I've an PackardBell Easynote R1100 laptop here with feisty/7.04. Everything works great, apart from WLAN/Wifi which I can't get to work.

According to the PackardBell site the machine has an "Atheros 5BMB5 Wireless network adapter". I think the problem is that there is a software switch for the antenna, controlled by a hotkey (Fn-F1) - the wlan adaptor does not appear in linux at all.

Now. According to [http://ubuntuforums.org/showthread.php?t=255574](http://ubuntuforums.org/showthread.php?t=255574), the wifi adaptor works with the rfswitch module. So I downloaded it, and after patching the source files to use autoconf.h instead of config.h, I was able to successfully compile and install it. After "sudo modprobe pbe5" the module seems to be loaded successfully (according to lsmod). I then editied /etc/network/interfaces as suggested in the mentioned post. 

So far this is what I've done, and it doesn't work.
When pushing the Fn-F1 key combo, /var/log/messages reports [FONT="Courier New"]Unknown key released (translated set 2, code 0x6a on isa0060/serio0)[/FONT]. So, the key not recognized - that's not really important for me, though, as long as there are other means to get wifi to work.
When doing 'sudo ifup ath0', it reports:
"SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0."
And /var/log/messages:
[FONT="Courier New"]Sep  5 17:13:01 nebelheim kernel: [11009.306820] pbe5: failed at request_region()
Sep  5 17:13:01 nebelheim kernel: [11009.306828] pbe5: Radio turned ON[/FONT]

Any ideas? Are there other ways to possibly make wlan work? Or am I doing something wrong?

thanks in advance,
frando

---

### Post by IBG on 2007-12-27
Hi,
I have a packard bell too but a different model.
try to do as root (it wont work with sudo):
echo 0 >/proc/pbe5/radio
pressing the Fn+F1 won't help u much since this key is not handeld by the system.
tell if it didn't  work may be i can help.

---


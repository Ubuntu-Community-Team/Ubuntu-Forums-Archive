---
title: "Networking config question"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by nbcohen on 2008-12-30
I'm a long time Unix/Linux user (going back to 1975, actually), but I just installed Ubuntu for the first time this week. I've been working with various Red Hat distributions since 1995 or so, and have used Fedora at home for a long time.

My current setup does not have DHCP set up for my workstations at home. When Ubuntu starts up, the Network is disabled, and when I configure the eth0 connection with a static IPv4 address, DNS information - it works. The network manager enables the device. However, routes don't seem to be activated. I had to manually add a route to my gateway machine and a default gateway route as well.

None of that would be much of a problem - except that none of the settings are saved. If I reboot the machine, I have to enter all the networking data again. How do I force the system to store that information? Also, I find that I have to enter the data and then manually stop and restart the NetworkManager process in order to get it to connect to the eth0 device - I'd prefer not to do that...

An unrelated question, but maybe someone has a quick answer - I set the screen saver to 'Random' and when it kicks in, the system hangs - has to be power cycled. I changed it to one specific screen saver, and it seems to have run overnight - is that a known problem??? My hardware is about 8 years old at the moment - a Pentium system with an ATI graphics card that I'm hoping to replace in the near future...

thanks in advance,

nbc

---

### Post by zika on 2008-12-30
I've just answered to a similar question: [http://ubuntuforums.org/showpost.php?p=6461701&postcount=5](http://ubuntuforums.org/showpost.php?p=6461701&postcount=5).

---

### Post by albinootje on 2008-12-30
> **nbcohen said:**
>  An unrelated question, but maybe someone has a quick answer - I set the screen saver to 'Random' and when it kicks in, the system hangs - has to be power cycled. I changed it to one specific screen saver, and it seems to have run overnight - is that a known problem??? My hardware is about 8 years old at the moment - a Pentium system with an ATI graphics card that I'm hoping to replace in the near future... 

Certain screensavers in the screensavers have caused problems in the past, I've read bug reports about those before.

A colleague once told me that her Linux installation at home froze from time to time. Later she found out herself that it was due to the screensaver.

Here's one bug report :
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/91132](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/91132)

---

### Post by nbcohen on 2008-12-30
Thanks - I created that file and tried remotely rebooting the system (I'm currently at work). After 10 minutes, I have logged into my gateway machine but it is telling me the host is still unreachable. I'll have to wait until I get home tonight to see whether the settings are gone, or if the NetworkManager just didn't start the connection... I'll reply then if I can't solve the problem...

Thanks for the help,

nbc

---

### Post by nbcohen on 2008-12-30
Small typo in my first edit - corrected that and it worked. Manually setting up /etc/network/interfaces solved the problem - Thanks!

nbc

---


---
title: "kernel panic installing on hp g62"
date: 2011-03-06
forum: Hardware
---

### Post by enriqued on 2011-03-06
Hi, 

First, i want to apologize for my english... :-)

i'm trying to install ubuntu 10.10 32 bit on an hp g62. i started the live cd with the nomodeset option cause if not i get a blank screen.

After a while, the startup process stopped with a kernel panic.

the cpu is intel i3 350m and the graphic card is ATI Mobility Radeon HD 5470.

Any help will be welcome.

Thank you in advance

Regards
        Enrique

---

### Post by didac on 2011-04-20
No need to apologise for your English. Pretty good. Mine is worse.

I have the same laptop. 10.10 installed without problems. Well, actually one: the first installation screen couldn't be seen. It was just too dark. After pressing 3-fingers-salute aka Alt+Ctrl+Del, I got past it unto the desktop. I installed from there.

Then, no sound. In dmesg I could found a kernel oops related to intel_ips. Then edited /etc/modprobe.d/blacklist.conf and added a line:

```
blacklist intel_ips

```

Sound is back and no more kernel oops.

I wonder whether this will help you, if you cannot even install. I don't know how to blacklist intel_ips from the grub prompt.

---


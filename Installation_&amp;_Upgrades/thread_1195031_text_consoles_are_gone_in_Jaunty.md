---
title: "text consoles are gone in Jaunty"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by systemgod on 2009-06-23
Hi,

I installed Ubuntu 9.04 on my Dell Inspiron using the NVIDIA drivers supplied with Ubuntu. The system works fine in X, however when I press Ctrl-Alt-F1(2..6) to get a text console I only see a blinking cursor. 'ps' shows getty is running properly on tty1 to 6. When I run an strace on getty for tty1 while going to the first console, I see it actually does something but I don't see anything on the screen except for the blinking cursor.

Any ideas what might be wrong?

Thanks in advance,

Nico

---

### Post by systemgod on 2009-06-26
bump, snif.

---

### Post by RD1 on 2009-06-26
This isn't any help but, ctrl+alt+f1 ....f6 consoles are working here.

---

### Post by systemgod on 2009-06-26
Hmm, I tried logging in, blind, on one of the text consoles and ran 'ls -lR'. 'ps' from a console in X shows the ls is indeed running. So apparently the keyboard is responsive, I can logon at the text console, I just don't see anything at all except for the blinking cursor.

Also when I turn powerdown the pc I get white bars on my screen but no readable text. Seems like the NVIDIA drivers are messing with the text console

Verry weird

---

### Post by RD1 on 2009-06-26
That is odd! I can't say for sure but, it could very well be a Nvidia problem. Are you using the latest and greatest drivers?

Anyone else have any ideas?

---

### Post by systemgod on 2009-06-26
I'm using the latest proprietary drivers supplied by a regular Ubuntu upgrade. I did not install the NVIDIA drivers myself as I really like the way Ubuntu makes sure everything still works when a kernel update is applied.  I don't know how well Ubuntu tracks the NVIDIA drivers.

Hmm, at closer inspection the installed version appears to be 180.44 while the latest version on the NVIDIA website is 185.18.14, sigh.

Nico

---

### Post by systemgod on 2009-06-26
Hmm, found this link: [http://lcardinaals.wordpress.com/2009/05/11/ubuntu-9-04-x-updates-voor-ati-intel-en-nvidia/](http://lcardinaals.wordpress.com/2009/05/11/ubuntu-9-04-x-updates-voor-ati-intel-en-nvidia/)  (in Dutch unfortunately).  According to the article adding the following line to /etc/apt/sources.list enables installation of the latest NVIDIA drivers.

deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main

Trying it now...

---

### Post by systemgod on 2009-06-26
Well, I'm definitely running NVIDIA's latest driver now

root@erwin:~# cat /proc/driver/nvidia/version 
NVRM version: NVIDIA UNIX x86 Kernel Module  185.18.14  Wed May 27 02:23:13 PDT 2009
GCC version:  gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 

However I still don't see a text console and now even the blinking cursor has dissapeared :)

---

### Post by RD1 on 2009-06-26
uh-oh .... looks like a known bug 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282068]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282068")

---

### Post by systemgod on 2009-06-26
Doh, yep that's what I'm having too. Sigh. Thanks for the link.

---

### Post by amrypma on 2009-07-28
Bump 

same here. no console will have a look.

---


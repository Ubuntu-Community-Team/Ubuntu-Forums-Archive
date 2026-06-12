---
title: "&quot;Input Signal Out of Range&quot; on second monitor - X1400 Vid Card"
date: 2010-05-02
forum: Hardware
---

### Post by landman 1560 on 2010-05-02
I just installed 10.04 on a Dell E1505 with an ATI X1400 (you know, those ancient, not supported cards) video card.

I use a second monitor that is a HannSpree 23".  With the monitor plugged in video will not start on boot up.  If I start without the monitor plugged in everything goes fine.

I then plug in the 23" and "monitor" gui detects it and even gives me the option for full resolution (9.10 wouldn't).  I set it up and then get the message "input signal out of range" and a black screen on the 23".  Everything seems to work fine on the laptop monitor.

I'm not a super noob but I do need step by step directions.  Don't assume I know. :)

Any help would be great as this is my work setup and very important to have working.  Thanks in advance.

---

### Post by landman 1560 on 2010-05-02
Bump

---

### Post by johansandelin on 2010-05-02
This affects me too. These two bug reports seems to describe our problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/537640](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/537640)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541834](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541834)

Comments seem to indicate that it can be solved by disabling KMS, by running ```
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
``` as root and rebooting.

---

### Post by landman 1560 on 2010-05-02
What is KMS?  Is there functionality loss due to disabling?  Meaning re-enabling once they get it fixed?

---


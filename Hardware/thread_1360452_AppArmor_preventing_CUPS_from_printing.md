---
title: "AppArmor preventing CUPS from printing"
date: 2009-12-20
forum: Hardware
---

### Post by ExquisiteDeadGuy on 2009-12-20
Hey all,

I have a printer hooked up to one machine, whenever I use a second machine (both machines running Ubuntu) to send a print job to it, the printer starts queing up, but it doesn't print anything. Looking at the syslog on the machine the printer is connected to shows:

Dec 20 23:11:46 devserver kernel: [  289.820747] type=1502 audit(1261368706.708:10): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=5138 profile="/usr/sbin/cupsd"
Dec 20 23:11:48 devserver kernel: [  291.587312] type=1502 audit(1261368708.470:11): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=5150 profile="/usr/sbin/cupsd"
Dec 20 23:11:48 devserver kernel: [  291.746018] type=1502 audit(1261368708.630:12): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=5154 profile="/usr/sbin/cupsd"


This worked up until about a week ago though I'm not sure what changed. I appreciate any help!

---

### Post by IcarusR on 2009-12-21
Made an incorrect suggestion so have deleted it

---

### Post by ExquisiteDeadGuy on 2009-12-21
At the suggestion of a website, I tried running:

sudo ln -s /etc/apparmor.d/usr.sbin.cupsd /etc/apparmor.d/disable/usr.sbin.cupsd

sudo apparmor_parser -r /etc/apparmor.d/disable/usr.sbin.cupsd


but I still get the same error and printing still won't work... any ideas?

---


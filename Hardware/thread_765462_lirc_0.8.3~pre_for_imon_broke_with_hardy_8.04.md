---
title: "lirc 0.8.3~pre for imon broke with hardy 8.04"
date: 2008-04-24
forum: Hardware
---

### Post by stc77 on 2008-04-24
I have a soundgraph imon with VFD. IT worked very well on 7.04 and 7.10, but I had to build the modules by myself. No I did the upgrade to hardy 8.04 today. At first I was surprised, as the IR worked out of the box. But then later on I noticed, that the computer alway crashes, when I log out. I had a look at the log, and noticed that "lirc" produces errors all the time. By removing "lcdproc" the errors seem to stop, but the VFD does not work. 
System: AMD64-bit, hardy 8.04

The log error (apperas once a second or so):

"... /var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: lcd_write: invalid payload size: 32 (expecting  8 )"

After removing lcdproc I get: 
 "/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: VFD port closed"

Is this the problem?: [http://archives.free.net.ph/message/20071218.201730.401dd0cf.el.html]("http://archives.free.net.ph/message/20071218.201730.401dd0cf.el.html")

---

### Post by länkky on 2008-04-27
Hello,

Same problem here, I also have AMD64 + iMON PAD + 8.04. After 7.10 -> 8.04 update Lirc and LCDproc both broke down. Eventually I got Lirc working again, but LCDproc is just generating faults to syslog.

I found following link with google, where same error message is mentioned: [http://patches.ubuntu.com/l/lirc/extracted/23_pad2keys.dpatch]("http://patches.ubuntu.com/l/lirc/extracted/23_pad2keys.dpatch"). Could it be so that pad2keys patch has something to do with this problem, since it is a new LIRC feature in 8.04??

Has anyone been successful getting LIRC + LCDd to work on ubuntu 8.04 with imon IR/VFD and AMD64?

---

### Post by stc77 on 2008-04-27
Think you are on the right path. So far lirc alone runs here fine. The IR works. But as soon as I activate lcdproc, I get this problem. But the problem seems to be related to lirc (and not a bug of lcdproc). I hope someone can fix this soon.

---

### Post by länkky on 2008-05-02
I made a bug report about this to launchpad:
[https://bugs.launchpad.net/ubuntu/+source/lcdproc/+bug/225594]("https://bugs.launchpad.net/ubuntu/+source/lcdproc/+bug/225594")

---

### Post by jkoyle on 2008-05-04
I have an Antec Fusion case with the VFD display and was having this same problem after upgrading.  From looking at the patch, it looks like the default now for the lirc_imon module is for LCD displays (not VFD).

I added the following to /etc/modprobe.d/options and it solved my problem:

options lirc_imon islcd=0

HTH,
John

---

### Post by länkky on 2008-05-05
Perfect! Thank you for the tip that solved the problem!

I am just wondering where this should be documented so that other people would not have to struggle with this.

---

### Post by angope on 2008-05-06
Using the options lirc_imon islcd=0 disables the LCD panel I suppose are there any patch to make the LCD panel work again?

Best Regards
Anders

Edit: Think I found the answer to my question by my self, didn´t know that there where Imon Pure LCD...:)

---

### Post by stc77 on 2008-05-07
Thanks, it worked. 
Adding ```
 options lirc_imon islcd=0 
``` to ```
 /etc/modprobe.d /options 
```
solved the problem.

This should be automatically recognized for imon VDF at install or at least prompted for.

---


---
title: "Acer aspire one A150 trackpad stopped working"
date: 2010-09-13
forum: Hardware
---

### Post by danielsbrewer on 2010-09-13
Hello,

When I booted up my Acer aspire one A150 this morning the trackpad doesn't work any more.  The pointer just stays in the centre and doesn't move.  Any ideas how to debug this etc.  Is it an update to x.org or a hardware issue?

Thanks

---

### Post by iamgeniusrnti on 2010-09-14
> **danielsbrewer said:**
> Hello,
 
When I booted up my Acer aspire one A150 this morning the trackpad doesn't work any more. The pointer just stays in the centre and doesn't move. Any ideas how to debug this etc. Is it an update to x.org or a hardware issue?
 
Thanks
 
I believe one of your function keys enables and disables the trackpad--sounds like you disabled it.

---

### Post by danielsbrewer on 2010-09-14
That's a good idea, but my wife tried that and it didn't do anything (Fn-F7).  I will try again this evening when I get back home.

---

### Post by iamgeniusrnti on 2010-09-14
> **danielsbrewer said:**
> That's a good idea, but my wife tried that and it didn't do anything (Fn-F7). I will try again this evening when I get back home.
 
Yea--I did that the other day when I was hooking up my netbook to the tv to stream football.  For some reason, that function key won't enable it right away.  I think I hit it and then rebooted and it finally worked.  odd...

---

### Post by iamgeniusrnti on 2010-09-14
I don't think it's F7 btw, I think it's like 3 or 4... but hey, I've been wrong about these things before.

---

### Post by danielsbrewer on 2010-09-14
OK, I'll try that.  Wife said that something comes up on the screen and says it is off when she first presses it and on when she presses it again, so maybe it isn't that?  Is there a command line tool that reads the input for a trackpad seperate from xwindows?

---

### Post by iamgeniusrnti on 2010-09-14
> **danielsbrewer said:**
> OK, I'll try that. Wife said that something comes up on the screen and says it is off when she first presses it and on when she presses it again, so maybe it isn't that? Is there a command line tool that reads the input for a trackpad seperate from xwindows?
 
No there isn't.  I think she is hitting the wrong one.  But if it's the right one, turn it on and then reboot.  Also, I think she is hitting the external LCD button... I don't have my netbook with me right now, sorry.

---

### Post by danielsbrewer on 2010-09-14
[http://eric.chromick.com/aa1/turn-off-the-touchpad-on-the-aspire-one/](http://eric.chromick.com/aa1/turn-off-the-touchpad-on-the-aspire-one/)

I'll have to check when I get back, but the above suggests that that it is FN-F7, but maybe there is something that is ubuntu specific.  Anyway I need to get the thing into my hands.  Thanks.

---

### Post by danielsbrewer on 2010-09-14
OK, so this got a bit weirder.  If I press FN-F7 a notification comes up that it has been turned off.  If I then reboot I can use the trackpad for a couple of seconds while everything is loading, but then it stops dead.  If the trackpad is "on" when I reboot you can not use the trackpad at any stage of the process.  So at least it is a software problem.  So it is like something in UNR is overriding the underlying state of the trackpad, so if the underlying state is off then UNR thinks it is on but it doesn't work, but if the underlying state is on then UNR thinks it is off and turns it off.  Help!

---

### Post by iamgeniusrnti on 2010-09-16
> **danielsbrewer said:**
> OK, so this got a bit weirder. If I press FN-F7 a notification comes up that it has been turned off. If I then reboot I can use the trackpad for a couple of seconds while everything is loading, but then it stops dead. If the trackpad is "on" when I reboot you can not use the trackpad at any stage of the process. So at least it is a software problem. So it is like something in UNR is overriding the underlying state of the trackpad, so if the underlying state is off then UNR thinks it is on but it doesn't work, but if the underlying state is on then UNR thinks it is off and turns it off. Help!
 
Wow--I have absolutely no idea.  Probably post an output of dmesg and or start looking thru the syslog for when it craps out... sorry.

---


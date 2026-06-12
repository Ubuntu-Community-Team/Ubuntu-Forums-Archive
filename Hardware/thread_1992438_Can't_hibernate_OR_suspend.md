---
title: "Can't hibernate OR suspend"
date: 2012-05-31
forum: Hardware
---

### Post by ntnkj on 2012-05-31
I am not able to finish hibernation/suspension processes on my laptop in the last few weeks, and it seems to me it's a USB device blocking the process. I suspect it's the built-in webcam as an internal USB device (if I understand correctly), which stopped working around that time (isn't recognized anymore by cheese, skype or any other program, and it used to work perfectly fine)

P.S. I'm not very experienced in ubuntu stuff, so please be gentle! :D

---

### Post by ntnkj on 2012-05-31
I am using Ubuntu 12.04. I had the same problem on 11.10 and hoped the upgrade would fix it, but it didn't. The machine is HP Probook 4310s

---

### Post by scott1541 on 2012-05-31
I have this issue too on my HP Pavilion DV6-2020sa.  If I try and use sleep I have to perform a hard reset every time. :frown:

---

### Post by ntnkj on 2012-05-31
I don't actually have to do a hard reset, it just goes back to the user authorization screen, as if it just woke up from suspension

---

### Post by ntnkj on 2012-06-01
When I try to suspend, I get a message "unable to enumerate USB device on port 4", while enumeration of ports 2 and 3 finishes fine, than it goes back to port 4, and continues doing that in circles, until 20 sec pass and the system revives

---

### Post by hawkeye314 on 2012-06-04
Hey guys (very new to ubuntu),

I'm suffering from almost the exact same problem,
running the 12.04 on the ASUS X54C
when I choose to suspend or hibernate my laptop it goes to the suspended state,
but no matter what I do - it remains in it, and I must force shutdown (press for a few
secs on the power button), then turn it back on.

anyone ? 

p.s. my windows-using-friends keep laughing at ubuntu :mad:

---

### Post by idoitprone on 2012-06-04
> **hawkeye314 said:**
> Hey guys (very new to ubuntu),

I'm suffering from almost the exact same problem,
running the 12.04 on the ASUS X54C
when I choose to suspend or hibernate my laptop it goes to the suspended state,
but no matter what I do - it remains in it, and I must force shutdown (press for a few
secs on the power button), then turn it back on.

anyone ? 

p.s. my windows-using-friends keep laughing at ubuntu :mad:

please post make your own thread, since hardware issues like these usually have different solutions.
because acpi is abominable crap produced by intel

Here I guess you your issue in particular 
one fixes suspend and the other maybe works for your laptop
[http://ubuntuforums.org/showthread.php?t=1979490](http://ubuntuforums.org/showthread.php?t=1979490)
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)


make sure you have more swap than ram before you hibernate

---

### Post by sscaff1 on 2012-06-04
> **idoitprone said:**
> please post make your own thread, since hardware issues like these usually have different solutions.
because acpi is abominable crap produced by intel

Here I guess you your issue in particular 
one fixes suspend and the other maybe works for your laptop
[http://ubuntuforums.org/showthread.php?t=1979490](http://ubuntuforums.org/showthread.php?t=1979490)
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)


make sure you have more swap than ram before you hibernate

I tried this solution and it's not working for me. I have a HP Pavillion dv6 laptop. Running the ATI/AMD proprietary FGLRX graphic drivers. I can't suspend my laptop at all (I tried all methods). Let me know what other information you need. Also I'm running 12.04.

---

### Post by idoitprone on 2012-06-04
> **sscaff1 said:**
> I tried this solution and it's not working for me. I have a HP Pavillion dv6 laptop. Running the ATI/AMD proprietary FGLRX graphic drivers. I can't suspend my laptop at all (I tried all methods). Let me know what other information you need. Also I'm running 12.04.

like I said. laptop vary in model, make and bios.  A solution for the OP does not work for you. This is why you have to start a new thread.

That solution I posted is not for you but hawkeye

---

### Post by ntnkj on 2012-06-05
Does someone has any ideas for the actual creator of this post - me? :D

---

### Post by idoitprone on 2012-06-05
> **ntnkj said:**
> Does someone has any ideas for the actual creator of this post - me? :D

sorry I cannot find anything on your laptop
[http://www.linlap.com/wiki/hp+probook+4310s](http://www.linlap.com/wiki/hp+probook+4310s)

it does not say anything about suspend issues

---

### Post by ntnkj on 2012-06-05
> **idoitprone said:**
> sorry I cannot find anything on your laptop
[http://www.linlap.com/wiki/hp+probook+4310s](http://www.linlap.com/wiki/hp+probook+4310s)

it does not say anything about suspend issues
The thing is that it used to suspend and hibernate perfectly well, as I already stated in the first post, but there is process (which I suspect is connected to the malfunctioning camera) which stops it from suspending in the last month or so.

---

### Post by ntnkj on 2012-06-08
It fixed itself after installing some updates... Both the camera and the suspend issue... Should I mark it as solved?

---

### Post by togo59 on 2012-07-17
Same problem. Updates didn't fix. So IMHO not solved!

---

### Post by Toz on 2012-07-17
@ntnkj, yes, as creator of this thread, if the issue is resolved, please mark it as solved.

@togo59, please create a new thread and include specifics about your computer including the make and model. Contents of the /var/log/pm-suspend.log file would be also helpful along with any troubleshooting steps you may have already tried.

---


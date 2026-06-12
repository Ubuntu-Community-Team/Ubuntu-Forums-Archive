---
title: "Dell Inspiron 9300 Video Drivers"
date: 2011-07-16
forum: Hardware
---

### Post by LiteDrive on 2011-07-16
I'm having some video driver issues: when I try to detect the hardware drivers nothing pops up from the additional hardware screen. In fact, all I get is a "No proprietary drivers are in use on this system." I'm running a Dell Inspiron 9300, and was wondering if anyone else has had any problems with video hardware in Ubuntu. My Ubuntu is 10.10 atm.

Is there any fix for this, so it may detect hardware? I tried installing everything from apt using the regex ^nvidia, but still nothing has popped up from that. When I check my NVidia X server settings, I get a message telling me that my X driver currently isn't in use, so I must still be running this without anything. 

Thanks.

Update:

I just tried turning on the Extra video settings in the Change Desktop panel, and wow... I have honestly never seen anything more screwed up on a desktop before. Everything looked like it was written in Russian, and my desktop was turned upside down : /

---

### Post by LiteDrive on 2011-07-16
Brainfart: sorry, I just found out that the drivers which come with an Inspiron 9300 are of the ATi breed. My video card is x300. 

A new problem: After attempting to install the proprietary drivers, the installer crashes and doesn't respond after about 3 seconds of running in terminal. Has anyone else experienced this? If so, what was your method for rectifying the issue?

---

### Post by deusexcalibur on 2011-07-16
I have an Inspiron 6000 which also has an ATI X300 and it has been nothing but trouble for me as well.

I made a thread here about my troubles with getting a decent driver: [http://ubuntuforums.org/showthread.php?p=11055379#post11055379](http://ubuntuforums.org/showthread.php?p=11055379#post11055379)

Maybe some info there can help you.

---


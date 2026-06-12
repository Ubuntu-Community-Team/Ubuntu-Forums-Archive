---
title: "New nVidia GT440 graphics - unknown"
date: 2012-05-26
forum: Hardware
---

### Post by samwillc on 2012-05-26
Hi everyone,

Installed my new graphics card, used the 'additional drivers' to get the latest nvidia drivers.

However, in system settings, it still says 'Graphics - unknown' even though everything seems to be in full working order.

Should this not say GT440? Or maybe it doesn't matter. Any advice would be great.

Thanks.

Sam.

---

### Post by Yellow Pasque on 2012-05-26
That's just a common bug with sysinfo program. Don't worry about it.
(IIRC, you can fix it by installing mesa-utils.)

---

### Post by samwillc on 2012-05-26
Thanks.

But now I have a more pressing issue, I copied all my files in, everything was going fine, then I tried logging out > black screen, nothing.

Tried again, same thing. Then, turned on, ubuntu loaded up, then launcher disappeared then black screen (without a log out this time!).

What the hell is going on?? nVidia GT440 with additional drivers installed. My system appears completely unstable so how am I supposed to use this for work?!

I added the swat x update (or whatever it is) ppa, and got driver 295.xx (or something), on another pc at the mo, having to reinstall again on the other one. The latest driver just doesn't work for me. Maybe there is something in the nvidia x server settings program itself I need to change? The program install correctly after adding the ppa and I can access it. Just black screen on logout.

Any help please.

Sam.

---

### Post by samwillc on 2012-05-26
Sorry can I add:

Did the apt-get stuff, now running the NVIDIA X Server settings.

Driver: 295.53
GPU 0: GeForce GT440

So it knows my card! At least that's something. The logout problems persists though.

**edit** a restart into safe mode gave me a black screen with a bunch of info, one line which said "no screen found". Rebooted and ended up with the wrong resolution of 1600 or something. Supposed to be 1920 x 1080 p 60Hz. That's the native display.

At boot, my screen has a 1inch black border, and in the splash screen, and in the logout screen (even though it's black you can see where the background is supposed to be). Maybe the resolution  settings are not being kept or something?

Sam.

---

### Post by samwillc on 2012-05-27
[SOLVED]

Thanks to [QIII]("http://ubuntuforums.org/member.php?u=628170") and the superb guide here:

[How do I install the ATI driver]("http://ubuntuforums.org/showthread.php?t=1982640")?

My solution was to not waste any more time farting around with an nvidia card that clearly has problems. So, took it out, packaged it up ready for a refund, stuck my old HD5450 in the pc, and followed the guide.

No problems so far and a lesson for myself to listen to both sides of the fence before making hardware decisions!

Sam.

---


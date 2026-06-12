---
title: "Problems with SNA acceleration on intel videodriver aka black screen on logon."
date: 2013-10-19
forum: Hardware
---

### Post by Gribs on 2013-10-19
[SIZE=3]Problem[/SIZE]
After fresh installation of kubuntu i've got completely black screen instead of logon screen. I was able to switch to tty1 by using ctrl-alt-f1. No error messages on /var/log/Xorg.0.log. I was able to run kde session on tty8 by executing startx, but seems that opengl did not work. If instead of this kill Xorg process it starts again, sometimes successful. 

[SIZE=3]Hardware[/SIZE]
Lenovo thinkpad edge e420s with Intel HD Graphics 3000 video. 

[SIZE=3]Temporary solution[/SIZE]
If somebody encountered this problem solution that worked for me was to disable SNA hardware acceleration. You can check if it is active running
```
cat /var/log/Xorg.0.log | grep SNA
```

To disable SNA you need to create /usr/share/X11/xorg.conf.d/ folder (let it be 20-intel.conf) with next lines: 
```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod"  "uxa"
EndSection
```

and restart xserver (kill X.org process or reboot or ctrl-alt-Backspace). 

Actually this may help you if you sometime have Xserver freezes with error [drm:i915_hangcheck_ring_idle]. 

[SIZE=3]Question[/SIZE]
Is it a bug? Who has the same problem (I assume that there is a lot of installation ubuntu 13.10 on low cost laptops with the same graphics, but it is not seem that all of them have the same error). Is it possible to make SNA work on HD Graphics 3000? Who has the same error, or who has no problems with SNA on the same videocard?

---

### Post by bquigley5 on 2014-03-29
Thanks for the post Gribs. This helped me to solve a problem that I was having with my muxless intel/radeon laptop.

---

### Post by sudodus on 2014-03-29
Welcome to the Ubuntu Forums :-)

First of all, thanks for sharing your 'temporary solution' :KS

UXA acceleration is what I recommend for very old Intel graphics (typically 10 years old). I think the problem started with 13.10 'Saucy', and it is there also in 'Trusty' to become 14.04 LTS.

I think the support for some Intel graphic chips has been dropped or deteriorated. I think it is a bug. Report the bug to Launchpad, and chances are that someone will try to fix it, now that it appears also for newer Intel graphics!

But you a new here (with one bean, but the joining date tells another story), and I do not expect that you are ready to create bug reports. Do it if you have the time and would like to learn something new.

---


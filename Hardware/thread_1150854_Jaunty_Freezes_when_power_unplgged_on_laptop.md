---
title: "Jaunty Freezes when power unplgged on laptop"
date: 2009-05-06
forum: Hardware
---

### Post by ddarsow on 2009-05-06
I have a DELL Latitude D620 which is currently dual booting with Hardy and Jaunty. I am having an annoying problem with Jaunty which does not happen with Hardy.

The trouble is that if I unplug the AC adapter the computer freezes up. The keyboard, mouse, etc. do not work at all. The only way to recover is to do a hard power-down and then reboot. This happens while running Jaunty only, not with hardy.

If I boot into Jaunty on battery power it runs fine. Plugging in the power cord does not cause the issue, only unplugging it.

This is the only issue I am having with Jaunty, but it can be really annoying at times. Any thoughts?

---

### Post by ddarsow on 2009-05-08
bump...

---

### Post by wabbalee on 2009-05-08
Not that this is going to help you fix your problem but there are other ways to reboot a linux system before pushing the hard reset button:

Alt+SysRq+r ( The LEFT Alt key ) ( SysRq is on the same button as print screen )
Alt+SysRq+s
Alt+SysRq+e
Alt+SysRq+i
Alt+SysRq+u
Alt+SysRq+b 

to remember the letters: Rasing Skinny Elephants Is Utterly Boring

if your system still responds to switching to a virtual terminal (e.g. ctrl+alt+F2)
you can see what happens when you give these keystroke combinations. the last one eventually reboots the system, but it is adviseable to do them all in this order, for the sake of your hard drive and filesystem.

---

### Post by hansdown on 2009-05-08
wabbalee is right. r-s-e-i-u-b works just as well as r-e-i-s-u-b, which is 

busier spelled backwards.

[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

---

### Post by ddarsow on 2009-05-09
The replies from wabbalee & hansdown would be quite useful, but for the fact that neither the mouse nor the keyboard work when the freeze happens!

On the brighter side, I installed the new 2.6.28-12 kernel yesterday and the problem seems to be gone. I still have no idea what was causing it, but so far so good with the new kernel.

---

### Post by fpeixoto on 2009-07-27
I have the same problem, but I use the 2.6.28-13-server.  Happens randomly though.  I had a feeling it was the unplugging of my USB hub that did it, but seeing the OP makes me question my theory.

Where should I start looking for clues?

---

### Post by wabbalee on 2009-07-28
I run Jaunty on my Acer TM2480 without this problem, it all seems to work well even coming out of sleep/stand-by mode, fill in password and working!

but if I did have this problem, I would want to know for certain if the problem was Jaunty specifick by either booting into Hardy and see if it occurs there as well or even a whole other distro all together. 

if it occurs in all then I would check BIOS settings relating to this event and if that did not help then finally check for faulty hardware, shouldn't take too long all together. without being too technical.

..and I don't want use the M-word but if you still have a Microsoft Distro on there I would try that one too, just to see...

if none of the above worked then I would wait here and hope that a Guru will reply to me, before I start talking French with myself.

---


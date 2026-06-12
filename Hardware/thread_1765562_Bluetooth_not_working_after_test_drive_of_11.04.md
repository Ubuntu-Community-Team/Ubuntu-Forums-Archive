---
title: "Bluetooth not working after test drive of 11.04"
date: 2011-05-23
forum: Hardware
---

### Post by Rocket J Squirrel on 2011-05-23
I initially inquired about this in the General Help forum but it was suggested I bring it over here. I don't know if it's possible to re-direct a thread, so I'll just point to it: [http://ubuntuforums.org/showthread.php?t=1764142](http://ubuntuforums.org/showthread.php?t=1764142)

Summary: My netbook running 10.10 fine has stopped seeing my Bluetooth mouse. This after test-driving Ubuntu 11.04 from a Live USB. More details including a screen shot and things I've tried on the above link. 

The batteries in the mouse are fine: the power light goes green on turn-on and I tried a second pair. It's unlikely that the mouse just broke when I went back to 10.10, more likely that the 11.04 Live USB clobbered something on the HD. 

I bet someone here knows some commands I could run in Terminal to help diagnose what happened. Many thanks in advance for help.

---

### Post by ajgreeny on 2011-05-23
The live USB you used will not have written anything to the hard disk unless you told it to, and I think you would have to do that as root using sudo, so you couldn't do it accidentally.

Look elsewhere, I suspect for the answer to your problem, though never having used bluetooth I can not suggest anywhere to look.

---

### Post by Rocket J Squirrel on 2011-05-23
Thanks, ajgreeny.

Sure, it's possible that the failed communication with the mouse was entirely coincidental with the Live USB experiment. But it would be pretty tight timing. 

When I booted to the USB, I didn't bother to connect the Bluetooth to the mouse, figuring if 11.04 behaved well I'd get around to it. 

Booting back to the HD took a bit of work -- even with the stick removed from the USB port, Unbuntu still wanted to boot into 11.04, which I found magical and amazing. 

I had to F2 into the computer's bios and bring the HD to the top of the boot list to get into 10.10. Still have no foggy idea whatsoever how 11.04 got a toehold.

But anyway. Once 10.10 re-loaded, the BT can no longer see the mouse. 

Something fishy happened and I know it wasn't because I picked some "install in partition on HD" thing or anything like that. I approached the test drive with caution. 

So . . . if anyone has any good troubleshooting steps it would be helpful.

---

### Post by Rocket J Squirrel on 2011-05-24
Um . . . anyone?

---


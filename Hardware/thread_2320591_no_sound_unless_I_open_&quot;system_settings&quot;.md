---
title: "no sound unless I open &quot;system settings&quot;"
date: 2016-04-15
forum: Hardware
---

### Post by walterramjet on 2016-04-15
after several updates (october 2015), my sound stopped working.  I found that by clicking on "system settings" (the little gear and wrench icon), my sound returned. I can close system settings and my sound continues to work, but every time I login, I have to click on "system settings" before my sound works. Is this normal?

I am using ubuntu 15.10 (64-bit), linux-image-4.2.0-35-generic
Memory:  5.8 GiB
Processor:  Intel® Core™ i7 CPU 920 @ 2.67GHz × 8 
Graphics:  Gallium 0.4 on AMD RV770 (DRM 2.43.0, LLVM 3.6.2)

---

### Post by T.J. on 2016-04-16
No, it is definitely not!

Try checking if Pulseaudio has been disabled on login.  You can do that in a terminal with*  ps x | grep pulse. * 


You should see something like this:

1272 ?        S<l    0:03 /usr/bin/pulseaudio --start
 1343 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 1354 ?        S      0:00 /bin/sh /usr/bin/start-pulseaudio-x11
 3889 pts/1    S+     0:00 grep pulse



If it comes back without the top 3 lines, the sound has been deactivated.  You will need to go to the startup area in your desktop environment (it varies - depending on what you are using) and add the *start-pulseaudio-x11* command to the list.  After that, log out and back in again.  It should be fixed.

If it comes back normal, check your sound levels to see if it has been muted.  It may be as simple as that.

If that doesn't do it, please let me know.

---

### Post by walterramjet on 2016-05-01
Hi T.J.,

I did what you said and for the command, ps x | grep pulse

it returned the following:
 2712 ?        S<l    0:00 /usr/bin/pulseaudio --start --log-target=syslog
 3140 pts/17   S+     0:00 grep --color=auto pulse


that doesn't look like it should.  i dont know how to change it.  You were saying i should do something to my desktop environment and add a line to the list.  is there a file I should edit?  

Thanks for the great help.  it looks like i'm going in the right direction.  finally :D

walt

---

### Post by walterramjet on 2016-05-01
i figured out how to add a line to my startup.  something called startup applications preferences.  
after saving and rebooting, the sound worked like you said it would.

after trying this command, ps x | grep pulse, the message returned changed only slightly.  I really dont know what it should look like, but the sound seems to work.
thank you!
walt 

 2538 ?        S<l    0:02 /usr/bin/pulseaudio --start --log-target=syslog
 3013 pts/2    S+     0:00 grep --color=auto pulse

---


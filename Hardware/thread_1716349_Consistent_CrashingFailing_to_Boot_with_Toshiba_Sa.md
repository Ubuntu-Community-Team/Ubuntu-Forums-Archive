---
title: "Consistent Crashing/Failing to Boot with Toshiba Satellite T115-S1100"
date: 2011-03-28
forum: Hardware
---

### Post by CaptainCouch on 2011-03-28
Hello, Ubuntu Forums!

After searching around the web and these forums for a friend of mine who would really like to begin using Ubuntu, I decided to ask about a problem of his for which we have not been able to solve ourselves.

The problem is this: after installing Ubuntu 10.10 on his Toshiba Satellite T115-S1100, he has experienced system crashes after closing the lid, even when it has been set to show nothing but a blank screen for both AC power and battery power, and subsequently, cannot boot Ubuntu from GRUB, as the computer only restarts after making the selection from the menu. Updating the system and restarting has not proven to be helpful. In addition, he has also experienced issues without closing the lid, in which Ubuntu does not recognize the presence of any wireless networks and crashes on every other startup.

Is there a possible fix for this issue?

Thank you very much!

---

### Post by Jevmann on 2011-05-20
I have a friend with the same problem. Unbuntu 10.04 on her Toshiba Satellite kept crashing after going into hibernate, and then after the last update, she is unable to boot from GRUB, no matter which option she chooses (except Windows, how ironic).

I see the message:

Target filesystem doesn't have s/bin/init.
No init found. Try passing init= bootarg

I cannot boot into the LiveCD at all, it just hangs, and when I hit ESC I see the process has been killed because no user is found.

I'm now going to attempt to boot in with an 11.04 LiveCD to see if I can at least get into the system.

Anyone have a fix for this problem?

*************************

Using the 11.04 Live CD I managed to log into Ubuntu and run 

fsck -y /dev/sdaX where X is the number of the extended partition (which I located by opening GParted)

A whole bunch of things got fixed and voila! I can restart and login again!

---


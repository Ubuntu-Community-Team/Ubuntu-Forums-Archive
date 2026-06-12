---
title: "SD Card Reader Problem..."
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by ghstzr0 on 2006-08-31
I own a Fujitsu Lifebook T4010 Tablet/Notebook which comes with a SD card reader.  I know the device works because the computer came with Window XP and it worked on there.  I have installed Ubuntu (dapper) 6.06 on my tablet and all has gone well so far (I even got the pen & digitizer to work!).  Now I have realized that my SD slot won't recognize cards when I insert them.

I looked in the device manager and there appears to be drivers installed for it... I think:  I see a 'OZ711M3/MC3 4-in-1 MemoryCardBus Controller/Accellorator which appears to have driver 'yenta_cardbus' installed.

What could be causing my card reader to not work?  Please advise!

---

### Post by Zed on 2006-08-31
People have had a lot of trouble with SD cards and Linux. Here's [a thread](http://www.leog.net/fujp_forum/topic.asp?TOPIC_ID=9304) from another forum about a different Fujitsu model; the links and references there may be of use.

[Someone here](http://ubuntuforums.org/showthread.php?t=214157) reported that the SD reader could a read a card that was already there at start-up, but not one inserted afterwards.

---

### Post by ghstzr0 on 2006-08-31
Thanks for the suggestion.  The link you provided appears to be about a device other than my O2Micro device.  I sent an email to O2Micro figuring that the more they get asking for linux drivers, the more likley they'll release one.

If anyone else has experience, or has gotten this to work, please reply...  Thanx!

---

### Post by ianmillington on 2006-09-01
I have a Dell 630m with a card reader.

It did not work until I installed the restricted modules relevant to the kernel I was running. After that, no problem as an inserted SD card was automatically detected on the desktop (kde)

Ian

---


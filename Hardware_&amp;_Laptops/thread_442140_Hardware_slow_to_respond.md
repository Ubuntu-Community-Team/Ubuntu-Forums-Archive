---
title: "Hardware slow to respond"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by danbert on 2007-05-13
I just installed a fresh copy of Fiesty Fawn and I have a slight problem.  The system would run fine, but every 30 seconds or so, my system becomes unresponsive for awhile, and then is fine again.  Upon further investigation, every time my system temporarily freezes, the IO Wait usage on my system monitor spikes and takes 100% of my processing time.  I assume this is misbehaving hardware that is not responding and the system is waiting on it.  How can I check what hardware is the problem?  When the system is running normally, everything works correctly, so there is no red flag as to what the problem might be. Thanks for any help.

---

### Post by danbert on 2007-05-13
I checked the Hardware Information tool in the system menu and all my hardware appears to have been detected correctly.  I also noticed that when it boots up it hangs and tells me that my root drive appears to be mounted read-only (it's ResiserFS).  Could this be a problem that I can fix?

---

### Post by danbert on 2007-05-15
You're telling me that there is no one on these forums that can tell me a simple console command to check hardware compatibility?  Or even where to start looking?  /bump for at least a reply of "Sorry sucker, you're outta luck"

---

### Post by danbert on 2007-07-29
Been awhile, I've been living with the issue,  However, I have been doing some research.  The problem still exists in testing versions of Gusty, as well as in fresh installs of Fiesty.  However, I went back and installed Dapper, and it works just fine.  What could have changed from Dapper to Fiesty/Gusty that would have caused my IO wait to spike randomly?  Maybe a buggy driver update?

---

### Post by fredj on 2007-07-30
There can be many different causes of this sort of problem so don't be surprised if no one can give you
a quick answer. When it hangs, can you still move the cursor around the screen. If you can then try to
find updated firmware for your DVD/CD drive.

---

### Post by danbert on 2007-08-01
Yes, I can still move the cursor around fine.  And it isn't the entire system freezing, it's individual applications that stop responding.  Like if I were using Firefox, it would stop accepting any input, but I could go over to Pidgin and chat fine.  It really doesn't make any sense, and I could use any hints to diagnose specifically what is the problem because it seems to affect all applications and it doesn't matter what I am doing when it happens.

---

### Post by fredj on 2007-08-01
I had the same problem on a sony vaio notebook. I fixed it by upgrading the firmware in the TSST
DVD drive. I think the problem was caused by Ubuntu polling the DVD at regular intervals to see
if a disk has been inserted and not getting a reply from the dvd, so it waits for a timeout before
giving up.

---

### Post by danbert on 2007-08-05
I found the updated firmware for my DVD-RW drive (Lite-On SSM-8515S), but the firmware is a windows executable installer.  I suppose, i'll have to install windows to fix it...

Alternatively, is there a way to disable automounting on the drive?  I rarely use the drive, and could easily mount it myself when needed.

---

### Post by fredj on 2007-08-05
As an alternative try leaving a mountable cd or dvd in the drive at all times and see if this fixes it.

---

### Post by danbert on 2007-08-25
So far, neither the firmware update or leaving a mounted cd in the drive has changed anything.

Also, I've notice a trend that the frequency and duration of the io-wait lag is highest at system startup, and slowly becomes less common after the system runs for awhile.  Thus, I've started to use suspend a lot more, but since this is a laptop, I do have to shut it off when I can't plug it in.

---


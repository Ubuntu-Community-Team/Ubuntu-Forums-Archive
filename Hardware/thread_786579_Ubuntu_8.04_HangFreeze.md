---
title: "Ubuntu 8.04 Hang/Freeze"
date: 2008-05-08
forum: Hardware
---

### Post by SRParda on 2008-05-08
I'm having a big problems with Ubuntu 8.04, system Hang / Freeze totally, no mouse move, no keyboard response, no message, no error logs generated. And all this in three different installations.

First, It occurs with the liveCD, making the previous backup for update from 7.10 to 8.04 (but don't give it importance)

After update I was having random hangs, usually when using it, don't hang if I'm not using interactively. (I thing about a problem in old configuration, or kde)

So I decided, to do a clean installation, (with gnome desktop only) and deleting /home partition with old config and the same problem appeared.


I checked the memory during 2 hours and it's ok, and don't hang in the test. So I'm sure about some bug in 8.04.


My laptop is : Sony VGN-A117S.
With an Intel 855 mobile chipset, and an ATI Mobility Radeon 9700. And a Pentium M 735 1.7Ghz Processor, and 2GB Memory. Using the Centrino integrated WiFi.

---

### Post by mcwizard on 2008-05-08
I'm having the same issue.  Just hard freezing, complete lockup, can't drop to shell or use the alt-sysrq key combos to reboot. It's getting really annoying, sometimes it happens a couple times a day.  Google earth seems to be pretty consistent at locking it up. I've checked a couple log files and haven't seen anything out of the ordinary like a kernel panic or any errors that would indicate something is wrong.

---

### Post by jszzang on 2008-05-08
I have exact same problem and it looks like it will be hard to solve this issue. cause i lost all my inputs.

---

### Post by mcwizard on 2008-05-08
I've waited all day with heavy use (music playing, google earth doing random tours, firefox loaded with multiple tabs, etc.) for the problem to finally repeat itself and checked all logs in /var/log after a hard reboot with no indication of anything out of the ordinary at the time of the lock up. 

Anyone have any idea where else to look besides /var/log?
 
***edit***  seemed to be related with firefox, 2 times now after clicking a link it froze, less than 5 mins after reboot it happened again. I tried to repeat the exact situation running firefox from the command line to see if any errors popped up, so far nothing.

I'm going to try running 2.6.24-12 kernel for awhile to see if it still happens.

---

### Post by SRParda on 2008-05-09
Hi,

I'm using my laptop all the day with the wired card instead of wireless, and it has worked without hang, browsing Internet all day was impossible before .

So in my case It's likely a wireless network problem. I have post a bug.

I hope they find the bug fast.

---

### Post by LokeTheDog on 2008-05-09
I've been getting it too, seems related to losing internet connection.

---

### Post by jszzang on 2008-05-09
Ok mine has been working for 30 minutes today. (it was hung after 10min yesterday. :-( )

This is what I did.
>sudo dpkg-reconfigure xserver-xorg

Please try reconfigure your X.

See whether it solves the problem.

---

### Post by jszzang on 2008-05-09
I think my problems are gone. As i told the previous reply, I did X reconfigure and updated to the latest version.

---


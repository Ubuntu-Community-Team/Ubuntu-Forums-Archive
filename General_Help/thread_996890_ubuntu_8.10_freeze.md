---
title: "ubuntu 8.10 freeze"
date: 2008-11-29
forum: General Help
---

### Post by rcoble on 2008-11-29
hello, new linux user. i am using ubuntu 8.10 and have been happy with the performance. the only problem is that i leave the computer on all night for torrents etc... when i leave the computer idle sometimes i find that the computer has frozen and the capslock key is blinking. i have to manually restart the computer. any ideas on how to fix this? thanks

---

### Post by OrangeCrate on 2008-11-29
Random freezes are hard to diagnose. Usually, the first thing to do, is to insert a Live CD, and check your memory with Memtest. Let it run, at least 10 complete cycles, to let the algorithms put a heavy load on the memory.

---

### Post by robroy911 on 2008-12-04
I am having the exact same issue with my Laptop Acer Aspire 7720 Laptop.  Machine works fine for a time, then freezes.  The Caps lock light blinks on and off.  I am running this as a dual boot w/ Vista ultimate.  Has worked flawlessly until tonight. Happened twice in a two hour period.

---

### Post by Stargazer989 on 2008-12-05
i'm having a similar problem on my Gateway MC7081u. unfortunately i have no caps lock light (BS, imo), so i have no blinking. but every time i startup, it's a hassle cause i don't know when intrepid will start without stopping up and when it won't. it'll show that 'checking battery...' thing every-so-often. the screen'll blink a couple of times... then back to the battery checking screen... and the cycle'll repeat over and over until i hit either the power button or ctrl+alt+del.

if ANYONE has a suggestion on how to fix this, PLEASE tell me. i don't like it how i have to wait nearly 5min to make sure it's in it's "fit," so to speak, and then have to restart it for intrepid to boot into low-graphics mode and then another restart for regular usage.

---

### Post by phonixor on 2008-12-29
oooh... i am having the same problem...
started another thread cause i thought it was hardware related...
but if more people have simular problems it might be software related after all... ... even though my comp also crashed during memtests 

:popcorn:

---

### Post by Stargazer989 on 2008-12-30
[http://ubuntuforums.org/showthread.php?t=999255]("http://ubuntuforums.org/showthread.php?t=999255")
started a thread because this is just too much...

---

### Post by euclidsbrother on 2009-01-03
hmm.. i'm having this issue too.. Dell XPS m1710 using ubuntu 8.10 64bit installed to a Kingston 4gb flash drive.  I never had the problem with 8.04 32bit, nor the 8.10 32bit (but only had the 8.10 32bit a copule of days).

Left computer running idle all nite and today both capslog and numlock lights were blinking and screen black and everything unresponsive.  I did not that a spot just to the right of the power button above the keyboard was very very hot..  A reboot brought everything back to normal and that spot is not hot anymore..

this could be a heat related issue..

-EB

---

### Post by utnubuuser on 2009-01-03
Is this a screen-saver issue? Have you tried disabling the screen-saver?

---

### Post by euclidsbrother on 2009-01-03
I'll test that out.. I just disabled screen saver (it was on "black screen").  I'll leave it running tonight and see in the morning.. if all is well, i'll turn it back on and try it again the next nite.. will post back..

---

### Post by Seks on 2009-01-03
sounds like a kernel panic 

I've never had one (even though I have caps lock lights and my system has locked up), but that's what it's called.

---

### Post by euclidsbrother on 2009-01-04
> **utnubuuser said:**
> Is this a screen-saver issue? Have you tried disabling the screen-saver?

Nope doesn't seem to be a screen saver issue.  with screen saver disabled, it still locked up overnight with capslock and numlock lights blinking.  Desktop still showing since screen saver was not running, but no activity.  CPU Scaling monity showed 1Ghz (on a 2.33Ghz cpu).  Again, it was very hot near the power button, but cooled down quickly once rebooted.  Conky was the only thing that was even remotely using CPU% at the time of the freeze.

Any other thoughts to what could be the cause?  Is there a log somewhere that might shed some light?

Thanks
-EB

---

### Post by euclidsbrother on 2009-01-04
I think the issue I'm having is what was described in this thread:
[http://ubuntuforums.org/showthread.php?t=1008478](http://ubuntuforums.org/showthread.php?t=1008478)

When the CPU is scaled down, the fans don't run or run slower and allows the CPU to get too hot.  I set it to not scale down (stays on 2.33Ghz) and left it for a couple of hours and it did not freeze up.

If only there was a program that could monitor the temperature vis "sensors" and turn the fans on/off..  hmmm

-EB

---

### Post by euclidsbrother on 2009-01-05
I let it run all night and still no freeze..  as long as the Frequency Scaling Monitor is set to "2.33Ghz" and not "On Demand".

It might be time to take it apart and clean the fans.. lol

---


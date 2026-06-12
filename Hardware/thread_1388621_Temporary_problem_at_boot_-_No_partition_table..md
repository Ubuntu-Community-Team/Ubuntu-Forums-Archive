---
title: "Temporary problem at boot - No partition table."
date: 2010-01-23
forum: Hardware
---

### Post by ajgreeny on 2010-01-23
I'm running jaunty 32bit on a Sempron 2400+, 2GB ram ati 9200se graphics card and Maxtor 160GB hard disk on an Asus A7N8X-X MBoard.

Occasionally on booting, after grub, the UUID of the ubuntu partition show, and the words "Starting up" appear, then the computer goes no further; I don't see "Loading, please wait", which is what normally appears.  A press of the reset button usually gets it running fine after that.

Last night I was playing around updating the almost unused windows XP which I needed for a refresher, as I am dealing with a communal machine running XP, and which I have almost forgotten how to use properly.  After updating my winXP virus checker and several other programs, I rebooted windows as is always needed.  It did not boot but dropped back to the POST as if the reset button was pressed.WinXP  did this 3 or 4 times so I gave up on that.

I then tried to boot to my main ubuntu again, and this time it got as far as the splash screen then said "No valid partition table found on sda" or similar words.

"PANIC"- that was my first thought, even though I have good backups.  Other family activities then called me away, so I shut down completely.  An hour or so later I tried booting again and everything was exactly as it should be; no problems at all to be seen.

I thought it may be a coming hard disk failure so used the Maxtor/Seagate disk diagnostic tools on Ultimate Boot CD.  That found no problems either on the quick test, nor on the full scan of this 160GB disk. Today no problems have been seen either and it booted as it should.

Has anyone seen this sort of behaviour before, firstly, not getting beyond "Starting up" at boot, and secondly, "No partition table found", only for it to appear again after a full shutdown?

---

### Post by louieb on 2010-01-23
Hello ajgreeny, Don't know what its called in England, but I call it a **computer burp**. Looks like you've made all the usual checks. 

I've seen enough of your helpful posts to know - if your posting a problem - it would not be an easy one.  Its really hard to track down an intermittent problem.

---


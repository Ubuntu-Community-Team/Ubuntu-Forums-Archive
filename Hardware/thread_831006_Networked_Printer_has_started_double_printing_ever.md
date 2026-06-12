---
title: "Networked Printer has started double printing everything"
date: 2008-06-16
forum: Hardware
---

### Post by sethd32 on 2008-06-16
BACKGROUND: I have a mixed OS network with 20 XP computers, and 2 with Ubuntu 8.04.  We share a networked Kyocera KM5050 copier/printer.  Until recently the printer worked perfect for all.

PROBLEM: About two weeks ago, the printer started double printing everything sent from both Ubuntu machines.  If I send one copy to print, it prints two copies.  If I ask it to print 2 copies it prints 4...

We have tried tweaking settings, removing and re-adding the printer and have had no success.  It's frustrating since it did work fine, and we did not make any changes.  The only thing that would have changed is perhaps an update that came through in 8.04 (it did work fine when we both initially upgraded to 8.04)

I haven't been able to find any posts with the same issue.  Anybody ever seen this?  Does anybody have any ideas on how to fix this?  I try to reuse the wasted paper as scrap, but I am killing forests here :(

---

### Post by pelmenept on 2008-06-20
Well me gues, is with update, Ubuntu machines got a printer update.

May be I am wrong, but as I know Ubuntu can use 2 different driver configurations or interfaces (whatever they are called) CUPS and some other one. I think CUPS is better, and probably you were using a non-CUPS version, but with an update a CUPS driver came in, and was automatically installed. So right now I guess, you have same printer installed through 2 different interfaces, so whenever you print, even though it sends command to only 1 printer, it sends it through 2 diff interfaces, thus making it print twice....

Maybe I am totally wrong....

---

### Post by sethd32 on 2008-06-30
That sounded logical to me at first, but the issue only occurs on the networked Kyocera km5050.  When I print to my local Lexmark x1150, I don't get doubles.  Also, removing and re-installing should have fixed that issue if it were the problem I would think. Anybody have any other suggestions???

---


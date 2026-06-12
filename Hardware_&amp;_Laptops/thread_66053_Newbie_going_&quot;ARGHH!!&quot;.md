---
title: "Newbie going &quot;ARGHH!!&quot;"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by Ron Fouler on 2005-09-15
First day with Ubuntu Linux, and not suprisingly  I'm having problems :). Some were easy to solve (like the shared folders on the Linux box not showing on the w*nd*ws boxes until they were rebooted), but some are being a real pain in the buttocks! I Can't get my monitor to do the 1280x1024@75Hz that I had on XP. It does do 1280x1024 (after a lot of faffing and some help from a friend), but it moves the screen like a virtual desktop, and that's no good. I may be missing something and I may have missed a reference in previous posts, but can someone please help! I'm Using Hoary Hedgehog with an XP2100+ on a Syntax SV266A mobo with 512Meg RAM and a 64 meg GF4 MX440 AGP8x into an Eizo Flexscan F56. (it's a bloody good thing I'm bald already, cos I'd be pulling my hair out otherwise......)
Thanks in advance....

---

### Post by heimo on 2005-09-15
Hi!

I've collected some information here:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

You should check that you don't have anything with word "virtual" in xorg.conf display section, then you can try reconfiguring xserver.xorg. If that still doesn't work, could you post your xorg.conf and search the log file (mentioned in post above) for any relevant information? Thanks!

---

### Post by Ron Fouler on 2005-09-15
Aha....  sussed it! Went to xorg.conf and added Option "IgnoreEDID" and all is funky and fruity now :D \\:D/  \\:D/ 
Cheers for the help.

---


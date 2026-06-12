---
title: "dual boot problem"
date: 2005-09-06
forum: Hardware &amp; Laptops
---

### Post by triune on 2005-09-06
Hi all
 
 New to linux but falling in love. Have tried Ubuntu on my VPR matrix and it works great. Sound and internet right from the bat. Have MEPIS on my main work laptop which is good but no sound, but when I tried to set up Ubuntu instead of MEPIS, problems with the dual boot. During install tries to connect and asks me for DCHP and says can't find it. Went ahead with install but when tried to set up network but my built in wireless was not available as an option. Everything worked great when I installed as only OS (my VPR). Unfortunately I need XP programs for work related matters so have to set up dual boot system. Is something from XP blocking Ubuntu from recognizing the hardware?
 
 Thanks for any assistance
 
 Bill
Add to triune's Reputation     Edit/Delete Message

---

### Post by numberexhaust on 2005-09-06
If I understand the problem correctly, you think that your dualboot is interferring with the wireless hardware?  Did you have wireless on your VPR?  Chances are, on your work laptop, your bult-in wireless hardware is not supported natively in linux.  Linux, unfortunately, is far behind in wireless technology.  The best way to solve this problem in Ubuntu currently, is to use a program called ndiswrapper, which imports windows wireless drivers over to linux.  I use it with a pcmcia netgear wg511t card and everything works great.  If you need guidance on how to set this up, please post back... I will suscribe to this thread and give you answers as you need them (welcome to linux!). 

By the way, if there is no "wlan0" or something similar in the output of "ifconfig", then chances are you don't have the driver installed and need to use ndiswrapper.

---

### Post by triune on 2005-09-08
Thank you for the suggestions.  This sounds like a weekend project when I have a few hours to try things out, but I will give it a shot.  Your right, my VPR is connected via a pcmcia card, but my work laptop has wireless built in.  Thanks for the welcome, linux is simply fantastic.

Bill

---

### Post by triune on 2005-09-10
number

thanks for your suggestions.  Problem solved though I do not know exactly how it happened.  I set up the computer with Partition Magic, and booted the Ubuntu install disk.  I turned off WLAN and tried to use my PCMCIA card (as it worked on the VPR) and during install I was informed my eth1 (wireless) was not active.  I continued anyway, and with the PCMCIA card, I had the same issue (no DCHP). I went back, turned on the WLAN, and it read it this time.  Everything works well.

Thanks again.

---


---
title: "Problems with Thinkpad harddisk Load_Count_Cycles"
date: 2010-01-23
forum: Hardware
---

### Post by mvamsip on 2010-01-23
hi there..

I am a new bee in this Linux community. I have installed Ubuntu 9.10 on my Thinkpad R61i a couple of days back. While I was using the laptop I found out that my hard disk is making a high noise, while I hardly ever hear the noise when I am working on windows. A quick search took me to this forum where the file "/etc/hdparm.conf" was edited.
I use "date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'" to keep an eye on the load cycle count. I have noticed that this fix does not work with my hard disk. My hard disk is a ATA Hitachi HTS542516K9SA00, 160GB one.
I have been working on this problem for over 6hours now and as a last resort posting this message.

Thanks in advance for any help in this regard.

[RIGHT]-Makky.
[/RIGHT]

---

### Post by mikewhatever on 2010-01-23
Please, don't be vague. What fix are you talking about? What changes did you make to hdparm.conf?

---


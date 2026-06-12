---
title: "ubuntu 10.04 gets stucked after running /scripts/init-bottom"
date: 2010-05-06
forum: Hardware
---

### Post by lokeshverma on 2010-05-06
Hi all

I am an ubuntu newbee.

I have installed 10.04 from live cd. But the boot process is slow as compared to other machines.

I am attaching my bootchart.
I guess that around the phase from 3sec to 14 sec is causing the delay.

I booted after removing "quite splash" to see whats happening.
After "Running /scripts/init-bottom" nothing happens for around 12-13 seconds, just a blinking cursor.

Please help me with this one, as I have no idea about ubuntu. ( I was a windows user till few days back )

[IMG]http://i40.tinypic.com/14y1oah.png[/IMG]

---

### Post by papopapo76 on 2010-05-06
I have the same problem as you! I'm using Ubuntu Netbook Remix 10, that is the same as say: Ubuntu 10.04.  Im using a Toshiba NB205 (Model N330BL) and the Ubuntu is fast when it is running, but the boot up is very very slow. I also check that stuck in the /scripts/init-bottom more than 2 minutes.

We need a fix for that, please help us! we need any GURU-man in Ubuntu.

P.S. I discover a trick for bypass this boot delay: Press and hold the "Control" key when the blinking cursor appear for accelerate the unknown delay. But this is just a tweak, maybe work for others people with the same problem.

---

### Post by papopapo76 on 2010-05-07
In my case, I change the SATA setting in the BIOS from ACHI to "Compatibility Mode" and it fixed the problem. Now the Ubuntu start very fast. I hope this help.

---

### Post by strathausen on 2010-09-25
Looks like something's wrong with ureadahead - despite it should actually speed up boot.

---

### Post by kkinder on 2010-11-01
This is now happening for me on 10.10 after installing kubuntu-desktop. My BIOS serial ata setting has no effect, nor does holding ctrl. Never unhangs. 

no errors, no debug info, nothing. just a broken system.

---

### Post by theWrkncacnter on 2010-12-05
This happens to me too -- everything goes pretty fast until init-bottom, and then i get a blinking cursor for 10 seconds or so. I've never tried the control trick yet though -- i'll try.

---


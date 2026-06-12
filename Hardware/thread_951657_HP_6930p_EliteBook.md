---
title: "HP 6930p EliteBook"
date: 2008-10-18
forum: Hardware
---

### Post by vtslimik on 2008-10-18
Hi!

I got a new laptop HP 6930p (2x 2.4Ghz, 4gb RAM, 45000MHD integrated graphics from Intel). I wonder if anyone installed Ubuntu and got i to work out of the box?  After reading in the forum i realize that some have problem with the Intel 4500MHD, and problems with WiFi card, also from Intel, 5300 AGN.

Does anyone know if the new 8.10 release of Ubuntu will have fixed these problems?

Another question is; if Intel 4500MHD will be supported, is it going to be enough to run compiz on it?

---

### Post by vtslimik on 2008-10-20
No input in this matter?

---

### Post by mindfall903 on 2008-10-24
Last time I tested this laptop with Ubuntu 8.10 Beta (Octo 22./23.), wireless network was working right from the CD.

The new release client (Oct. 24.) should be even more promising.

---

### Post by vtslimik on 2008-10-24
did you try out the graphics? compiz?

---

### Post by wanchai on 2008-10-26
I have the FL490AW (Intel graphics) and installed 8.10 beta. Graphics including Compiz worked out of the box. Even the dual-monitor functions seem to be ok although they may not get along with Compiz.

There was a problem with the wired network. It had a scary bug in the alphas, it simply didn't work in the beta, but it was fixed later on. When I installed the Oct 13 daily, it was ok. It may have been fixed earlier, but Oct 13 happened to be the day I was looking into it.

---

### Post by vtslimik on 2008-10-31
Im running the Live Cd now and everything works except the sound (ICH9) Works only with headphones. 

Anyone knows how to fix?

Seems otherones have the same problems: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284319](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284319)

---

### Post by wanchai on 2008-11-02
I have created a laptop test page for this model:
[https://wiki.ubuntu.com/LaptopTestingTeam/HPCompaq6930p/Intel](https://wiki.ubuntu.com/LaptopTestingTeam/HPCompaq6930p/Intel)
I specified "Intel" in the URL because this laptop comes with two different video cards: Intel and ATI.

Please have a look and edit it if necessary. I would appreciate it if someone could repeat the test of the MMC/SD slot as well as the microphone business.

---

### Post by wanchai on 2008-11-04
Just for the record: Matt Ginzton pointed out that the sound problem can be fixed easily. The following solution works for our model as well:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027)
:p Thanks, Matt.

---


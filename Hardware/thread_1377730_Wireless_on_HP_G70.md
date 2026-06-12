---
title: "Wireless on HP G70"
date: 2010-01-10
forum: Hardware
---

### Post by davethegent on 2010-01-10
I have an HP G70 and would like to get into the world of linux, starting with Ubuntu.

I need to know if my wireless card will work with the latest release, 9.10, because if not I cannot use the distro.

If anyone can help me make it worl I will be very grateful!

---

### Post by Greenwidth on 2010-01-10
Do you know what the make/model/chipset is?

Probably the easiest way to test is to burn a Ubuntu CD and boot to it to test & try it out without making any changes to your PC.

---

### Post by avilella on 2010-01-11
Can you run this command on a terminal to know the specific model?

lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/'

> **davethegent said:**
> I have an HP G70 and would like to get into the world of linux, starting with Ubuntu.

I need to know if my wireless card will work with the latest release, 9.10, because if not I cannot use the distro.

If anyone can help me make it worl I will be very grateful!

---

### Post by nathanhillinbl on 2010-01-11
Pretty sure he/she's on Windows right now, as they're saying that they won't install unless it works.

Wireless support has come sooo far in the past years, and your card is most likely supported. As Greenwidth said, the easiest way to figure out would be to burn a CD.

---

### Post by davethegent on 2010-01-11
Looking in the windows hardware list its an Atheros AR5007 on an Intel motherboard and Intel Core Duo t5800 processor. 

I will try a live disc, that thought had never crossed my mind!

---

### Post by davethegent on 2010-01-11
Yeah it works, just selected my router, typed the key and I was online!

Thanks for your advice guys

---

### Post by nathanhillinbl on 2010-01-11
Great! Glad we could help! Welcome to Linux! 

I have tried many distributions over the past 7 or so years that I've been running Linux, and have to say that Ubuntu is one of the best for ease of use, and for something that "just works". The community here at Ubuntuforums.org is HUGE, and most likely if you have an issue, someone here will help or direct you in the right place.

---


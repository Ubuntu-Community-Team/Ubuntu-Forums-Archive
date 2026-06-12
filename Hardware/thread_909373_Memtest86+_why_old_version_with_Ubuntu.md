---
title: "Memtest86+ why old version with Ubuntu?"
date: 2008-09-03
forum: Hardware
---

### Post by mundo on 2008-09-03
Hi,

Just wondered if someone could answer this question for me.  Why does Ubuntu come with an outdated Memtest86+?

Hardy comes with version 1.7 but if you go on to the memtest.com websites then they have version 3.4a

Another question is, does it make much of a difference?

---

### Post by mundo on 2008-09-03
Ah, I have found this:

[https://bugs.launchpad.net/ubuntu/hardy/+source/memtest86+/+bug/238990](https://bugs.launchpad.net/ubuntu/hardy/+source/memtest86+/+bug/238990)

It appears that an updated version (2.01) will be in Intrepid Ibex.

---

### Post by molochi on 2008-09-06
It makes a difference. The older versions of memtest86 will fail to identify chipsets and give false fails with some newer (less than 2 year old) hardware configurations. Even the 2.01 version does this. IMO memtest86 is only usefull for ruling out memory problems or identifying specific failures in a range of memory addresses. ie if you get no errors, you're ok to troubleshoot something else and if you get a small range of failures somewhere in the middle of your memory you might try troubleshooting the memory, but if you get massive numbers of errors (and you aren't having equally massive problems with the system) maybe its the memory, maybe not.

---

### Post by mundo on 2008-09-10
I'm not getting any errors with any of the versions but definitely have a hardware issue so will continue the diagnostics!

---

### Post by skinnie on 2008-12-26
is there a way to update the internal memtest86+ in hardy?

---

### Post by Sef on 2008-12-26
>  		is there a way to update the internal memtest86+ in hardy? 	

Click [here]("http://memtest86.com/").  That link will take you to the Memtest86 download page.

---


---
title: "Raid"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by Peter6218 on 2007-09-24
I'm looking for information.

I have what will become a quad boot system

Two main HD's runing a version of Xandros and a WinXP disk.

I have a RAID card supporting two more HD's running Win98 on one and another version of Xandors on the other.

If I replace the main version of Xandros (disk 1) with Feisty will Grub be able to link the two disks on the RAID card as well??

RAID card is a Ultra ATA 100/133

---

### Post by psusi on 2007-09-24
You should read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

### Post by Peter6218 on 2007-09-25
> **psusi said:**
> You should read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

Sorry, guess your reading skills are?

This is Hardware RAID. A specific card is involved.

---

### Post by psusi on 2007-09-25
I guess you did not read the link.  Please do so.  Unless you paid $400 for the card, it is not hardware raid, but fake raid.

---

### Post by Peter6218 on 2007-09-25
> **psusi said:**
> I guess you did not read the link.  Please do so.  Unless you paid $400 for the card, it is not hardware raid, but fake raid.

I did read the link and it makes NO sense.

---

### Post by psusi on 2007-09-25
What part don't you understand?

---

### Post by Peter6218 on 2007-09-25
> **psusi said:**
> What part don't you understand?

The entire geek speak!!

Why can't they write this stuff in intelligible English??

Anyway did a test. Ubuntu can't see through the RAID card.

OK I'll find some other way.

---

### Post by psusi on 2007-09-26
It doesn't even see them as individual drives?

---

### Post by overdrank on 2007-09-26
> **Peter6218 said:**
> The entire geek speak!!

Why can't they write this stuff in intelligible English??

Anyway did a test. Ubuntu can't see through the RAID card.

OK I'll find some other way.

Hi you may look at this links 
[http://www.linuxcommand.org/man_pages/mdadm8.html](http://www.linuxcommand.org/man_pages/mdadm8.html)
Good luck!

---

### Post by Peter6218 on 2007-09-26
> **psusi said:**
> It doesn't even see them as individual drives?

Nope, not there as far as Feisty is concerned.

---

### Post by Peter6218 on 2007-09-26
> **overdrank said:**
> Hi you may look at this links 
[http://www.linuxcommand.org/man_pages/mdadm8.html](http://www.linuxcommand.org/man_pages/mdadm8.html)
Good luck!

Well that at least reads and makes sense.

Can't get the download though. Know of another site for mdadm?

---

### Post by psusi on 2007-09-26
> **overdrank said:**
> Hi you may look at this links 
[http://www.linuxcommand.org/man_pages/mdadm8.html](http://www.linuxcommand.org/man_pages/mdadm8.html)
Good luck!

That's for software raid.  

> **Peter6218 said:**
> Nope, not there as far as Feisty is concerned.

Oh boy, that's a problem.  Sounds like the kernel doesn't have a driver to talk to that card at all.  What kind is it?  A Promise something?  It should see it... if not, you may be sol.

---

### Post by Peter6218 on 2007-09-26
> **psusi said:**
> That's for software raid.  



Oh boy, that's a problem.  Sounds like the kernel doesn't have a driver to talk to that card at all.  What kind is it?  A Promise something?  It should see it... if not, you may be sol.

IT8212 ATA RAID Controller   

OK that's all I could find on the install CD that makes any sense.

Software for a whole range of Windoze but not a  squeak about Linux.

---

### Post by overdrank on 2007-09-26
> **Peter6218 said:**
> IT8212 ATA RAID Controller   

OK that's all I could find on the install CD that makes any sense.

Software for a whole range of Windoze but not a  squeak about Linux.

Hi I found this but it is for breezy 
[http://ubuntuforums.org/showthread.php?t=106285&highlight=patch+kernel+2.6.12](http://ubuntuforums.org/showthread.php?t=106285&highlight=patch+kernel+2.6.12)
&
[http://ubuntuforums.org/showthread.php?t=10400](http://ubuntuforums.org/showthread.php?t=10400)
And if you want to keep looking
[http://search.yahoo.com/search?p=IT8212+ATA+RAID+Controller+on+ubuntu&fr=yfp-t-501&toggle=1&cop=mss&ei=UTF-8](http://search.yahoo.com/search?p=IT8212+ATA+RAID+Controller+on+ubuntu&fr=yfp-t-501&toggle=1&cop=mss&ei=UTF-8)
Hope this helps good luck! 

:guitar:

---

### Post by sr20ve on 2007-09-26
> **Peter6218 said:**
> Sorry, guess your reading skills are?

This is Hardware RAID. A specific card is involved.

Just because you have a raid controller, does not mean it is a true hardware raid.

A lot of the low end raid controllers are driver based, which makes them a bit of a hybrid of hardware and software raid.

---

### Post by psusi on 2007-09-26
According to that thread it should just work in in newer releases.

---


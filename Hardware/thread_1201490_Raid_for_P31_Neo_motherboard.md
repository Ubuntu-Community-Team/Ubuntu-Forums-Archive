---
title: "Raid for P31 Neo motherboard"
date: 2009-07-01
forum: Hardware
---

### Post by styleruk on 2009-07-01
Hi

I'm about to upgrade from Ubuntu 8.10 64bit to the latest 64bit version and have got hold of two 74gb raptor drives, that means I have 3 raptor drives teh same.  So I thought I would use them in a raid array.
I have a MSI P32 V1 motherboard and on the MSI site, they have a windows utility to run a raid, however, I wondered what I could use for Ubuntu.  I thought a raid driver ran before OS so it looks like a single drive.
Has anyone had any experience with setting this up?  Maybe some tips?
My ultimate plan would be to set them all up as a raid and install ubuntu on them.

Regards
Simon

---

### Post by styleruk on 2009-07-01
Sorry all....ignore that last post, turns out that the motherboard does not support raid.

---

### Post by ronparent on 2009-07-02
Don't let the term fakeraid throw you. This site tells all step by step.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

You should also read up on dmraid which is the ubuntu raid utility.

---

### Post by styleruk on 2009-07-02
That's an interesting article, I have a couple of days on ebay for a new motherboard that supports raid, I really would like to get all three raptors working in a raid.

Board I'm getting is:
ASUS P5W DH Deluxe Motherboard - 775

Link here for info:
[http://support.asus.com/faq/faq.aspx?SLanguage=en-us&model=P5W%20DH%20Deluxe&product=6&os=5](http://support.asus.com/faq/faq.aspx?SLanguage=en-us&model=P5W%20DH%20Deluxe&product=6&os=5)

What do you think? is this a 'fake raid', or do you think it will be ok?

Thanks in advance.

Si

---

### Post by ronparent on 2009-07-02
It is what the linux community refers to as fakeraid and it should do fine. Unless you need to dual boot with windows you might want to consider using a software raid setup (mdadm). I know of no current MB implementation that is a true hardware raid. The main advantage of a hardware raid is that it is usually mounted on a separate plug in raid card. They are reputed to be pricey however.

---


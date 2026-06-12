---
title: "general raid questions"
date: 2010-07-19
forum: Hardware
---

### Post by wlraider70 on 2010-07-19
I've been using my Ubuntu server to back up files from my laptops.

I was wondering about a raid setup. I don't know too much about it, but heres what i was thinking. 

a pci raid controller something like this

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3981741&CatId=1454](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3981741&CatId=1454) 

that will mirror 2 1TB drives. 

my questions are

Is there any software component I need?
Will ubuntu play nice with it?
My box is original and IDE connection, will it handle sata connections? 

thanks

---

### Post by wlraider70 on 2010-07-20
would anyone tell what raid card they use?

---

### Post by arsenic23 on 2010-07-20
Point of advise:  With linux those fake raid cards aren't really going to give you any benefit to just using the raid features built into the kernel.  Unless you need the additional disk connections you'd be better off just using straight software raid.


--------------
ADDITION::
--------------
More information here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by wlraider70 on 2010-07-21
I had heard that soft raid is bad.
so how can i tell a real raid controller from a fake one?

i actually do need more connections, can i use the extra port card and softraid?

---

### Post by arsenic23 on 2010-07-21
> **wlraider70 said:**
> I had heard that soft raid is bad.
so how can i tell a real raid controller from a fake one?

i actually do need more connections, can i use the extra port card and softraid?

Yes you can.  I buy those cheap Rosewill SATA controllers all the time, and have once or twice used them with regular software raid with good results.  Also they are cheap.

Actual hardware raid cards are in the $300 dollar range.

---


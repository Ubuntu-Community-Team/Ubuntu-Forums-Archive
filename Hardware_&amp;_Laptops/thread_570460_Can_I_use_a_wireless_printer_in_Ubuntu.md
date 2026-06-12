---
title: "Can I use a wireless printer in Ubuntu?"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by speedsix on 2007-10-08
I was thinking of buying something like this;

[http://www.ebuyer.com/product/128796](http://www.ebuyer.com/product/128796)

I've never configured a wireless printer before, I'm assuming I'd give the printer an i.p address and get it connected to the network and then in Ubuntu set the printer up to use IPP and provide the printers i.p?



Dom

---

### Post by bowmanr@mailcity.com on 2007-10-08
Hmmm ... I've got the Z1480 which works flawlessy with { XP | Vista } *hangs head in shame*

However, I've not got a clue about getting it working in linux. Strange thing is that it reports itself as a FTP server on the network -- with no access permissions. Curious.

Any thoughts on usage would be gratefully received.

---

### Post by bowmanr@mailcity.com on 2007-10-08
I had not heard of IPP and looked into it to see if the Lexmark printers Z1420 and Z1480 support IPP.

I could not find much. However, according to this IBM website, the Z1420 does not support IPP. Not looking promising.

---

### Post by speedsix on 2007-10-10
Anyone any more input?


Thanks

---

### Post by Spam Banjo on 2007-10-23
Bump. Same Question here...

---

### Post by Strangerdave on 2007-10-24
yeah I would like to know if it is possible because I have a HP Photosmart, i know the ip addy and the hostname of the printer, but I have no clue where to input the info.

-SD-

---

### Post by wieman01 on 2007-10-25
> **Strangerdave said:**
> yeah I would like to know if it is possible because I have a HP Photosmart, i know the ip addy and the hostname of the printer, but I have no clue where to input the info.

-SD-
What's the difference between a network printer and a wireless printer? I would think there isn't any. You simply need the right CUPS driver, that's all.

If OSX is supported, there is a pretty good chance that it will work with Linux soon as well. 

[http://apple.slashdot.org/article.pl?sid=07/07/12/1342258&from=rss]("http://apple.slashdot.org/article.pl?sid=07/07/12/1342258&from=rss")

---

### Post by PointyWombat on 2007-10-25
I have a wireless HP 5850 and it works without problem. If you can get it working through the ethernet interface, then it'll work via wireless because the driver is the same. It's just a config on your printer and router that makes it wireless. Ubunto doesn't know or care if it's wireless.

---

### Post by Strangerdave on 2007-10-25
So sorry, how would I configure it by the ehternet interface.  I am a bit of a n00b, but will try that avenue to see what I come up with.

-SD-

---

### Post by PointyWombat on 2007-10-25
I would suggest following the manufacturers procedure for the initial configuration of the printer.  Once the printer is available (pingable from your box) via ethernet or wireless, then you can add it  via System->Admin->Printing. It's considered a network printer at that point so just step through that.

---

### Post by mattm591 on 2008-05-17
I have the Lexmark Z1480 and can't get it working in Ubuntu.

I've tried adding it as a network printer but no luck.

Anyone had any luck installing this?

---

### Post by Spam Banjo on 2008-05-19
Still no joy in 7.10 or 8.04. This is annoying. Lexus should be supporting linux, it's pathetic for a company of their size to ignore an OS for professionals.

Looks like windows is still a necessity then.

:( :( :( :( :( :( :( :(

---


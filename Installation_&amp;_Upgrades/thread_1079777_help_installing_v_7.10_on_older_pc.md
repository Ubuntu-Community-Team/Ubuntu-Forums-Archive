---
title: "help installing v 7.10 on older pc"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by sdweimer on 2009-02-24
hello tyring to install ubuntu on older pc that has a fat 32 file directory on it want to remove all directories and only install ubuntu but the partiton editor will not recognize the hard drive that is installed it has a maxtor 20 gb hd please help thnxs

---

### Post by taurus on 2009-02-24
What's the output of this command from a terminal while in Ubuntu LiveCD?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
Instead of installing an old release which will expired in a few months, why not install intrepid Xubuntu or at least hardy?  How much RAM does it have anyway?

[http://www.xubuntu.org](http://www.xubuntu.org)

---

### Post by avtolle on 2009-02-24
It's been a while since I installed 7.10, but IIRC, there was an issue with the hard drive being mounted when trying to install from the CD, especially when you were installing from the live session, that is, by clicking on the "Install" folder on the desktop. When in the partitioner, see if the drive is mounted; there was, as I recall, also an icon that appeared on the desktop. If the icon is present, right click on it and select "unmount volume" from the list that appears; get back to the partitioner quickly and see if the drive is then recognized as being unmounted, and start the process. Again, from memory, the HDD would be again mounted rather quickly, so don't tarry in returning to the partitioner once the HDD is unmounted (if indeed this is the problem you have).

As support for 7.10 ends in April, is there some reason you are not going for 8.04 LTS (supported through April, 2011 on desktop machines; April, 2013 for servers) or 8.10 (supported through April, 2010)?

---

### Post by sdweimer on 2009-02-24
512 meg on a compaq deskpro running with p3 1000mhz processor, had this ubuntu disk for a while just downloaded 8.10 but havent burned it to disk yet.

---

### Post by sdweimer on 2009-02-24
the answer to the output question is none it just goes back to command promt

---

### Post by sdweimer on 2009-02-24
actually the hd does not sho up in gparted and during install.

---

### Post by sdweimer on 2009-02-24
if i upgrade to 8.10 will i still have this problem or will it be easier to install this one?

---

### Post by sdweimer on 2009-03-02
I really don't mean to seem angry but what are the point of forums if nobody succesfully answers your question? I mean five days ago i asked a question and it has yet to be answered.

---


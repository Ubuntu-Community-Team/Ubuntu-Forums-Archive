---
title: "Towards a quiet desktop"
date: 2010-09-22
forum: Hardware
---

### Post by dargaud on 2010-09-22
Hello all,
I'd like to hear your opinions about making my main desktop (and always-on server) quieter. Nothing too fancy:

First I was thinking of getting a flash SATA drive for the system and data-server disk. Their prices and quality now seem affordable and about 64Gb for 100$ should be enough for anybody. In the past it was ill-advised to run write-intensive stuff like swap on flash, but I think it is now solved, right ?

Then I would put my /home and all data on a large normal disk. In Windows it was easy to ask the disk to go to sleep after some time unused, but it seems a bit harder on Linux, using tools meant for laptops. I've done some tests yesterday with *hdparm* and the disk would wake after only a few seconds. Some googling reveals that '*ext3 is not meant to be put to sleep*'. Opinion ? Should I use another filesystem or can anybody recommend a set of magical incantations that does the job ?

Thanks

---


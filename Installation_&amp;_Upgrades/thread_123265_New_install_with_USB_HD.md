---
title: "New install with USB HD"
date: 2006-01-29
forum: Installation &amp; Upgrades
---

### Post by jtjames on 2006-01-29
Sorry if this has been solved before. This is my first time installing Linux but I have done some reading. What I am trying to do is install Ubuntu on an older HP machine (700mhz Celeron, 192megs ram, 20gig internal HD + 100gig external HD). What I want to do is put the OS on the 20gig HD and the programs and media on the external 100gig USB drive. Anyone have any pointers to how I would do this? Do I just need to put /home on the USB drive? If so how? Thank you.

---

### Post by slashem on 2006-01-29
The whole OS will fit nicely with much room to spare on the 20gig HD. You can put /home on the USB HD, although I would advice only putting your mediafiles on it, since a USB disk can be a bit slow, just my humble opinion.

But if you want to put /home on there, then here is just an overview of what you need to do, I'll be back tomorrow and see if you have any questions (I'm off for some sleep)  :

1. Install OS
2. Plugin USB HD and format.
3. Change /etc/fstab so that /home points to the USB HD
4. Copy /home/jtjames over to the USB HD

---


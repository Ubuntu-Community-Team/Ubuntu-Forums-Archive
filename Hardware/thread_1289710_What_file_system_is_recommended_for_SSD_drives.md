---
title: "What file system is recommended for SSD drives?"
date: 2009-10-12
forum: Hardware
---

### Post by Hund on 2009-10-12
What would you recomend?

---

### Post by dabl on 2009-10-12
The answer depends, somewhat, on your preference for simplicity versus data security.

The simplest thing to do is format it ext2.

The safest thing to do, IMO, would be to format it ext4, and then use your noatime, data=writeback, and commit=120 mount options to slow down the journal-writing to something reasonable, bearing in mind that you will need to be cognizant when you shut down, and not just nail the power button. You can research the ext4 mount options -- Google will teach you all about them.  :)

---

### Post by Garyu on 2009-10-14
[http://www.storagesearch.com/ssdmyths-endurance.html](http://www.storagesearch.com/ssdmyths-endurance.html)

The above link is to an article talking about SSD wear.

[http://www.corsair.com/products/ssd_extreme/default.aspx](http://www.corsair.com/products/ssd_extreme/default.aspx)

My girlfriend just bought the above Corsair Extreme SSD. They state it has a 100+ year life expectancy. If you read the first article I linked you will see that the life expectancy is not calculated the same way at Corsair, since they assume you will have some downtime. But are you really writing data to your disk all day long? Most people aren't, so I think the Corsair guys have a better estimate, even though they are trying to sell their product.

In my opinion, file system should not matter much. Sure, there are those options that may prolong the life of your SSD. But in a few years, new technology will be here that will make you want to replace your SSD anyway. So why bother with it?


EDIT: [http://www.linuxfoundation.org/news-media/blogs/browse/2009/03/ssd%E2%80%99s-journaling-and-noatimerelatime](http://www.linuxfoundation.org/news-media/blogs/browse/2009/03/ssd%E2%80%99s-journaling-and-noatimerelatime)
I also found this article, which I think makes a lot of sense.

---

### Post by Hund on 2009-10-14
I was just curius if there was any file system that was optimized for SSD drives. :)

I usually replace my system HDD after 2 years. There is a 3 year waranty on the Intel SSD I'm going to buy so I'm not worried about that.

**OT:** Kul med norrlänningar här. ;)

---

### Post by Garyu on 2009-10-14
> **Hund said:**
> I was just curius if there was any file system that was optimized for SSD drives. :)

[http://thunk.org/tytso/blog/2009/02/22/should-filesystems-be-optimized-for-ssds/](http://thunk.org/tytso/blog/2009/02/22/should-filesystems-be-optimized-for-ssds/)

[http://kerneltrap.org/node/8159](http://kerneltrap.org/node/8159)
LogFS & JFFS2

Alternatively, if you want journaling and fast fs:
[http://www.linux-mag.com/cache/7345/1.html](http://www.linux-mag.com/cache/7345/1.html)
NILFS

OT: jo, tack. :)

---

### Post by iTrickU on 2009-10-14
YAFFS2 was the one that came to mind first.

[http://en.wikipedia.org/wiki/YAFFS](http://en.wikipedia.org/wiki/YAFFS)

---


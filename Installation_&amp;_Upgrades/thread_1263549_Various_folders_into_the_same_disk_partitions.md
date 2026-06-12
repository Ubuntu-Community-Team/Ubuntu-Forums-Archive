---
title: "Various folders into the same disk partitions"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by *g!t5^_)*(H on 2009-09-11
Hi,

I'm using an Acer Aspire One computer, due its slow disk performance I've installed some folders into a fast SD Card capable of 30M/second read-write). Computer performance is very good now.

This is my partition table:

[place, space]

At SSD:

/ (3997)
/media/extra_space  (4071)

At SD Card:

<swap> (912)
/usr (4252)
/var (1998 )
/home (1003)

I don't like 4 partitions at the SD Card, and I would prefer only 2 partitions (for swap and the other folders). So:

Is there a way to install (specify) various folders (/usr, /var, /home) to use the same disk partition?

---


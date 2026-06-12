---
title: "SSD, LUKS, and Enabling TRIM"
date: 2013-12-31
forum: Hardware
---

### Post by linux4me on 2013-12-31
I am going to try an install on an SSD drive using LUKS and I definitely want to enable TRIM.

Accoring to [this post]("http://askubuntu.com/questions/18903/how-to-enable-trim/19480#19480"), the ideal method of enabling TRIM in Ubuntu, and the one slated to be included by default in 14.04, is to set up a daily cron job to run fstrim. That post, and other articles I've read, say that using the discard parameter in fstab can actually *reduce* performance of an SSD with delete operations. I also read that this fstrim cron job approach doesn't work with LUKS.

So, I did some more searching, and found [this article]("http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html"), which describes using the discard parameter to enable TRIM with LUKS.

My question is this: Is there any way to use the reommended fstrim cron job with LUKS instead of the discard method?

---


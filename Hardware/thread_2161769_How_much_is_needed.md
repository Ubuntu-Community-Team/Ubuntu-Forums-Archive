---
title: "How much is needed?"
date: 2013-07-11
forum: Hardware
---

### Post by Ubunetbook on 2013-07-11
Hi, thanks for any help.
I've been using stock LinuxMint, but my netbook harddrive died and I tried booting to USB using Ubuntu and really like it. So I'm replacing my hard drive with an SSD and switching.
Quick question:
So I just read this:
[http://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds](http://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds)

If I just use my netbook for surfing/papers for college/mail...and I don't really know about customizing Linux...do I need to do anything on that list? 

(Your answer might be that I don't NEED to, but is any of that REALLY, REALLY recommended?)
Thanks again.

---

### Post by BreezyBrooke on 2013-07-11
With the SSD, the only problem I see is with swap. Most SSD's still don't have good support for Linux SWAP partitions yet because SWAP can't use the Trim flag. So swap on a SSD will seriously wear it down fast. This can be remedied though by upgrading your Netbook's ram to 2GB, or if possible 4GB of ram and setting swappiness to something like 5. That way swap is called on as infrequently as possible.

---

### Post by Ubunetbook on 2013-07-11
> **BreezyBrooke said:**
> With the SSD, the only problem I see is with swap. Most SSD's still don't have good support for Linux SWAP partitions yet because SWAP can't use the Trim flag. So swap on a SSD will seriously wear it down fast. This can be remedied though by upgrading your Netbook's ram to 2GB, or if possible 4GB of ram and setting swappiness to something like 5. That way swap is called on as infrequently as possible.

I appreciate the response! So mine has 2gb now. So maybe I'll upgrade to 4-8 later. Mine can go up to 16gb, but I don't think 8-16 will ever be needed.

(30 minutes later) Now, after looking into what swap is, I really will fix that one! Perhaps the file system layer too. I never look at what time I access a file! Or review crash logs. Thanks for the heads up.

---


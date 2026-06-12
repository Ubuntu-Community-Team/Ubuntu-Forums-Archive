---
title: "HD Failure: fsck and Palimpsest indicates nothing"
date: 2010-04-25
forum: Hardware
---

### Post by ericmo on 2010-04-25
I have a ATA Maxtor STM3160215AS hard-drive. It's a relatively new HD, with less than 4yrs of use. I have three partitions in it, two ext4 (/ and /home) and one swap.

Lately, my HD has started failing, making weird noises. Today, the computer wouldn't even recognize  the HD while booting, for some time. For some reason, it started to work again, and then I could do a

```
sudo touch /forcefsck
```and reboot. But fsck didn't find anything, didn't warn me about anything. So, I loaded Ubuntu and when I opened Firefox, my HD failed again.

I opened my tower to phisically check out if there was anything wrong, as bad connections, and didn't find anything. But apparently, lying down my tower made the HD work again - which gives some reasonable certainty that there is something wrong with my HD.

Well, then, I took my Ubuntu Karmic Koala LiveCD (I use Ubuntu Studio, but I needed the LiveCD, that Ubuntu Studio doesn't provide) and opened Palimpsest, to run the selftest. Selftest also indicates nothing wrong.

So, I'm not sure what to do next.
I don't have any relevant data on my HD, because I recently reinstalled Ubuntu Studio (less than 2 weeks ago), so I'm not worried about that. But I need my PC to work!

Is there any deeper test I can run on my HD?
Would you recommend me to just buy a new HD, save my patience instead of my money? And if so, is there any thing I should have in mind when buying an HD for using with Ubuntu?

Cheers.

---


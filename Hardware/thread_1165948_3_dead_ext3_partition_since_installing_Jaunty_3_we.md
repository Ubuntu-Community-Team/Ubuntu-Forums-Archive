---
title: "3 dead ext3 partition since installing Jaunty 3 weeks ago"
date: 2009-05-21
forum: Hardware
---

### Post by jbang on 2009-05-21
I have been ruuning Kubuntu on my Lenovo T61 laptop since 7.10 came out, with only minor problems.

I have been running 8.04 since it came out, but never got around to upgrading to 8.10, because of driver issues with my nVidia card.

3 weeks ago I upgraded form 8.04 to 9.04 (Jaunty), and although I did get some error messages about packages that couldn't be upgraded most things seemed to work fine.

My disk was a 160GB SATA Seagate Momentus drive that came with the laptop. The root-partition (the only one apart from the swap partition) was ext3 formatted.

I never fixed the very minor problems arising from the not-upraded packages, since I was switching hard drives anyway. The new drive was a 500 GB SATA Seagate Momentus.

Installing Jaunty on the new drive went smoothly, and everything seemed to work fine. I copied everything on the old drive over to the new one (using an external USB HD cabinet), to sort it out.

That is when my problems started. After running fine for about a week (maybe a little less) my system complained at boot about the drive not being shut down properly (there had been no signs of that being the case when I shut down my system). And I was thrown into a prompt that told me to do a manual fsck because the automatic one couldn't solve the problem.

When I ran fsck there was a lot of messages about reads that resulted in 'a short read'. All that fsck could manage was a lot of files names something like #12345678.

For various reasons I thought I might not have had the HD firmly inserted into the laptop, so I made sure it was firmly inserted, and tried a new install. After all I wouldn't loose much data, since the old HD was still there, unchanged.

When I got the system up and running again, I connected the old HD using the same USB cabinet and started copying again. I didn't get very far before the connection to the old HD was lost. When I tried to reconnect I got the message 'Stale NFS handle' (this from a drive that have NEVER been NFS mounted in it's life). I connected the old HD directly to the SATA controller in my server (running Ubuntu Server 8.04 or 8.10, I can't remember) and ran fsck on it. I got the sme problems as I have just described above (the ones I had woth the new HD). This happened 1-1½ weeks after upgrading to Jaunty on the old HD.

I salvaged most of what was on the drive, and set about finding out what I could do with what I had.

Yesterday (about a week after installing 9.04 on the new HD for the second time) I couldn't boot my system. Again it was precisely the problems as before.

To summarise: 2 different HDs, both SATA, both Seagate, both running in my laptop, 1 160 GB and 1 500 GB and both with an ext3 formatted root partition. Both go belly-up after approx. 1 week after installing Kubuntu 9.04 on them. On a laptop that has been running Kubuntu fine until 9.04 was installed, using the 160 GB drive.

Could anybody advise me as to how I can solve this problem? And most importantly: How to avoid it in the future?

TIA

Jens

---


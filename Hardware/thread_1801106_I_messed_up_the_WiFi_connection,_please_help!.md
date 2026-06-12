---
title: "I messed up the WiFi connection, please help!"
date: 2011-07-09
forum: Hardware
---

### Post by fca_neo on 2011-07-09
Hi,

I own an eeePC 1000 and it worked great for many years with (k)ubuntu without issues... until I messed it up yesterday.

I was trying to set up an ad-hoc connection between computers but never got it to work so I gave up and found an alternative solution. When I wanted to connect back to the regular WiFi (which worked flawlessly before), I was unable to do so. I used the following tutorials:
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)
[http://ubuntuforums.org/showthread.php?t=861388](http://ubuntuforums.org/showthread.php?t=861388)

I immediately though that I screwed the network configuration and since I had just installed a fresh Kubuntu 11.04, I decided to reinstall it (whipping both the root and home partitions). I thought that it would be easier to comb back to the defaults that way than messing up the settings again. To my great surprise, this was not the case and now I cannot use the WiFi connection at all.

Whenever I try to connect to a network, it gets stuck at the authentication step.

I think I changed a hardware setting in the wireless network adapter but I don't know what settings to apply to make it work normally.

Please help me, this is very important. What settings can I use to get the wireless connection back to a functional state?

Thanks a lot for your help! I'll be glad to provide any additional information necessary.

---

### Post by fca_neo on 2011-07-11
Bump. Any ideas?

---

### Post by fca_neo on 2011-07-30
What am I doing wrong in this forum? I never get any answers....

---

### Post by ankspo71 on 2011-07-30
> **fca_neo said:**
> What am I doing wrong in this forum? I never get any answers....

It's not you, it's that 90% of the users here are not very familiar with KDE, and because of that, I'm sure many people will skip over threads tagged with Kubuntu.

> I decided to reinstall it (whipping both the root and home partitions).
Is it possible that when you reinstalled Kubuntu you forgot to place a checkmark in the little checkbox indicating that you would like to reformat the partitions (in the manual partitioning settings)? If the partitions aren't reformatted, most of your files and settings will still remain intact.

Have you tried connecting with a different wireless connection manager, at least to check to see if the problem is with knetworkmanager? 'wicd' is a good alternative for knetworkmanager. I ask this because knetworkmanager doesn't work so great for quite a number people.

Hope this helps.

---

### Post by fca_neo on 2011-09-05
Yes I reformatted the partitions, no issues with that, I'll try wicd and let you know what happens.

Thanks a lot for your help and advice!

---


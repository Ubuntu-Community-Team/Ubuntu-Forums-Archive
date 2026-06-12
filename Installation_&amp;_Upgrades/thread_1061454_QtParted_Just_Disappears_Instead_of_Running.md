---
title: "QtParted Just Disappears Instead of Running"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by NowIsAllWeHave on 2009-02-05
I installed QtParted through Add/Remove and no errors were reported on the install. When I try to run it from the menu system, I see it appear on the status bar with the spinning hourglass, but after a period of time, it completely disappears and no matter how long I wait, and QtParted never starts.  Both the hourglass and the word QtParted both disappear from the status line at the same time, yet it was successfully installed through Add/Remove.

I tried the "gksu qtparted" in a terminal window that was suggested in a previous post, and indeed the program starts, but as soon as I click on the hard drive to see the partitions, the program says "getting information", and then the program disappears from both the status bar and the screen and it never returns.

I tried an uninstall of QtParted and reboot, then a reinstall of QtParted and reboot, but the result remains unchanged. I've tried QtParted on a fresh boot with no other programs running on the status bar, but I still get no result from the menu system approach.

When I activate Windows XP through my dual-boot and run Partition Magic 8 (which QtParted is said to be a clone of), Partition Magic shows everything is normal on the hard drive, so I can't verify that there seems any errors on the hard drive that are preventing QtParted from running (besides, I would assume QtParted would report the errors rather than just disappear).

I am using Kubuntu 8.04, since Kubuntu 8.10 gives me only a black, empty desktop on my Dell GX260 with the motherboard Intel video chip, so 8.10 is totally useless until the black or empty screen problem with many video cards (as identified within other forum threads) finally gets fixed in 8.10 (so 8.04 it is!). I have a 120 GB Western Digital HD which was first partitioned within Windows XP on another computer by Partition Magic 8. Initially, XP was installed and there were no HD disk errors, and then after the failed attempt to install 8.10 (and a reformat of the partition set up as ext3 for Ubuntu), finally 8.04 was successfully installed in the ext3 partition without any HD disk errors and 8.04 has been running as expected for a new install (well, it's about a week old). I have 512 MB of memory and a 2 GB swap partition.

I would like to get QtParted to run from the Menu system normally, which I assume is possible but is not yet what I have attained.

---


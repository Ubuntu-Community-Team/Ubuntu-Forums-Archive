---
title: "How to: Shrink Vista Partition"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by zalberico on 2009-01-03
I have had an annoying experience trying to shrink Vista in order to dual boot with ubuntu.  Since Vista makes everything difficult I'd thought I'd create this easy to find how to in order to help somebody out.

If you're trying to use the ubuntu live cd to shrink Vista and dual boot and it keeps failing to partition you likely searched the internet and found this how to: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

This how to assumes, however, that Vista's shrinking tool isn't a broken piece of **** (much like the rest of the operating system).  If you try that way you'll likely get an access is denied message for no apparent reason even if you are the administrator on the account.  Strangely I couldn't find any solution to fix this problem using Vista's shrinking tool, so as is usually the case with a windows program there is a better alternative that works.

This program: [http://www.partition-tool.com/download.htm](http://www.partition-tool.com/download.htm)
Does a great job although it does take a while to resize vista.  Then you'll be able to use the live cd to install ubuntu and have some freedom from vista.  You may, as I had to, have to choose manual partition during the live cd install because when it tries to do it for you it is confused.

Don't fret though, if you don't know what to do it's not too bad:
First click manual partition
Second click where it says free space
Third click make new partition
Fourth make the partition the size you want leaving 2000mbs for a swap and set the mount to / (root)
Fifth make a new partition, change ext3 to swap using the remaining 2000mbs

Then continue with the installation :-)

I hope this guide helps some people who were in the same position as me, let me know if you need clarification and then we can burn our vista disks and mandatory vista required programs around a campfire together enjoying smores and hot chocolate.

---


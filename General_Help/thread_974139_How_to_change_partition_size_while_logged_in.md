---
title: "How to change partition size while logged in?"
date: 2008-11-07
forum: General Help
---

### Post by wyth on 2008-11-07
Howdy all,

I have an oddball question.  I *know* that generally you need to use a live CD to grow or shrink a partition.  However, I'm in a bind where that isn't possible, and I absolutely need to grow a partition in order to create room for an upgrade.  I believe this is possible with parted or fdisk, and the change takes place on a reboot, but I'm just not clear on it.

Here's the situation:

A couple years ago I save my parents from getting a new computer by slapping Ubuntu on it when their Dell became so trojan and virus -ridden that all the Athenians and penicillin in tech world couldn't help.  They've been doing just great with it.  However, as a safety measure, we saved about 20GB of Windows partitions -- their data, and the Windows data, in case they wanted to go back to Windows.  Years later, that ain't happening.

I live half a continent away, and I manage their computer by logging in via VNC on a VPN.  Generally this works.  However, with the 8.10 upgrade, I'm finding that there is not enough room left in their root partition to run the upgrade.  I nixed the Windows partitions; one was adjacent to the root partition, and their swap, home, and another nixed Windows data partition are all in an extended partition.  I *want* to grow the root partition from 4GB to 12GB, taking over the empty former Windows space.  But Gparted won't let me do this because I'm logged in -- and I can't do it otherwise, because I have to log in via VNC in order to do this stuff.

This brings me to parted, fdisk, and any other command line tool that might work.  I seem to remember way *way* back being able to change a partition's size using one of those tools, but the actual change doesn't occur until you restart the machine -- then it runs through the process, and you boot into a new larger (or smaller) partition.

And that's where I'm lost.  I cannot recall which tool it is or how to accomplish that task.  I'm not even certain that was possible on *nix machines -- it may have been an old Windows tool that I used once long ago.

Any ideas here?

---


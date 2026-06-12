---
title: "Plug USB drives no nautilus open"
date: 2009-03-01
forum: Hardware
---

### Post by iosifidis on 2009-03-01
Hello,

I face a problem long time. Here's the story.

I have Ubuntu 8.10. My partitions are 1 for the OS, 1 for home (to keep files without first keep backup) and 1 for swap.

When I plug a USB disk on my computer, nautilus stays closed. I must manually mount the device from Places menu. Then nautilus is opened.

This might happened from the time I tried to make a live USB on 8.04. I pressed cancel during the procedure since it gave me 6 hours to create the disk.

Well, I deleted the files:
.hal-mtab
.hal-mtab-lock
inside /media folder. It didn't solve my problem.

I upgrade to 8.10 but still didn't help.

Then due to other issues, I reinstalled 8.04 but it didn't solve it.
I fresh installed 8.10 but still problem exists.

When I use Live CD, the automount and autonautilus work fine. So the device is working. There must be something in my home partition. Don't know what to do.

Does anyone have an idea how to solve it?

---

### Post by iosifidis on 2009-03-15
Hello,

Well, here's the thing.

I made a fresh installation. I have 3 partitions:

1st is the root /
2nd is the home /home
3rd is the swap

So when I make an installation, I don't have to keep backup. Now I made a fresh install but I created another user, I copied all files there and erased the old user. There were files kept there that when I did fresh install, using the same user, there were some files kept in there, preventing the automount fucntion.

---


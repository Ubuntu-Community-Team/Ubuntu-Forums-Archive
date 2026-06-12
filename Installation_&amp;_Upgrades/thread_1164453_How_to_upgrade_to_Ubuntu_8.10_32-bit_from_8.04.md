---
title: "How to upgrade to Ubuntu 8.10 32-bit from 8.04"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by 2048Megabytes on 2009-05-19
[SIZE="3"]Is there anyway you can upgrade your desktop personal computer from Ubuntu 8.04 32-bit to Ubuntu 8.10 32-bit without having to wipe out your hard drive?

Also, I just found out that the hard drive I installed Ubuntu 8.04 is about 70 gigabytes in size but only has about a 40 gigabyte partition.  Is there any easy way to expand the partition?[/SIZE]

---

### Post by Sub101 on 2009-05-19
You can update Ubuntu using the Update Manager, an option should appear at the top of the window.

And I believe using a Live CD you can increase the size of your partitions using GParted.

---

### Post by 2048Megabytes on 2009-05-19
> **Sub101 said:**
> You can update Ubuntu using the Update Manager, an option should appear at the top of the window.

[SIZE="3"]The option isn't there to upgrade to Ubuntu 8.10 in update manager, I looked already.

Where do you get a copy of G-part for Ubuntu?[/SIZE]

---

### Post by Mark Phelps on 2009-05-20
> **2048Megabytes said:**
> The option isn't there to upgrade to Ubuntu 8.10 in update manager, I looked already.

Where do you get a copy of G-part for Ubuntu?
Go to System --> Administration --> Software Sources. Click the Updates tab.  Change the selection on the Release Upgrade pulldown to Normal Releases.  Close out.

Select Administration --> Update Manager.  Should now get a notice at the top that an upgrade is available.

It's GParted, not G-part, and it's available from the distrowatch.com page about 1/3 way down the left side under Latest Distributions.

---

### Post by 2048Megabytes on 2009-05-28
[SIZE="3"]Thanks for the tips Mark.  I got it to work.  There were a few errors in the file path you gave me.  Your tips were good enough for me to figure out though.  I corrected the errors below:

Go to System --> Administration --> Software Sources. Click the Updates tab. Change the selection on the Release Upgrade pulldown to Normal Releases. Close out.

Select System --> Administration --> Update Manager. Should now get a notice at the top that an upgrade is available.[/SIZE]

---

### Post by Mark Phelps on 2009-05-28
Thanks.  Made the corrections you mentioned in my earlier post.

---


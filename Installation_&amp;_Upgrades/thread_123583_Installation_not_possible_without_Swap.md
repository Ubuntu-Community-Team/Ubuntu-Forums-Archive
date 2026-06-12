---
title: "Installation not possible without Swap?"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by nachtmensch on 2006-01-30
Hi,
I've tried to install Kubuntu on a harddisk with only one large ext3fs partition. I thought it would be possible to install Kubuntu without creating a swap partition. When the installer proceeds to the partition dialogue, I choose "Use Existing Partition As /" and "Don't format, leave data" (I have some music files I want to keep). When I choose "Save Table and proceed" nothing happens, just the screen reloads.
Any suggestions? Do I need a Swap partition so that the installer continues??

---

### Post by bartbes on 2006-01-30
I think so, but are you sure you have configured it right, like mounting the partition to /, make it bootable and is it a **primary** partition (I did the last one wrong myself;)), I remember I got the warning that I hadn't got a swap, so I think you need it

---

### Post by lha on 2006-01-30
[QUOTE=nachtmensch]Hi,
I've tried to install Kubuntu on a harddisk with only one large ext3fs partition. I thought it would be possible to install Kubuntu without creating a swap partition. When the installer proceeds to the partition dialogue, I choose "Use Existing Partition As /" and "Don't format, leave data" (I have some music files I want to keep). When I choose "Save Table and proceed" nothing happens, just the screen reloads.
Any suggestions? Do I need a Swap partition so that the installer continues??[/QUOTE]

AFAIK, installer won't let you install on a drive with an existing Linux install without formatting it first. Is this your case? Maybe installer just wants a freshly formatted partition for root?

Swap is not compulsory but why on earth you want to go without swap?

---

### Post by nachtmensch on 2006-01-31
Finally, it worked. You just have to set bootable flag off and then on again. (Would be better if there was some kind of error message.)
It is also possible to leave the data.

Why I don't need/want a swap partition:
1. It should be a home fileserver. It has 512 MB Ram, but doesn't need a GUI. I think the machine would never need more then 512 memory for just some NFS exports.
2. Is my harddisk full, where should I create a swap partition without distroying my data (qtparted won't resize my ext3 partition neither will parted ("your partition has a strange layout, i can't resize this) ).

---

### Post by lha on 2006-01-31
[QUOTE=nachtmensch]2. Is my harddisk full, where should I create a swap partition without distroying my data (qtparted won't resize my ext3 partition neither will parted ("your partition has a strange layout, i can't resize this) ).[/QUOTE]

See the bottom of [this page]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html").

---


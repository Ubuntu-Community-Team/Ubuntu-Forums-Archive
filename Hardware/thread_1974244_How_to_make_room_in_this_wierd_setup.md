---
title: "How to make room in this wierd setup"
date: 2012-05-05
forum: Hardware
---

### Post by PfromD on 2012-05-05
Hi. So I thought I'd would do the upgrade from 10.04 LTS > 12.04 LTS, and quickly the process complained about not having enough space.
I then went into Windows to use Partition Magic, because I'm more comfortable with that and ended with HD setup looking like this:

| windows | 1,5 GB free | Linux main | swap | 

The question now is how the h..  to make the newly freed extra 1,5 GB a part of what I called 'Linux main' as it's become a free space BEFORE the main (leave out the 1,5 GB free and you have the prior partitioning). I had to use rescatux to even start the computer up again as I was a little to hasty in what I did initially. There isn't any obvious way of doing it, based on my limited knowledge of the Ubuntu disk tool.
It ought to be possible to more or less move the main up, thus leaving the 1,5 GB behind it and then include in the same partition, right? But how ..
ARG! help.

---

### Post by ahallubuntu on 2012-05-05
Gparted (available in Ubuntu, probably still on the live Ubuntu CD for 12.04) can resize and move partitions.

You can just resize your Linux main partition in Gparted.  It's graphic-oriented: just right-click on the partition and say "Resize/Move" and expand it out to the maximum size.

Gparted is also included on the great utility distro called Parted Magic (unrelated to the windows "Partition Magic" tool).  Google for "parted magic" if you want to download/burn/boot the CD - really handy to have around.

---

### Post by uRock on 2012-05-05
Running Bleachbit may clear up enough space to run the upgrade. It will remove all obsolete packages. I just ran it and it cleared up almost 250MB. If you are running on an older install, then you are likely to clear up much more space. (My install is only a two months old.)

Since you are running 10.04, it is likely you have several hundred megabytes just in old kernels which can be removed via Bleachbit or Synaptic Package Manager.

---

### Post by PfromD on 2012-05-06
sigh .. as expected the Gparted way isn't as straight forward as one could have hoped: I've tried every which way and it doesn't give me the option to resize the 'main'.
Does it make any difference in this regard that the whole Linux portion is on an extended partition, so that the two (three) Linux partitions are in a partition of it's own, sort of?
It's been set up like this by Linux it self, way back when I installed 7.10

and by the way .. can bleachbit do something the pretty extensive list of boot-up options too? I thought the 'system clean up' (don't know what it's called in english as I'm running Ubuntu in Danish) would do it, but it doesn't :(

---


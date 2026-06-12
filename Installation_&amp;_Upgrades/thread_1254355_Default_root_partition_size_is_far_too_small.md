---
title: "Default root partition size is far too small"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by Pjotr123 on 2009-08-31
The installer on the Live CD is Ubiquity. The default proposal from Ubiquity for the root partition size of Ubuntu, when creating a dual boot with Windows, is far too small: only 2,5 GB!

With a root partition of 2,5 GB, you can't install any extra software or even process all updates. The default partition size should therefore be a lot bigger.

Of course it's easy to change the partition size with the slider that Ubiquity provides. But most Linux beginners won't realize that, and will assume that Ubiquity proposes a workable partition size by default.

This happens both in Jaunty and in the current test versions of Karmic. I've reported this as a bug on Launchpad. Feel free to support it there:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/421407](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/421407)

Greetz, Pjotr.

---

### Post by Bartender on 2009-08-31
I don't know that this is a bug.  I imagine that there were probly several debates about how to set up the default partitioner, and they settled on a bare minimum as a starting point.

No matter where they put it, there would be complaints.  What about all the people installing Ubuntu to old PC's with small HDD's?

Perhaps there should be a big "NOTICE" sign on the installer page that makes it clear the slider is set by default to a very small sliver and it's up to the operator to choose what they want?

---

### Post by drs305 on 2009-08-31
I wrote two guides about this issue. The first tells you why it happened and how to reinstall without the same thing happening:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

The second guide tells you how to expand / to make it a usable size, taking space from Windows.
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

This continues to plague new users and a bug report was filed. Hopefully the installation process will change and become clearer when the "side by side" option is chosen.

---

### Post by Pjotr123 on 2009-08-31
@Bartender: it definitely is a bug.... When you want to install all updates after a fresh installation of 9.04, you get an error message: not enough space! 

A very bad first impression for a beginner, and a blow for his confidence in the reliability of the default choices with which he is being presented by Ubuntu.

In short: a nasty bug, much worse than a mere usability "paper cut". But luckily one that's easy to fix for the developers of ubiquity. :)

To anybody who agrees: please support the request for change: 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/421407](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/421407)

Everyone's help is being appreciated. :)

---

### Post by Topsiho on 2009-08-31
Hello Pjotr12345,

I supported your bug report. Though I did not notice this my self as I always partition my disks manually, I am really shocked by this stupid bug. There is no excuse for it at all: a "feature" that wrecks a system is not a wanted feature.

Ik heb gezegd :)

Topsiho

---

### Post by Pjotr123 on 2009-08-31
I've contacted the package maintainers of ubiquity about this bug. In this thread, I'll keep you all informed about their reaction.

@drs305: I've confirmed your previous Launchpad bug report on this issue.

---

### Post by Pjotr123 on 2009-09-01
The matter has attracted the attention of Colin Watson, a member of the Ubuntu Installer Team. He has changed the package indication of the Launchpad bug report, from "ubiquity" into "partman-auto". 

Apparently the problem is not in ubiquity itself, but in the automatic partitioning tool.

Anyway, it seems that the right people are looking at this bug now. This is a good sign. :)

To be continued.

---

### Post by Glenn nl on 2009-09-02
Awesome news :)
Lets hope it will be fixed soon in karmic :)

---

### Post by drs305 on 2009-09-02
> **Glenn nl said:**
> Awesome news :)
Lets hope it will be fixed soon in karmic :)

The devs are on it. I filed a bug about a month ago but several more reports were filed recently. Pjotr12345 has been especially helpful in documenting the bug and communicating with the devs. 

It was initially designated a "ubiquity" bug but investigation by the maintainers, including Colin Watson, determined it was actually a bug in the "partman-auto" package. The importance has been upgraded to "high" and they know it effects at least jaunty and karmic. 
UPDATE: The maintainers decided it *was* an ubiquity problem after all, since ubiquity passes the instructions to partman-auto. Not that it matters to us users which one needs fixing. ;-)

Here is the bug tracker:
[https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/421407]("https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/421407")

---

### Post by Pjotr123 on 2009-09-02
I'm confident that they'll fix this quickly. Can't be hard to do, I think (although I don't know anything about coding myself).

Most likely, they will only fix Karmic and not Jaunty. They never change an iso of a stable released version. The only exception is, of course, point releases of LTS versions.

Doesn't matter much, because next month Karmic will be released. :)

---

### Post by Pjotr123 on 2009-09-03
The solution that the developers will apply, will probably be to assign half the available space above the first 2,5 GB (absolute minimum), to the Ubuntu root partition. By default; of course a user will still be able to change this default setting during installation.

A good solution, in my opinion. Although I would have liked the absolute minimum to be set somewhat higher, let's say at 5 GB. But that might of course create difficulties on some machines, e.g. netbooks with a 4 GB flash disk.

Anyway, I think a fix is only days away. I'm looking forward to test it (next alpha release of Karmic?).

---

### Post by Pjotr123 on 2009-09-19
Alpha 6 of Karmic isn't fixed... Ubiquity still has the same bug. :(

---

### Post by Pjotr123 on 2009-10-08
The problem has been solved! Today's daily build of Karmic, has been fixed. Great news! :)

See the attached screenshot of the default disk partitioning proposal.

---

### Post by drs305 on 2009-10-08
I was a bit disappointed that the fix was only going to be made to Karmic and not to Jaunty. This means that we will continue to see new members of the Ubuntu community experience this bug. 

If you see a post about installing Jaunty side by side with Windows, please provide the user with a caution about Step 4 in the partitioning process.

Pjotr123 thanks for your efforts in getting this bug resolved, and to Colin Watson, who has lots of things on his plate but managed to work this problem as well.

---


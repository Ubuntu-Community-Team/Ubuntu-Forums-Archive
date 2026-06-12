---
title: "Uninstall Ubuntu on Windows-Ubuntu machine?"
date: 2008-07-29
forum: General Help
---

### Post by muppett on 2008-07-29
Hello

I've looked around a bit and i've just got a bit confused. My Ubuntu 7.10 partition has gone pear shaped and i need to uninstall it, making space for windows. Then maybe i'll think about installing Hardy Heron.

I don't have the Windows CD (can't find it anywhere). Is there another way of doing it without?

Thanks

---

### Post by phidia on 2008-07-29
There are two methods for unistalling ubuntu listed at [this thread]("https://answers.launchpad.net/ubuntu/+question/33413").
Hope that helps.

---

### Post by steveneddy on 2008-07-29
If it is XP or Vista, just tell the built in partitioning tool to take over the Ubuntu partition and merge it with the existing Windows partition.

---

### Post by muppett on 2008-07-29
> **phidia said:**
> There are two methods for unistalling ubuntu listed at [this thread]("https://answers.launchpad.net/ubuntu/+question/33413").
Hope that helps.

Those methods both require the Windows CD.

Is there any other way?

Thanks

---

### Post by ladr0n on 2008-07-29
Download the [Parted Magic]("http://partedmagic.com/wiki/PartedMagic.php") live CD.  Boot from it and use its disc partitioning utility to delete the Ubuntu partition and resize the Windows partition to fill the empty space.  You will want to defrag windows a couple times before doing this, as resizing a broken NTFS partition could cause data corruption.

---

### Post by muppett on 2008-08-14
Thanks for the help!

How will i know which partition to delete, will they be clearly labelled or in some sort of code?

Thanks

---


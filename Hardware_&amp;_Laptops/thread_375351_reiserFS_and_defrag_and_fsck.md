---
title: "reiserFS and defrag and fsck"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by bmhm on 2007-03-03
[FONT="Verdana"]Hi folks!

I installed ubuntu on a reiserFS partition, because reiserFS is told to be faster than ext3. I don't know whether it is or not, just got some questions:

* How do I set-up an auto-check every 30 mounts?
* Is reiserFS as fragment-resistent as ext3?
* Is reiserFS really faster?
* Anything else I should know?

Anyway, no problems so far.

Regards,
-> bmhm[/FONT]

---

### Post by Ryba on 2007-03-03
> **bmhm said:**
> [FONT=Verdana]I installed ubuntu on a reiserFS partition, because reiserFS is told to be faster than ext3. I don't know whether it is or not, just got some questions:[/FONT][FONT=Verdana]
No offensive but typically with something as sensitive as the file partition which is not usually easy to change around, I tend to recommend people do more research into the pros and cons first. However, I myself run reiserfs as well and have done much research between ext3 and resierfs.

[/FONT]> **bmhm said:**
> [FONT=Verdana] * How do I set-up an auto-check every 30 mounts?[/FONT][FONT=Verdana]
Well, actually the filesystem does an integrity check on itself on every single read access it does.

[/FONT]> **bmhm said:**
> [FONT=Verdana]* Is reiserFS as fragment-resistent as ext3?[/FONT][FONT=Verdana]
ext3 is not really fragment resistent at all. I'm not sure why you say it is. Maybe there is another hook or kernel module that does this but ext3 itself is not.

reiserfs is fragment resistant in the sense that everytime it reads a file, it does relocate the file and rehash the BST tables if it determines that the file is sitting on a sector that is about to go bad or if the file is being more frequently accessed then some other files above it in the tree listing.

[/FONT]> **bmhm said:**
> [FONT=Verdana] * Is reiserFS really faster?[/FONT][FONT=Verdana]
There is no if ands or butts about this one. The best way to test this with "human" eyeballs is to get a removable media device like usb keypens and to format them into the different filesystem formats. then just use them normally for reading and writing thigns to the system and see how they go. my best test is to compile and clean and compile again something on the usb device. i find reiserfs to be the fastest of them all (but to be fair I did not try jfs or xfs).

[/FONT]> **bmhm said:**
> [FONT=Verdana] * Anything else I should know?[/FONT][FONT=Verdana]
I'd just recommend doing google searches on pro/con of ext3 and reiserfs. then determine the merits based on what you find to be the best fit for yourself.
[/FONT]

---

### Post by bmhm on 2007-03-04
[FONT="Verdana"]I took a look at english and german wikipedia before using reiserFS.

wait, here are the links:
> [http://en.wikipedia.org/wiki/ReiserFS#Performance](http://en.wikipedia.org/wiki/ReiserFS#Performance) says:
"ext3 in version 2.4 of the Linux kernel, when dealing with files under 4 KiB and with tail packing enabled, ReiserFS is often faster by a factor of 10&#8211;15."

and:
> There are no programs to specifically defragment a ReiserFS filesystem, although tools have been written to automatically copy the contents of fragmented files hoping that more contiguous blocks of free space can be found. However Reiser4 will have a repacker that takes care of optimizing file fragmentation.

> [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems) says:
* reiser stores about same metadata as ext-systems
* filenames in ext may be longer
* reiserFS allows tailpacking (allthough i disabled it)
* reiser allows Block suballocation

Anyway: [http://en.wikipedia.org/wiki/Tail_packing](http://en.wikipedia.org/wiki/Tail_packing) recommends to turn off tail packing, if you don't need every single bit of your HDD for performance reasons.

That's why I choose reiserFS.


Still, in fstab, I can set check to 1, and on every startup reiserFSck is being executed...[/FONT]

---

### Post by bmhm on 2007-03-11
> **bmhm said:**
> [FONT="Verdana"]
Still, in fstab, I can set check to 1, and on every startup reiserFSck is being executed...[/FONT]

*bump*

---

### Post by dejitarob on 2007-03-11
[quote=bmhm]on every startup reiserFSck is being executed[/quote]
I get the same thing too and can't find any info on fixing this. I have been using reiserfs since Hoary (on Gentoo as well) and just noticed this when I upgraded to Edgy. I tried reverting back the changes to UUID in my /etc/fstab and while fsck says the reiserfs partition is clean, fsck still runs at every boot.

---

### Post by bmhm on 2007-03-21
> **dejitarob said:**
> and while fsck says the reiserfs partition is clean, fsck still runs at every boot.

[FONT=Verdana]That's why I disabled it. But that's a bad option somehow... Do I HAVE to reboot from LiveCD to be able to run fsck?[/FONT]

---


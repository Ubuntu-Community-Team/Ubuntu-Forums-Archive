---
title: "Grub"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by bigbird on 2009-07-04
How do I Figure out which version and how much disc space is allocated to that version.

Or should I ask how do I minimize all but the latest and my 8.04 versions on my hard drive with out screwing up everything while keeping all critical files accessible by all.

Sorry I realize I have asked allot, can any one tackle this and help me Please.

I do understand how to use partition software,
I do not get GRUB Im not a real whiz at command line thing I have survived a few bouts with Ubuntu command line fixes though.

Mostly how do I connect a version with the partition so I can re allocate it.
And re direct stuff like my documents within each version to a central partition. ](*,)

---

### Post by dandnsmith on 2009-07-04
> **bigbird said:**
> How do I Figure out which version and how much disc space is allocated to that version.

Or should I ask how do I minimize all but the latest and my 8.04 versions on my hard drive with out screwing up everything while keeping all critical files accessible by all.

I assume that what you're not asking is how to find the space allocated to different versions of grub, but do want the space used by the various ubuntu installs.

Look into the du and df commands to get space used, and use the partition software to shrink the relevant partitions.

> **bigbird said:**
> I do understand how to use partition software,
I do not get GRUB Im not a real whiz at command line thing I have survived a few bouts with Ubuntu command line fixes though.

Mostly how do I connect a version with the partition so I can re allocate it.
And re direct stuff like my documents within each version to a central partition. ](*,)

I'm not sure of some of what you're trying to ask here. Did you install each version to a different partition?
Do you have your data on a separate partition?

The showid (I think) command will get the UUID for a partition, and that you can relate to the grub entries for booting.

---

### Post by darolu on 2009-07-04
I didn't understand the questions very well but I think I got the overall idea just fine.

If I got it right, you want to see how many partitions do you have, in which partition is Ubuntu and what partition has Windows, know their size and change them.

The easiest way to do all this, is using **Gparted**, it will show you the configuration of all your hard drives, their partitions, size, etc... in a easy to understand way (with colour bars and all!) is easy to *re-allocate* disk space too. Install it with "sudo apt-get install gparted" or from Synaptic.

Now, here's the part that confused me a bit on your question, probably what you want to change is the order of OS in the GRUB list; once a OS is installed on a partition you can't change it to another unless you reformat everything; but what you can do is change the order GRUB displays them on the boot loader screen (when you turn on your computer) and even hide options; the easiest way to do this is with **StartUp Manager**, a program that basically is a GUI of GRUB configuration file (/boot/grub/menu.lst). Just install it with "sudo apt-get install startupmanager" or from synaptic.

You can also use manual (console) tools, **fdisk** can help you with partitions and you can edit grub manually with any text editor (i.e. vim or gedit) the file you need to edit is: /boot/grub/menu.lst

Read this links for more information:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[http://whoopis.com/howtos/man.php?query=fdisk&type=2&section=8](http://whoopis.com/howtos/man.php?query=fdisk&type=2&section=8)

---


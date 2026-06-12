---
title: "Ubuntu Kernel Vs Vanilla Kernel"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by EJeanmaire on 2009-10-25
I haven't seen anything posted on this subject in the past few years; so without further ado, what are the differences between the Ubuntu kernels (more specifically Jaunty and Karmic these days) versus the Vanilla kernels from kernel.org .  I usually like to compile the vanilla kernels and cut the fat on extra drivers and hardware support for items I do not need, but I'm wondering if there are custom drivers and enhanced features in the Ubuntu patched kernels that I am losing out on?  Can anyone shed some light on this?

---

### Post by EJeanmaire on 2009-10-27
Hmm, I was hoping someone would be able to shed some light on this...

---

### Post by rippin on 2009-10-27
> **EJeanmaire said:**
> Hmm, I was hoping someone would be able to shed some light on this...

Ignore - double posted - oops!

---

### Post by rippin on 2009-10-27
> **EJeanmaire said:**
> Hmm, I was hoping someone would be able to shed some light on this...

Without getting into specifics, vanilla includes the kitchen sink and Ubuntu's includes the entire kitchen with stove, refrigerator, sink and table with chairs ... IMO.

---

### Post by jsowoc on 2009-10-27
I'm sure you could find an exact listing of what was changed from the vanila kernel to the ubuntu kernel, but I'm not sure how much use that would be to the average user.

One good reason to stick with the Ubuntu kernel is the "free updates" you get while maintaining stability. Moving from 2.6.29 to 2.6.30 to 2.6.31, you need to recompile drivers and could potentially run into compatibility problems with some programs.

The Ubuntu team takes all the important stuff from 2.6.30 and migrates it to a special 2.6.29-ubuntu2, then from 2.6.31 and migrates it back to 2.6.29-ubuntu3 etc. One specific thing I know they ported back was a fix to ext4.

Does this sort-of answer your question, or were you looking for a detailed changelog? (you can probably find it by downloading the kernel sources from Ubuntu)

---

### Post by shaggy999 on 2009-10-28
It should be pointed out that it's not just the patches, but when you get the kernel there are HUNDREDS of compile options and the ubuntu developers go through and select sane default values that will work on the widest array of systems. So it's not so much "what was added" but "what was selected and compiled".

The basic process goes like this:

1) Get kernel
2) Apply security patches to fix broken stuff
3) Go through and set good values for all variables
4) Compile
5) Package
6) Test
7) Repeat if things break

As was mentioned above, you generally don't want to muck with trying to create your own kernel because it's very easy to break everything. For example, some stuff is specifically compiled against the ubuntu kernel like drivers. If you try to compile your own kernel it could lead to a cascading effect of having to download, configure, and compile other packages that link into the kernel.

If you really want to fiddle with kernels check the Master Kernel Thread: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by shaggy999 on 2009-10-28
Oh, and you can always look at the changelogs:

[http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.28-16.55/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.28-16.55/changelog)

---


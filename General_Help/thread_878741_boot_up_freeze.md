---
title: "boot up freeze"
date: 2008-08-03
forum: General Help
---

### Post by penquin on 2008-08-03
I tried to boot up my computer after a Update/Upgrade it had a new kernal and now it freezes before the progress bar shows up.  I tried in recovery mode, but it freezes to.  I need help.  Although I can recover most of my data. The data I can't get is not vital. It is password protected and read only.

---

### Post by jean noel on 2008-08-03
I had nearly the same problem yesterday after downloading some updates. Although I would get in Ubuntu, my screen would freeze. Today I was stunned to see that everything was Ok.(Touch wood).
Good luck.Any advice (especially commands in terminal) would be welcome,especially as I was considering formatting and reinstalling Ubuntu.

---

### Post by coffeecat on 2008-08-03
Can you boot into the previous kernel, and what was the version number of the newer kernel?

---

### Post by penquin on 2008-08-03
I don't have that option due to sum.  I don't think that will solve the problem though

---

### Post by jubilee0824 on 2008-08-03
If you had the proposed repository on, and installed 2.6.24-20 kernel, it may be a source of your problem.

I don't know too much details of it, but a bag has been filed.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344)

I had the similar problem, so now am booting the older kernel (2,6.24-19) which still works fine! On the side note, I believe that, by default, Ubuntu does not overwrite older kernels, so you should be able to go back to it. And if you decided to delete older kernels manually, it is recommended to keep at least one older kernel.

Cheers

---

### Post by coffeecat on 2008-08-03
> **penquin said:**
> I don't have that option due to sum.

I don't understand what you mean.

> **penquin said:**
> I don't think that will solve the problem though

If a problem is caused by a new kernel, then booting into an old one is the standard way of getting around the problem.

---

### Post by penquin on 2008-08-04
sum= start up manager.  how do you get around this

---

### Post by coffeecat on 2008-08-04
You said you were able to boot up into recovery mode, so I would have thought that you selected that from the grub menu. You should be able to select a previous kernel from the grub menu as well.

If you managed to get into recovery mode some other way, and you are not seeing the grub menu, pressing esc immediately after the BIOS POST screen should bring it up. You have to be quick - perhaps repeatedly pressing esc near the end of the POST sequence will be best.

---

### Post by penquin on 2008-08-05
actually I can't get into recovery mode.  I Thought that is what I wrote.  If I could edit the boot file I could probably get into a different kernal.  Does anyone know if you can edit it in windows?

update I removed menu.lst and replaced it with menu.lst.backup and I am now in it.

---


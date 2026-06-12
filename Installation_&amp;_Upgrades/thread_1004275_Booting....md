---
title: "Booting..."
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by looi76 on 2008-12-07
[FONT="Georgia"][SIZE="3"][IMG]http://img257.imageshack.us/img257/125/06122008305ev6.jpg[/IMG]

I have a duplicate copy of these lines:
Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)

I only have 1 Ubuntu installation. How can I remove the duplicate lines because I don't think there is any use of them, right?[/SIZE][/FONT]

---

### Post by inobe on 2008-12-07
they aren't duplicates, those are two different kernels.

that may have happened after a major update, a kernel update.

edit: this has happened to me using opensuse, it was useful when something broke with a kernel update, i was able to start from the prior kernel.

with ubuntu this has never happened.

---

### Post by cdtech on 2008-12-07
You should keep the recovery mode and at least a last kernel image. If you have issues with the first kernel, you could boot with the old kernel image.

---

### Post by taurus on 2008-12-07
The recovery mode is for when you screw up your machine and won't be able to boot, then you need to boot into recovery mode to fix the problem.

And if you want to remove the older kernel, 2.6.27.7, you can do that with synaptic, System -> Administration -> Synaptic Package Manager.

---

### Post by andreasis on 2008-12-07
If you really just don't want the options appearing on every boot, or only, let's say, the first two options, you can edit your menu.lst file by ```
sudo gedit /boot/grub/menu.lst
``` and commenting out (putting a # in front of) the lines corresponding to the options that you don't want to see in grub.

---

### Post by looi76 on 2008-12-07
Oh! I didn't realise that they were different 8-[. How can I hide Windows XP Professional?

---

### Post by awam66 on 2008-12-07
> **looi76 said:**
> Oh! I didn't realise that they were different 8-[. How can I hide Windows XP Professional?

Edit /boot/grub/menu.lst (that's a lower ase ell not a one) and comment out the lines with Windows (use a # at the line start.

---

### Post by andreasis on 2008-12-07
You can use the command in my previous post or use your favorite editor.

DO MAKE SURE THAT: you comment out all lines related to the windows xp entry like so:

# title		Windows XP Professional
# root		(hdx,x)
# makeactive
# chainloader	+1

and not just

# title		Windows XP Professional
root		(hdx,x)
makeactive
chainloader	+1

This won't remove XP of course.  You can repartition the hard drive by reinstalling ubuntu so you'd have a clean disk with only linux on it, if that's what you'd be looking for.

---


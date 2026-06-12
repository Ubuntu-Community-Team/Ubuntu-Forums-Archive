---
title: "Ubuntu 8.10 Sometimes Fails to Boot"
date: 2009-04-05
forum: Hardware
---

### Post by DBQ on 2009-04-05
Hi everybody.  I am running Ubuntu 8.10 on a Toshiba A75-S209 laptop.  Generally everything works fine.  However, sometimes the system fails to boot (like 60% of the time).  It simply hangs shortly after the booting process begins.  My kernel version is 2.6.27-11-generic.

Any help would be great - this issue is annoying me a great deal, as I usually have to restart my machine several times before the boot finally succeeds.

---

### Post by zigga15 on 2009-04-05
Next time you restart you should press ctl+alt+f3 - this switches to a virtual machine (if you could call it that).

Basically it allows you to see the output of the boot process rather than the pretty loading ubuntu graphic.

Post some of the output around where it hangs so we can help you get a solution.

Generally if it is getting past the grub you may have a problem with your modprobe if you have installed stuff without your package manager.

~ Dan

---


---
title: "64bit or 32 ?"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by dj_unforgetable on 2007-06-11
I've got a brand new T61 and I want to see how the 64bit OS's perform on it (Vista is terribly slow).  I downloaded Fiesty amd64 (it stated this works for both amd and intel processors).  As I understand the Core 2 Duo supports 64bit extensions (EMT64), but when I load the LiveCD, it loads the kernel, then fails (with some unable to load mem resource error) and just restarts the laptop.

Any ideas?  Anyone here try this on their T61's ?

---

### Post by foxmulder881 on 2007-06-11
Try the 32bit version and see if you get the same problem.

---

### Post by Kobalt on 2007-06-12
I don't think it's related to the 46bit version of Ubuntu at all. You may need to use boot options on your computer (it's quite common, don't worry). When you boot your computer with the LiveCD, at boot screen press F6 to access the boot options. At the end of the line, and after a space, enter > noapic nolapicThen press Enter to boot. 
You may need other options, but these are the most common ones. I hope it helps you.

---

### Post by dj_unforgetable on 2007-06-12
Is there a list of these options I need to add that others have come across?

Vista is really frustrating me right now!

---


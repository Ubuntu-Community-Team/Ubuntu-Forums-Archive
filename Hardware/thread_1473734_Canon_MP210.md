---
title: "Canon MP210"
date: 2010-05-05
forum: Hardware
---

### Post by Thomasasz on 2010-05-05
Hello, 

I have this problem: when I try to install Canon MP210's drivers into my Ubuntu 10.04 (drivers from: [http://software.canon-europe.com/products/0010485.asp](http://software.canon-europe.com/products/0010485.asp)) it fails to do that saying, that 'cnijfilter-common depends on libcupsys2 (>= 1.2.1); however
libcupsys is not installed' and 'Error: Failed to satisfy all dependencies (broken cache)'

However, I cannot find any libcupsys2 on Synaptic Package Manager.
What should I do?

P.S. I've made the printer work when I connected it but it cannot print PDF files, although, everything else it can.

Thanks!

---

### Post by Björn on 2010-05-05
Hi, i had the same problem on my mp240 and the thing is that the package in question has been replaced by libcups2. You just have to install a transition package. You can find it here: [http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download)

Hope it helps!

Björn Rask

---

### Post by Thomasasz on 2010-05-05
> **Björn said:**
> Hi, i had the same problem on my mp240 and the thing is that the package in question has been replaced by libcups2. You just have to install a transition package. You can find it here: [http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download)

Hope it helps!

Björn Rask

Oh, it really helped! Now the PDF problem is gone too! 
I am very very thankful for your help!

---

### Post by Björn on 2010-05-05
No probs but thanks =)

---

### Post by Thomasasz on 2010-05-05
By the way, how do i make it print grayscale? :D

---

### Post by Rytis on 2010-08-23
> **Thomasasz said:**
> By the way, how do i make it print grayscale? :D

Someone should answer this :-|

---


---
title: "Resume after hibernate speed"
date: 2011-04-16
forum: Hardware
---

### Post by asadkn on 2011-04-16
There's a serious problem with the speed of resume on Linux. Perhaps not many people use hibernate/resume much. 

I am currently using uwsusp and after resume, everything becomes so laggy it's unbearable. To counter this, I added swapoff -a && swapon -a to the resume hooks. However, swapoff -a by itself is so slow than it takes up to 5 mins to clear up the swap and put it back into RAM. 

I haven't tried swsusp as it wasn't working for me earlier, but does it work the same way? Leaving all the pages on swap after a resume? 

I am sure things would have been better with TuxOnIce but compiling everything is a pain in itself. It would kind of defeat the purpose of using a distro.

---

### Post by asadkn on 2011-04-17
<snip>

---


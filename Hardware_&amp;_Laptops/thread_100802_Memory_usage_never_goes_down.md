---
title: "Memory usage never goes down"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by Ocxic on 2005-12-08
In the system monitor on my menu bar, I find that the mem usage not swap, never decreases unless i reset my computer. why does my system eat my memory like this?

---

### Post by jamesford on 2005-12-08
i think linux handles memory in such a way that as much ram as possible is always used, for example firefox may only use 50 mb, but is allocated 200 mb, so that all ram is always used, but will let it go if another process needs the ram firefox has been allocated but isnt using

thats my understanding anyway

---

### Post by davidsrsb on 2005-12-10
The Linux kernel uses free ram as cache until all is used, so after a while top will show none free. This is not a problem as when an application needs memory this cache is then used. The only figure to worry about is swap file in use.

---


---
title: "Netgear"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by Franz1 on 2009-03-21
I have a wg311 pci adapter on this computer, I have Ubuntu on its own hard drive. I find there are many issues that I do not understand, where can I find a linux driver for this card and how can I make Ubuntu see the other drives on this computer?

---

### Post by cariboo on 2009-03-21
Could open an Applications--Accessories-->Terminal and type:

```
sudo lshw -C network
```

and  paste the output in your next post. 

The other hard drive in your system should show up in the left pane of Places-->Home Folder. In the attached screenshot I have underlined the first partition of my hard drive that has Interpid on it, and storage that is also underlined is my second internal hard drive that is mounted automatically and bookmarked as storage.

---


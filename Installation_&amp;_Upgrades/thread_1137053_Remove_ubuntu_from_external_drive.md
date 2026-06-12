---
title: "Remove ubuntu from external drive"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Unkuiri on 2009-04-25
Hi, I want to remove ubuntu from the external disk drive where I've installed it and install it alongside windows on my main drive but the worst problem is that I can't iniciate my computer without the external drive plugged in because the grub bootloader is installed in it and I can't install it to my main hard drive...:(...what can I do?

Thanks in advance

---

### Post by theozzlives on 2009-04-25
Delete the partition, boot up with your Windows CD, go into "Recovery Mode" and type :```
fixmbr
```. That'll allow you to boot Windows.

---

### Post by Unkuiri on 2009-04-25
Thanks for the reply, but I don't have a windows cd I have a recovery partition on hard drive...and how can I delete the ubuntu partition?from windows?is there a way to do this only with ubuntu live cd?

---

### Post by Unkuiri on 2009-04-25
problem solved with alternate cd...thanks

---


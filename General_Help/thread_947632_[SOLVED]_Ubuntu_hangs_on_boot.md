---
title: "[SOLVED] Ubuntu hangs on boot"
date: 2008-10-14
forum: General Help
---

### Post by 09buntu on 2008-10-14
Hi!

I have installed Ubuntu and about every third boot it hangs. I type luks passphrase and the progressbar then moves about 20% then nothing. After turning power off/on it boots fine then on the next boot it hangs again etc...

I really can't do anything not even switch to console mode to see what's happening. If this was a disk check then I would see it right? Last time I installed Ubuntu it wanted to check my disk every boot (nothing wrong with it btw).. annoying

Anyway, any ideas whats wrong with Ubuntu here?
Thanks

---

### Post by 09buntu on 2008-10-15
Anyone?

---

### Post by woodenbrick on 2008-10-15
When grub comes up press 'E' to edit your boot line and remove 'quiet splash'. That way you will see at which point it is freezing.

---

### Post by Zogg on 2008-10-15
I experience same issue with 8.10. With 8.04 it was all ok.

---

### Post by 09buntu on 2008-10-15
> **woodenbrick said:**
> When grub comes up press 'E' to edit your boot line and remove 'quiet splash'. That way you will see at which point it is freezing.

Thank you very much!
It turned out to be disk checks and nothing wrong with Ubuntu after all.

---


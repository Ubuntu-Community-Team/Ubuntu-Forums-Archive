---
title: "dd to make swap file: segementation fault!"
date: 2006-08-30
forum: Hardware &amp; Laptops
---

### Post by HolyJoe on 2006-08-30
The swapfile working corretly before i upgrade to 2.6.15-26. I got:
reboot sudo swapon /swap.file: invalid argument
aboved message. so i removed /swap.file, and use dd to create a new 512M swap file:
sudo dd if=/dev/zero of=/swap.file bs=1024 count=524288, but i get the following response:
524288+0 records in
524288+0 records out
Segmentation fault

What's wrong about it?

Need any help!
](*,)

---

### Post by bkix on 2006-09-02
hi,

seems to be a bug. i found this solution in a french forum:
try to add a "LANG=en" in front of the dd-command, so your line would be

$ LANG=en sudo dd if=/dev/zero of=/swap.file bs=1024 count=524288

---


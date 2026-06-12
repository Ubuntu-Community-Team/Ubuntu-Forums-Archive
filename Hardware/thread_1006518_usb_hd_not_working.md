---
title: "usb hd not working"
date: 2008-12-09
forum: Hardware
---

### Post by Thoralex on 2008-12-09
Hi!
I just installed ubuntu on my desktop after getting a new drive, and i cannot get my wd mybook to work. The os does not seem to bee able to find it. when i turn it on it starts, and after a few seconds the light flashes a few times and it shuts down. usb mouse and keyboard works, and the hd works on my laptop running ubuntu installed from the same disc. Anyone know what it is? The drive worked on the desktop before reinstalling.

---

### Post by taurus on 2008-12-09
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
dmesg | tail
sudo fdisk -l
df -h
```

---


---
title: "Mounting again...grr"
date: 2009-03-14
forum: Hardware
---

### Post by MissKitty on 2009-03-14
I was having a problem mounting my usb drive, I got that problem fixed. Now I've run into a new problem: My windows partition is no longer mounted! It was working ok before. I was able to go into my windows partition and get any file. It worked without me having to tell it to. This problem only starting when I told it to mounted my usb drive. Don't tell me that every time I want to use an external drive or get something out of my windows partition that I have to go in and use code to tell it to mount.

---

### Post by taurus on 2009-03-14
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by MissKitty on 2009-03-15
I found the problem. A family member in my house was on my lappy in windows and they didn't shut down windows right. When I went into ubuntu, windows was still running therefore not letting me on the windows partition. I'm sure thats not good to have both OS running at the same time. So I'm good now. Thanks!:KS

---


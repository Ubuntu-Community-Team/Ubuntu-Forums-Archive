---
title: "Won't boot to start screen!!!"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by neurosis737 on 2007-07-30
The other day I moved my video card to a different PCI-E slot and now I'm getting "No Device Found" and
a command line. I have no idea how to tell the computer where my video card is. Any help would be really appreciated.

---

### Post by w4ett on 2007-07-30
From the command line type:

```
lspci
```

Take note of the Bus ID of the installed video card and then run:

```
sudo dpkg-reconfigure xserver-xorg
```

and reconfigure your xserver...if your bus id is not automatically detected, when prompted, insert the new Bus ID, complete the reconfigure, save and restart x (<ctrl><alt><Backspace>)

---


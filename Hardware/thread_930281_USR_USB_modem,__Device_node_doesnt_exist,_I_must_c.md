---
title: "USR USB modem,  Device node doesnt exist, I must create it manually after reboot"
date: 2008-09-25
forum: Hardware
---

### Post by travm on 2008-09-25
I bought this modem which claims (correctly so) to support linux.  Ubuntu isnt expressly supported but in the user guide it says for "other unsupported versions of linux" to do the following command
```
ln -s /dev/ttyACM0 /dev/modem
```
When i do this it works great.  aside from the dialup software being rather bland.
The problem is I must do this every time after a reboot.  It seems the symlink is deleted on reboot.
How can I make this permanent?

---


---
title: "Restoring partition with new drive?"
date: 2008-10-08
forum: Hardware
---

### Post by Evo Pete MTL on 2008-10-08
Hey guys,

I tried doing something I'm not sure I can do. Basically I took the whole ubuntu 3fs partition of my old laptop and backed it up using Partimage. After that I took my new laptop and created a linux 3fs partition with a space for swap the same size as my old laptop and then I restored (copied) my old partition onto my new one. But still only windows will boot the boot grub doesn't seem to work. Any idea what should i do?

Thanks,
Pete

---

### Post by Evo Pete MTL on 2008-10-12
Please help me out!!! Thanks in advance.

---

### Post by cariboo on 2008-10-13
You need to install or reinstall grub. The easiest way to do it, is in a terminal type:

```
sudo apt-get reinstall grub

```

Jim

---


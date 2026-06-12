---
title: "Help choosing the right upstream kernel for testing"
date: 2011-01-18
forum: Hardware
---

### Post by ofir_k on 2011-01-18
Hello,

A month ago I opened a bug about some problem with connecting external monitor to my laptop.

Some automated message (from a guy named Jeremy) was added to the bug. The message asks me to check an upstream kernel to make sure the problem is not with the Ubuntu kernel patches.

Anyway, I tried to figure out what I need to do from:
[https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)
but with no luck.

Can someone here help me choose the right kernel?

The bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/692673](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/692673)

Thanks,
Ofir

---

### Post by ofir_k on 2011-01-22
Someone???

---

### Post by frogotronic on 2011-02-17
Your problem is KMS.  Turn it off

```
sudo gedit /etc/default/grub
```

Make this line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

look like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

then

```
sudo update-grub
```

Try the external monitor now.

- CH

---

### Post by ofir_k on 2011-02-18
cement_head, thanks for your reply.

I tested what you said and it doesn't work. I always get a tty screen after boot, and any attempt to go back to the graphical environment fails.

I get errors like:
> intel(0): no kernel modesetting driver detected
when trying to start X.

Someone has an idea?

---

### Post by frogotronic on 2011-02-18
Bummer, worked for me.

How about the XORG Edgers repositories?

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

I actually use the "drivers-only" and the MESA repos, not the full-on XORG EDGERs repo (bit too fresh for me)

- CH

---


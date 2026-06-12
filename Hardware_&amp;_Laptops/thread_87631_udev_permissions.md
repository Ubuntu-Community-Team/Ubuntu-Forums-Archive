---
title: "udev permissions"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by kLy on 2005-11-08
I have a few custom permission rules in /etc/udev/permissions.d/udev.permissions

Specifically for kqemu:

```

# kqemu
kqemu:root:root:0666

# tun
net/tun:root:admin:660

```

Now the modules load fine and the devices show in /dev, but the problem is that the permissions aren't being set as shown :(

In Hoary, this worked and permissions were right, but here in Breezy the permissions aren't being set at boot. What's wrong?

thx

---


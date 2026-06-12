---
title: "Install gcc without network conn"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by olddave1 on 2009-03-31
Hi,

I have installed 8.10 Server amd64. I need to build a device driver for the wireless network USB device. I therefore do not yet have network support. But the install does not include gcc. Is there documentation on how to download onto a USB mem stick on another machine then install from there?

Thx.

David

---

### Post by Partyboi2 on 2009-03-31
You should be able to install it from the ubuntu cd. Put the cd in the cdrom and in the terminal type
```
sudo apt-cdrom add
```
```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by ronparent on 2009-03-31
Or you may be able to install it thru the sysnaptic package. I shows up in my package list as an ubuntu distro, and installed (though optional)!

---

### Post by olddave1 on 2009-04-01
Hi,

Thx. The apt-get commands worked.

David

---


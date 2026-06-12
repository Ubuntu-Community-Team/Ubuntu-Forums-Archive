---
title: "Acsess windows partition from boot"
date: 2008-10-25
forum: Hardware
---

### Post by surfsunadam on 2008-10-25
I'm setting up an ubuntu laptop for my parents.

I have things such as the desktop background and a shortcut to 'My Documents' in 'Places' that come from the windows partition. However, when I boot the computer, these don't show up. I have to first go into places and select the 'S3A2999D001' drive (which is the windows partition) and this seems to mount it. Also, there is no icon on the desktop for this drive on startup.

How do I make this drive accessible to the computer from boot?

It's at /dev/sda1 and is ntfs

thank you :)

---

### Post by shawnrgr on 2008-10-25
```
gksudo gedit /etc/fstab
```

add the following line:

```
/dev/sda1   /media/windows   ntfs   defaults,umask=0222   0   0
```

keep a return at the end of the file (blank line)

save fstab. make sure the folder your mounting it to exists on the system.

```
sudo mkdir /media/windows
```

---

### Post by surfsunadam on 2008-10-25
Worked great, thanks

---


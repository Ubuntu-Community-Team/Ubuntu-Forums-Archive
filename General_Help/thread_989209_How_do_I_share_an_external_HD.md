---
title: "How do I share an external HD?"
date: 2008-11-21
forum: General Help
---

### Post by joelw1351 on 2008-11-21
I have a USB external Hard Drive installed and I would like to share it in its whole. Can I get instructions on how to do this?](*,)

---

### Post by taurus on 2008-11-21
You mean you want to share the external harddrive between Ubuntu and windows?

What filesystem is that harddrive and have you tried to mount it?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by joelw1351 on 2008-11-21
> **taurus said:**
> You mean you want to share the external harddrive between Ubuntu and windows?

What filesystem is that harddrive and have you tried to mount it?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

The USB drive is on my Ubuntu PC and I want to share it with my iMac it is 32formated. I found know way to share the whole drive. Or do I have to put folders in it and then click on each folder?

---

### Post by taurus on 2008-11-21
So you want to share that external harddrive between Ubuntu and mac.  Have you tried to mount it in Ubuntu?

```
sudo fdisk -l
df -h
```

---

### Post by joelw1351 on 2008-11-21
> **taurus said:**
> So you want to share that external harddrive between Ubuntu and mac.  Have you tried to mount it in Ubuntu?

```
sudo fdisk -l
df -h
```

It is mounted on the Ubuntu desktop, but the only way to share it is by installing folders on the USB drive then right clicking and going to share. If I right click on the USB drive icon there is no menu item for sharing. I sometimes drop a file not classified onto the drive to transport it and it is not in a folder. I like to drag the file on the Mac or on the Ubuntu to the drive. I hope that was clear. I just want to see the icon in the Mac.

---


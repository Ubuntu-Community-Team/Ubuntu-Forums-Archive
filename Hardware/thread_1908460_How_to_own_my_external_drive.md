---
title: "How to own my external drive"
date: 2012-01-13
forum: Hardware
---

### Post by cozski on 2012-01-13
Hello

I re-formatted and external drive (500BG Buffalo) to ext3 and everything is fine apart from not having permissions on the drive - it says I don't own it. How do I ensure that I do? Thanks in advance.

---

### Post by BC59 on 2012-01-13
I don't know how you formatted the drive, but the best way is through Disc Utility. From the left panel click on your drive and then from the right panel choose the actions.

---

### Post by Morbius1 on 2012-01-13
```
sudo chown your-user-name /path-to-mount-point
```

---

### Post by cozski on 2012-01-13
> **Morbius1 said:**
> ```
sudo chown your-user-name /path-to-mount-point
```

Apologies, but how do I know where the mount point is? Thanks.

---

### Post by cozski on 2012-01-13
> **BC59 said:**
> I don't know how you formatted the drive, but the best way is through Disc Utility. From the left panel click on your drive and then from the right panel choose the actions.

I formatted the drive using Gparted... if that helps.

---

### Post by Morbius1 on 2012-01-13
It's the location of the mounted partition. When you go into Nautilus where do you access the partition.

/media/????

```
sudo chown cozski /media/????
```

---

### Post by cozski on 2012-01-13
> **Morbius1 said:**
> It's the location of the mounted partition. When you go into Nautilus where do you access the partition.

/media/????

```
sudo chown cozski /media/????
```

It's the one below 'desktop' in this screen capture:

---

### Post by Morbius1 on 2012-01-13
Run the following command from the terminal
```
gksu nautilus /media
```Then right click 1c377532-7407-4ac1-b757-d91c7f7dc368
Select Properties > Permissions > Owner >

---

### Post by cozski on 2012-01-14
Hey, thanks for that, fixed. So am I right in thinking that nautilus is maybe like File Explorer in Windows?

---

### Post by howefield on 2012-01-14
> **cozski said:**
> So am I right in thinking that nautilus is maybe like File Explorer in Windows?

Yep. Nautilus is a File Manager.

---

### Post by cozski on 2012-01-14
> **howefield said:**
> Yep. Nautilus is a File Manager.

Okay, thanks for clearing that up. I have another issue with another external drive.. should I start a new thread or keep it in this one?

---

### Post by howefield on 2012-01-14
> **cozski said:**
> Okay, thanks for clearing that up. I have another issue with another external drive.. should I start a new thread or keep it in this one?

Always best to start a new thread for separate issues. :)

---

### Post by cozski on 2012-01-14
> **howefield said:**
> Always best to start a new thread for separate issues. :)

Okay, will do, thanks :D

---


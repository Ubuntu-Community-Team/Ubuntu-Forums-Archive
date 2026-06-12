---
title: "Cant add music"
date: 2008-07-08
forum: Hardware
---

### Post by adamant715 on 2008-07-08
I cant add any music to my 2 GB Phillips GoGear Mp3 Player, It says the following.

Error opening file '/media/Philips/Alex Band - Tonight.mp3': Read-only file system

help?

---

### Post by Yuki_Nagato on 2008-07-08
_[https://answers.launchpad.net/ubuntu/+question/2252]("https://answers.launchpad.net/ubuntu/+question/2252")_

This might be a start, but I will continue to look.

Your hard drive on the mp3 player might actually not be formatted correctly.

---

### Post by adamant715 on 2008-07-08
I didnt really understand it, not explained very well.

---

### Post by Yuki_Nagato on 2008-07-08
Alright.

First we have to mount the device.  It seems that you have done that already.

Can you try:

```
sudo chmod 666 media/Philips
```

?

We are trying to give everyone the ability to read and write to the mounted drive.

---

### Post by adamant715 on 2008-07-09
The USB is mounted and I typed that and it returned saying this.

chmod: cannot access `media/Philips': No such file or directory

---

### Post by adamant715 on 2008-07-12
No help guys? V_V

---

### Post by Tha1 on 2008-07-12
> **adamant715 said:**
> The USB is mounted and I typed that and it returned saying this.

chmod: cannot access `media/Philips': No such file or directory

Does it really have the folder created, and referenced in fstab?

---

### Post by adamant715 on 2008-07-13
I dont see the folder and idk about the other one.

---

### Post by tech0007 on 2008-07-13
post the output of 'mount' and your /etc/fstab file.

---


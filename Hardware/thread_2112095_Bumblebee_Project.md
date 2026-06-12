---
title: "Bumblebee Project"
date: 2013-02-03
forum: Hardware
---

### Post by chribuntu on 2013-02-03
Hello I am having Nvidia graphics issues so I decided to use Bumblebee. Well I don't know how to run it or anything. Could someone teach me how? I have already download the  Bumblebee 3.0.1 folder

---

### Post by Yellow Pasque on 2013-02-03
First off, do you even have a hybrid/Optimus system? What is output of:
```
lspci | grep VGA
```

If you have both an Intel and nvidia GPU, then you use Bumblebe like so: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by chribuntu on 2013-02-04
I ran the command and I only have an NVIDIA card.

---

### Post by Yellow Pasque on 2013-02-04
Then Bumblebee is not for your system and you should probably elaborate on what issue you are having (including /var/log/Xorg.0.log may be helpful).

---

### Post by Szostak on 2013-02-04
> **chribuntu said:**
> Hello I am having Nvidia graphics issues so I decided to use Bumblebee. Well I don't know how to run it or anything. Could someone teach me how? I have already download the  Bumblebee 3.0.1 folder

You should specify your Hardware, like
O.S: (Distro and Version, bits)
VGA:
CPU:
Perhaps your Notebook Model if you're using one.
So we may have your background :), it's always good to specify when you open a topic.

---


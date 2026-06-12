---
title: "How do I access installed files from Live CD?"
date: 2008-08-27
forum: General Help
---

### Post by colobix on 2008-08-27
MY Ubuntu crashed again so now I have to use my live CD, and I would like to take a backup of some files before I reinstall ubuntu, so how do I do that from the live CD?

Thank you in advance

---

### Post by WRDN on 2008-08-27
Boot the LiveCD, click Places > Computer and then mount the partition Ubuntu or the files are located on.

You can also mount the partition manually if it does not appear in Computer, by entering the Terminal, and first typing:

```
sudo fdisk -l
```

This will allow you to identify the partition Ubuntu is located on. Take note of the device, which will either be /dev/sdaN or /dev/hdaN (where N represents a number).

Now, type:

```
sudo mkdir /media/ubuntu
```

This creates the mount point. Finally, mount the partition:

```
sudo mount /dev/[device] /media/ubuntu
```

---

### Post by colobix on 2008-08-27
Thank you very much:)

---

### Post by colobix on 2008-08-27
But it says Device doesn't exist.
hmm.

---

### Post by WRDN on 2008-08-27
> **colobix said:**
> But it says Device doesn't exist.
hmm.

Can you post the output of fdisk -l, and what you typed/ clicked before the "Device doesn't exist" message appeared.

---


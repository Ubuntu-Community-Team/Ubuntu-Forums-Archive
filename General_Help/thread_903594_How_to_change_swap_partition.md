---
title: "How to change swap partition"
date: 2008-08-28
forum: General Help
---

### Post by SammerHammer on 2008-08-28
Hello, I decided to try out openSUSE, and while partitioning I want to delete my current swap partition, to create an extended partition for SUSE. After that I'll carve up some of my Ubuntu partition to create a replacement swap partition for Ubuntu. I want to know how to designate that newly created partition as the swap partition.

Thanks for your help.

---

### Post by WRDN on 2008-08-28
You can delete the swap partitions, and create new ones without serious problems.
I have recently deleted a swap partition, so as to use another one. After doing so, you will have to do 2 things:

1) Change your fstab file.
2) Change the 'Resume' file

For the first change, open the Terminal and type:

```
sudo blkid
```

This will allow you to identify the UUID of the swap partition. Now, open the fstab file:

```
sudo gedit /etc/fstab
```

Find the line corresponding to the swap partition (it will have the word "swap" in it), and replace the UUID with the one obtained from the blkid command.

Now, you need to edit the resume file. To do this, type:

```
sudo gedit /etc/initramfs-tools/conf.d/resume
```

Again, replace the UUID with the one for the swap partition. The 2nd change is not required, but if it is not done, the splash screen will fail.

---

### Post by drs305 on 2008-08-28
While you are tinkering with the swap file/partition, don't forget the commands swapoff and swapon. Details in the man pages.

---

### Post by SammerHammer on 2008-08-28
Thanks, the instructions work correctly, but I haven't actually partitioned yet. I need to finish the ISO download and then burn it. I'll keep this thread open till I actually install openSUSE (if I can even remember this thread then) :)

---

### Post by SammerHammer on 2008-08-28
> **drs305 said:**
> While you are tinkering with the swap file/partition, don't forget the commands swapoff and swapon. Details in the man pages.

Can I have more details on that?

---

### Post by WRDN on 2008-08-28
> **SammerHammer said:**
> Can I have more details on that?

While altering swap partitions, you must turn them off. To turn swap off:

```
sudo swapoff -a
```

To turn swap on:

```
sudo swapon -a
```

---

### Post by SammerHammer on 2008-08-28
> **WRDN said:**
> While altering swap partitions, you must turn them off. To turn swap off:

```
sudo swapoff -a
```

To turn swap on:

```
sudo swapon -a
```

So before I do the UUID thing, I turn it off; when I'm done I turn it on?

---

### Post by WRDN on 2008-08-28
> **SammerHammer said:**
> So before I do the UUID thing, I turn it off; when I'm done I turn it on?

You shouldn't need to turn swap off when changing the UUID's in the fstab and resume files. However, it is good practice to. When you are resizing/ deleting swap partitions, you will have to turn them off though, and this must be done from a LiveCD.

To turn swap off on the LiveCD, just open the Terminal and type:

```
sudo swapoff -a
```

Alternatively, open GParted (System > Administration > GParted), right click on the swap partition, and click "swap off".

---

### Post by drs305 on 2008-08-28
As I mentioned to SammerHammer in a PM, if using gparted from the live cd there is an option, once the swap partition is selected, to go to Partition > Swapoff. The Swapoff option replaces the menu item where "Unmount" usually appears.

---


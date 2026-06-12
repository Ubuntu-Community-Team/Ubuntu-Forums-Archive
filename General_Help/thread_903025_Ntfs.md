---
title: "Ntfs"
date: 2008-08-27
forum: General Help
---

### Post by Prominence on 2008-08-27
I'm having an issue NTFS formatted things. Whenever I connect it, it says it cannot mount or something.

---

### Post by iaculallad on 2008-08-27
> **Prominence said:**
> I'm having an issue NTFS formatted things. Whenever I connect it, it says it cannot mount or something.

Try posting whatever displays when you issue the following commands below on your terminal:

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

---

### Post by Prominence on 2008-08-27
It says "Cannot mount volume" and "Invalid mount option when attempting to mount 'UDF Volume'" it does the same with my external hard drive, but a bit different.

---

### Post by Ng Oon-Ee on 2008-08-27
Please copy-paste ALL the output that you get in the terminal when you run those commands. Use Ctrl-Shift-C to copy what you have selected in the terminal.

---

### Post by Prominence on 2008-08-27
Yeah...umm...I'm lost, I'm not THAT much of an expert or anything lol.

---

### Post by evilnone on 2008-08-27
i had the same issue when i installed sabayon for the first time.  What I had to do was update HAL and it fixed all my issues... what version of ubuntu and HAL do you have?

---

### Post by Prominence on 2008-08-27
I'm not sure about HAL but I have 804.

---

### Post by evilnone on 2008-08-27
you can always open up synaptic and do a search for HAL and reinstall if necessary to try that... or 

```
sudo apt-get install hal
```

---

### Post by xravexheavenx on 2008-08-27
Try plugging it into a Windows machine and then back into your Ubuntu box.  Sometimes the drives can get locked up when trying to read NTFS.

---


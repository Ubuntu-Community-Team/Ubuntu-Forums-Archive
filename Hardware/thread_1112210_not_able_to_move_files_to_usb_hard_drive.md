---
title: "not able to move files to usb hard drive"
date: 2009-03-31
forum: Hardware
---

### Post by 1dawson on 2009-03-31
Hi

I got a MYBOOK 1Tb today. They were in fat32 and I formatted it to ext3. After having done this I cannot put files on this drive. As for trying to change read and write rights, I can't do this. Since it tells me I'm not the owner. ... What stupid thing am I doing wrong?

/Anders, Sweden

---

### Post by cariboo on 2009-03-31
You can change the permissions of the mount point to world read/writeable. Open an Applications-->Accessories-->Terminal and type:

```
sudo chmod -R 777 /media/MYBOOK
```

Change the mount point to where you mount your external drive.

Jim

---

### Post by 1dawson on 2009-03-31
Thanks!

One problem, though. After having formatted it to fat32 it changed its name to:"1000,2 GB-media". Inserting that name, the terminal tells me there is no such file or cataloge... How do I write that name? Is there an underscore or something?

/A

---

### Post by quini on 2009-03-31
Hi,

I'm also interested in being able to write on an Usb ext3 formatted HD from my normal user...

Changing the folder permissions or user by hand is only a temporary solution... it should be mounted r&w by the user by default.

Any idea on how to get that behaviour??

TIA  ;)

---

### Post by 1dawson on 2009-03-31
> **cariboo907 said:**
> You can change the permissions of the mount point to world read/writeable. Open an Applications-->Accessories-->Terminal and type:

```
sudo chmod -R 777 /media/MYBOOK
```

Change the mount point to where you mount your external drive.

Jim

You know, it worked. I just changed MYBOOK to DISK   Thanks ever so much, Jim!

---


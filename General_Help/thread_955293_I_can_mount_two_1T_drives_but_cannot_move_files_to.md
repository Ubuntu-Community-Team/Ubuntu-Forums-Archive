---
title: "I can mount two 1T drives but cannot move files to them"
date: 2008-10-22
forum: General Help
---

### Post by ragnarokeve on 2008-10-22
I have 2, 1 terrabyte drives (both are ext3. with only the lost and found file) on my computer i have played around and managed to mount them and explore them but i am unable to transfer any information from a usb external hard drive that I force mounted (NTFS)

---

### Post by northern lights on 2008-10-22
What distribution are you using?

Any quotable error messages?

Can you please run either 'mv' or 'cp' from a shell and post the output?
I.e. something along the lines of```
cp /media/terabytedrive/test.file /media/usb/
```

---

### Post by geirha on 2008-10-22
By default ext3 filesystems on harddrives will be owned by root, and only writable to root. Try ```
sudo chown $USER:$USER /media/mountpoint
``` to change the ownership to your user, and thus grant yourself write access.

---

### Post by ilrudie on 2008-10-22
+1 on the cause
I just put a folder in the drive that I own and can write to and then sym link it into my home.  That way if I ever need to put something on the drive some other user needs to own its just a new folder away.

---

### Post by scouser73 on 2008-10-22
> **ragnarokeve said:**
> I have 2, 1 terrabyte drives (both are ext3. with only the lost and found file) on my computer i have played around and managed to mount them and explore them but i am unable to transfer any information from a usb external hard drive that I force mounted (NTFS)

What you need to do is, open **Terminal**, type **gksudo nautilus**, the Root account will open up, then make your way to your drive, **right click**, click the **Permissions** tab, and from there you can alter permissions so you can read, write & delete on the drives.

---


---
title: "user priveledges"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by Richard Carlson on 2007-10-21
I've got 7.10 installed onto my primary hard drive. I have a secondary hard drive that will only allow root to read and write to it. I would like to allow all users to read and write to it. What files do I make the changes to and what if any specific commands need to be written (i.e. examples would be appreciated. ) I'd like to use this secondary drive to store a few thousand photo's onto it and use it as my primary photo work drive to do my file manipulation, stitching of photo's etc on it and free up my  primary drive for it's specific purpose of just running software.   Rich

---

### Post by ntetreau on 2007-10-21
Well, I'm not an expert here so if you feel unsure, wait for someone more knowledgeable to give a  hand. 

If you don't want to take risks, then the easiest is to create a folder on the drive which will be read/write by your user.

Let's say your drive is mounted under /media/disk2

```
sudo mkdir /media/disk2/photos-rw

sudo chown you:you /media/disk2/photos-rw
```

Replace "you" by your login username

---

### Post by ceecko on 2007-10-21
You can also simply change the permissions on the drive.

```

chmod +w /media/disk2 -R
```

This will recursively set write permission for all files.

---


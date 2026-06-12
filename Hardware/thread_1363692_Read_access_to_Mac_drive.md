---
title: "Read access to Mac drive?"
date: 2009-12-24
forum: Hardware
---

### Post by Fir3chi3f on 2009-12-24
I'm fairly unfamiliar with macs but a friend of mines just died and he wanted to me to try and see what I can do.

For now I'm just trying to pull his documents off of the hard drive. When I plug it into my desktop I can mount it and read files to a point. It says that I don't have permission to read anything in his Documents folder or any other within his user folder.

/Users/(his username)/Documents is the directory I'm trying to get to. Here is what I have tryed:

```
sudo chmod 777 -R /media/YOURMACDISKNAME
sudo chown YOURUSERNAME -R /media/YOURMACDISKNAME
sudo chgrp YOURUSERNAME -R /media/YOURMACDISKNAME
```

That I got from this thread with the same problem: [http://ubuntuforums.org/showthread.php?t=740531](http://ubuntuforums.org/showthread.php?t=740531)

Here is a picture off of that thread that demonstrates my exact problem: 
[http://static.panoramio.com/photos/original/8990692.jpg](http://static.panoramio.com/photos/original/8990692.jpg)

---

### Post by Dark_Stang on 2009-12-24
Why not just do a "sudo nautilus" and pull them over with root permission?

---

### Post by Fir3chi3f on 2009-12-24
OMG!

Thank you Dark_Stang!

---


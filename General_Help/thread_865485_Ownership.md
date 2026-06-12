---
title: "Ownership"
date: 2008-07-20
forum: General Help
---

### Post by bobie on 2008-07-20
I have some folders on my XP hard drive that I want to be able to access and copy/move. But here's the problem

I can't move them because it says permission denied. When I try the command "sudo chown -hR barry /media/Sambo" it pauses for a bit and then tells me it can't find a couple of files or directories. I've been trying different things with no luck. Some help would be great. Also, when I open the properties for my XP HD the owner is listed as root so i can't edit permissions that way.

Thanks.

---

### Post by spiderbatdad on 2008-07-20
chown is used in the format: command option owner:group file. Where owner group might be root:root or user:host. For example if you are logged in as bob@bob and you wanted to chown (recursively) a directory:```
sudo chown -R bob:bob /barry/media/Sambo
```

The mount permissions of your external drive are set up in /etc/fstab. See this guide for a better understanding of fstab and mounting permissions:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---


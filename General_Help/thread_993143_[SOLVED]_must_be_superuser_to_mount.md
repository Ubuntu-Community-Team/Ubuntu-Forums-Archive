---
title: "[SOLVED] must be superuser to mount"
date: 2008-11-25
forum: General Help
---

### Post by jakupl on 2008-11-25
I did a stupid thing. I ran a program called banshee witch it supposed to make you ubuntu installation more secure. I mistakingly made so that only root can mount and umount. how can I reverse this?

---

### Post by jakupl on 2008-11-27
I have been trying to make a separate /home partition, and succeded yesterday, doing so, this problem dissapeared. Probably when I had to do a:
```
sudo chown -R jakup:jakup /home/jakup
```
[This is my thread where I asked for help doing a seperate /home.]("http://ubuntuforums.org/showthread.php?t=993343")

---


---
title: "Auto Mount box.net"
date: 2008-07-19
forum: General Help
---

### Post by herschen on 2008-07-19
I've used the instructions from this post to mount my box.net account as a drive in Linux: [http://ubuntuforums.org/showthread.php?t=202761]("http://ubuntuforums.org/showthread.php?t=202761")

Now I open the terminal and type:

```
sudo mount -t davfs http://www.box.net/dav /media/box.net
```

Then it prompts me for my username and password and mounts the drive.

How do I automate the username and password and place this command in fstab, so it will mount every time I boot? Can I do this just as easily for my Windows NTFS partition?

---


---
title: "Samsung Q1 mp3 mount point...?"
date: 2010-11-11
forum: Hardware
---

### Post by danielstrong52 on 2010-11-11
Hi forum,
I have recently been having a rather odd and frustrating experince with an mp3 player. The device in question is a Samsung Q1, and it works perfectly well through nautilus: I can just drop files into it from my laptop, no problem. However, for a variety of reasons I want to access the device in BASH, but I can't for the life of me figure out where the mount point is. It's not in /media; when I'm in the device in nautilus there is no option to go up in the file heirarchy. The only ways I can access it are through the "Computer" and the device icon that appears in the "places" sidepane. I was under the impression that a filesystem MUST be mounted somehow in order to access it. Any ideas where it could be or how I could find it? Is there something odd going on?

Thanks,
Dan

---

### Post by danielstrong52 on 2010-11-11
Hmmm. I have found it. It was mounted on ~/.gvfs/gphoto2 mount on usb%3A001,008

If anyone can still be bothered, enlightenment as to WHY it did this would be appreciated ;)

---


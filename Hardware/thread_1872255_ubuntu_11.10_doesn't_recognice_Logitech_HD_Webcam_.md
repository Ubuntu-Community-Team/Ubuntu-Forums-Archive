---
title: "ubuntu 11.10 doesn't recognice Logitech HD Webcam C270"
date: 2011-10-30
forum: Hardware
---

### Post by xavi fernandez on 2011-10-30
Hi, I just try plug my webcam and doesn't recognize it, I download cheese and when I tried open it, just close intermediately, any idea? I'm really new in ubuntu.

Thanks in advance!!!

---

### Post by stunrock on 2011-11-01
have the same problem

editing
$HOME/.pulse/daemon.conf

didnt work for me!

---

### Post by xavi fernandez on 2011-11-02
Yes, I found it :D with this command

ls  /dev/video*

The system recognize my webcam, now I can make it works with vlc media player, but no with cheese that doesn't work in my ubuntu 11.10, so, I will try find another software for the web cam.

---

### Post by stunrock on 2011-11-02
is the microphone working???

i can see it in the sound settings. its listed in devices.
But i can't choose it as a input device

:confused:

---

### Post by xavi fernandez on 2011-11-02
I'm not idea about the sound, just because I can not find a software for make the web cam work properly for try, cheese is not installing well in my ubuntu 11.10, the only think I have done with the camera is make it work with vlc media player, but I can not make it record any video, so, I can not try the sound :(

---


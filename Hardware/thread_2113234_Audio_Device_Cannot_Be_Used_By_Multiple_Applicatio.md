---
title: "Audio Device Cannot Be Used By Multiple Applications"
date: 2013-02-06
forum: Hardware
---

### Post by AntumDeluge on 2013-02-06
I am having a problem where my audio card becomes unusable by an application if it is already in use by another. For example: If I start up Audacity the sound works. But if I start up, say, Avidemux while Audacity is still running I get now sound through Avidemux. I am not sure when this started happening. It has been like this for at least a month. I have KDE and Lubuntu desktop installed and both suffer from the same problem. It's like the first application to get hold of the sound card locks it.

```
:~$ lspci | grep -i "audio"
00:04.0 Multimedia audio controller: NVIDIA Corporation CK804 AC'97 Audio Controller (rev a2)
```

I have tried changing settings with multiple mixers: alsamixer, gnome-alsamixer, xfce4-mixer but nothing has affected it.

---


---
title: "nvidia driver breaks X"
date: 2008-11-20
forum: Hardware
---

### Post by flyeng4 on 2008-11-20
I had dual monitors working great in Gutsy. I upgraded to Heron and X broke. I can't seem to get anywhere with hours of Googling. Right now I just want to be able to use the nvidia driver. I ran
```

sudo dpkg-reconfigure xserver-org

```
and now I have full resolution instead of the 800x600 safe mode. I have the restricted drivers installed for my video card which is a
```

william@william-laptop:~$ lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)

```

When I put 'Driver "nvidia"' in my xorg.conf, X will only boot to 800x600. Any suggestions on how to get X to use the proprietary nvidia driver?

So in essence, the attached xorg.conf works as long as I leave the driver line commented out in the device section. When I uncomment it, X breaks.

---


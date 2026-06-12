---
title: "screen"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by lawcab on 2006-01-14
Good Day,

I on on a IBM NetFinity 3000 machine that has a S3 Trio3D video card. I am not sure if it is installed in ubuntu. When ever i move my moue around there are line that appear on the left hand side. And I can not change my screen resolution. Is there a way to fix this?

Thanks

---

### Post by rjwood on 2006-01-14
make sure you have your info about your box.Then
```
sudo dpkg-reconfigure xserver-xorg
``` If you don't have your info then just go with the detected settings. When you are all done and are back at the command line, I recommend you reboot
```
sudo reboot
```

EDIT: for your video driver you may want to choose 'vesa'.

---

### Post by lawcab on 2006-01-14
Thank you for the tip. I will try that out.

---


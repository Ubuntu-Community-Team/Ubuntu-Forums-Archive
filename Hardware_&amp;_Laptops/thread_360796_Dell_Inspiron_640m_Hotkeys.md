---
title: "Dell Inspiron 640m Hotkeys"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by Ivan Wagner on 2007-02-13
Hi to everyone,

I own a 640m and I just  installed Ubuntu 6.10. I'm able to use the hotkeys like switch display, volume, disable/enable wireless/bluetooth, hibernate and stand by. The only hotkey that doesn't work is the display's luminosity (Fn + Up or Fn + Down).

Could you please help me out?

Cheers.

---

### Post by nachotronics on 2007-02-18
You should try the following, it worked for me  ;) 

1. open and edit the file /etc/modprobe.d/blacklist
```
sudo gedit /etc/modprobe.d/blacklist
```

2. Append "blacklist video" at the end of the file.

3.Reboot

---

### Post by Pcniatic on 2007-04-17
It work for me, Thanks :D
You can also try it without rebooting, but it will not stay for the next boot :
```
sudo modprobe -r video
```

---


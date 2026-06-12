---
title: "USB camera not recognized - how to reset?"
date: 2011-01-12
forum: Hardware
---

### Post by rozo on 2011-01-12
Hi all,

I have an USB camera that is not recognized in about 1 of 3 times by my Ubuntu 10.04 when I start the PC. It is always recognized if I remove it and put back, so I thought I might somehow reset the USB bus after the PC starts. I went through many usb and ubuntu forums and only learned that I can not do it :( But I think it MUST be somehow possible! Anyone has an idea?
I use an embedded PC that has to work 100% that is why solutions like restarting it or removing and putting the camera back are no real solutions for me.

---

### Post by Fafler on 2011-01-12
I don't think it's possible to reset the USB bus, but try this instead:

Use lsmod to figure out what driver it uses. Now,
```
sudo chmod +x /etc/rc.local
sudo nano /etc/rc.local
```

Just before the before the last line, which should be exit 0, add

```
rmmod [drivername]
modprobe [drivername]
```

---


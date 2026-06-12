---
title: "Webcam doesn't work in Ubuntu"
date: 2009-12-27
forum: Hardware
---

### Post by rva1945 on 2009-12-27
Genius KYE usb webcam. Of course it works fine in Windows XP.

robert@rvasystem:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 002 Device 002: ID 093a:2624 Pixart Imaging, Inc. WebCam**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
robert@rvasystem:~$ 

Do I have to mount or something like that (I'm new to Linux).

Thanks

---

### Post by taurus on 2009-12-27
Have you installed cheese (it's in the repos) and see if it turns on your webcam when you run it (Applications -> Sound & Video)?

---

### Post by rva1945 on 2009-12-27
> **taurus said:**
> Have you installed cheese (it's in the repos) and see if it turns on your webcam when you run it (Applications -> Sound & Video)?

Cheese? Please tell me exactly how to find it (new to Linux sorry).

Thanks

---

### Post by llawwehttam on 2009-12-27
Go to Applications>Accessories>terminal

then type

```
sudo apt-get install cheese
```and enter your password when prompted.

Also you might want a newly installed guide.

[http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html](http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html)
that is the best one I know.

---


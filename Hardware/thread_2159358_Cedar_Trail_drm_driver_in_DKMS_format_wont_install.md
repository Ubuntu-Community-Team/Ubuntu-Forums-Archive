---
title: "Cedar Trail drm driver in DKMS format wont install!"
date: 2013-07-02
forum: Hardware
---

### Post by justinh119 on 2013-07-02
I have a Gateway LT4008u and I installed ubuntu so I can run XBMC. But my screen brightness and resolution is not right and I cant install the driver. I have the log file 

[http://pastebin.com/bxV6bTUZ](http://pastebin.com/bxV6bTUZ)

---

### Post by Yellow Pasque on 2013-07-03
[https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584](https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584)

---

### Post by justinh119 on 2013-07-04
Thanks for the reply. If I downgrade ubuntu will the driver then install?

---

### Post by Yellow Pasque on 2013-07-04
Yeah, you have to do a fresh install of Precise/12.04.  It will probably be easier if you use Ubuntu 12.04.1, because that still has the original 3.2 kernel and Xserver 1.11.x: [http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)
After you have it installed, make sure you don't install any non-3.2 kernels.

---

### Post by justinh119 on 2013-07-04
Ok thanks for your help, I thought it was a lost cause. I'm downloading Ubuntu 12.04.1 LTS now. I will update after I'm done installing it.

---

### Post by justinh119 on 2013-07-04
The downgrade to 12.04.1 did not work and it still shows the same error when I try to install the driver. Im going to downgrade further to 11.04.

---

### Post by justinh119 on 2013-07-04
I ran into a lot of problems with 11.04

---

### Post by justinh119 on 2013-07-04
I am now able to install the drivers!!!! I did a complete format of my hard drive (erased windows 7) and did as you said put a fresh install of Ubuntu 12.04.1.

---


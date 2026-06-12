---
title: "PC won't start nVidia X server after update"
date: 2012-01-26
forum: Hardware
---

### Post by Norwegiandude on 2012-01-26
Okey, so I did a normal update on the system yesterday (Updating linux headers and others which required a restart, 10.04.3 LTS) and when i rebooted it would not start the nVidia X server. The first error I get is this:

```
(EE) Failed to load module 'nvidia' (module does not exist, 0)
(EE) No drivers available.
```I get 5 options after this: restart X, troubleshoot, Use Ubuntu with simple graphics, change graphic settings, etc. but none of them seem to work.

The error i get after troubleshooting is this:

```
Fatal server error:
Server is already active for display 0
if this server is no longer running, remove /tmp/.X0-lock and start again
```I have removed the xorg.conf-files as root and tried this link:

[http://typethinker.blogspot.com/2010/02/ubuntu-fails-to-load-nvidia-kernel.html](http://typethinker.blogspot.com/2010/02/ubuntu-fails-to-load-nvidia-kernel.html)

but without any luck. I still get the error at startup. Any ideas how to solve this problem? :)

---

### Post by Norwegiandude on 2012-01-26
Nevermind, I reinstalled the newest nvidia driver from nvidia.com using this guide:

[http://eddieringle.com/how-to-install-official-nvidia-drivers-in-linux/](http://eddieringle.com/how-to-install-official-nvidia-drivers-in-linux/)

And presto! It worked :) Just press yes to every question the install wizard asks you (Make new X file etc.)

---


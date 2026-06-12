---
title: "Integrated webcam stopped turning on"
date: 2020-09-02
forum: Hardware
---

### Post by Minilek on 2020-09-02
I have a Lenovo Thinkpad X1 Yoga, 3rd gen, which has a built-in webcam. Up until today the webcam worked, but all of a sudden it stopped*. The only thing I can think of that changed is that I did an apt upgrade yesterday and have rebooted since then. apt upgrade upgraded the following packages:

libpam0g:amd64 (1.1.8-3.6ubuntu2.18.04.1, 1.1.8-3.6ubuntu2.18.04.2)
linux-libc-dev:amd64 (4.15.0-112.113, 4.15.0-115.116)
libpam-modules:amd64 (1.1.8-3.6ubuntu2.18.04.1, 1.1.8-3.6ubuntu2.18.04.2)
grub-common:amd64 (2.02-2ubuntu8.17, 2.02-2ubuntu8.18)
libsnmp-base:amd64 (5.7.3+dfsg-1.8ubuntu3.5, 5.7.3+dfsg-1.8ubuntu3.6)
google-chrome-stable:amd64 (84.0.4147.135-1, 85.0.4183.83-1)
libwinpr2-2:amd64 (2.1.1+dfsg1-0ubuntu0.18.04.1, 2.2.0+dfsg1-0ubuntu0.18.04.1)
grub2-common:amd64 (2.02-2ubuntu8.17, 2.02-2ubuntu8.18)
libpam-runtime:amd64 (1.1.8-3.6ubuntu2.18.04.1, 1.1.8-3.6ubuntu2.18.04.2)
grub-pc:amd64 (2.02-2ubuntu8.17, 2.02-2ubuntu8.18)
grub-pc-bin:amd64 (2.02-2ubuntu8.17, 2.02-2ubuntu8.18)
apport:amd64 (2.20.9-0ubuntu7.16, 2.20.9-0ubuntu7.17)
libsnmp30:amd64 (5.7.3+dfsg-1.8ubuntu3.5, 5.7.3+dfsg-1.8ubuntu3.6)
libfreerdp2-2:amd64 (2.1.1+dfsg1-0ubuntu0.18.04.1, 2.2.0+dfsg1-0ubuntu0.18.04.1)
grub-efi-amd64-bin:amd64 (2.02-2ubuntu8.17, 2.02-2ubuntu8.18)
python3-apport:amd64 (2.20.9-0ubuntu7.16, 2.20.9-0ubuntu7.17)
libpam-modules-bin:amd64 (1.1.8-3.6ubuntu2.18.04.1, 1.1.8-3.6ubuntu2.18.04.2)
apport-gtk:amd64 (2.20.9-0ubuntu7.16, 2.20.9-0ubuntu7.17)
grub-efi-amd64-signed:amd64 (1.93.19+2.02-2ubuntu8.17, 1.93.20+2.02-2ubuntu8.18)
python3-problem-report:amd64 (2.20.9-0ubuntu7.16, 2.20.9-0ubuntu7.17)
libfreerdp-client2-2:amd64 (2.1.1+dfsg1-0ubuntu0.18.04.1, 2.2.0+dfsg1-0ubuntu0.18.04.1)

(copied from /var/log/apt/history.log). Anything here alarming bells for anyone? I'm using Ubuntu 18.04 LTS Bionic Beaver.

* By "stopped" working, I mean the camera never turns on. A green light used to come on whenever the camera was in use, but that doesn't happen anymore. Now when a program wants to use the camera, I just get a totally black screen, e.g. from cheese, guvcview, or Zoom.

---

### Post by Minilek on 2020-09-02
OK, I figured it out. My laptop actually has a little switch at its top edge above the camera, and somehow that got flicked to the right. Flicked it left and it works again. Never noticed it before today!

---


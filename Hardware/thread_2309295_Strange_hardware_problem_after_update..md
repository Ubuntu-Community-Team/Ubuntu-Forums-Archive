---
title: "Strange hardware problem after update."
date: 2016-01-09
forum: Hardware
---

### Post by wddepooter on 2016-01-09
Hé guys/galls,

I had a strange error occuring in the last few days.

I have a HP Elitebook 2560, replaced the standard HD with an SSD
After I did my weekly update i rebooted my laptop and the puppy had multi-organ failure..
No WIFI, screen looked funny, no USB connection possible, wired ethernet still worked.
After testing and trying nothing worked so I thought my, second hand, laptop had died.

Just for fun i tried:
apt-get dist-upgrade
..... problem solved. everything works again...
I ran tail -n25 /var/log/apt/history.log
And this came up:

wddepooter@seamus:~$ tail -n25 /var/log/apt/history.log
Start-Date: 2016-01-08  17:42:46
Commandline: apt-get upgrade
Upgrade: libavresample-ffmpeg2:amd64 (2.7.3-0ubuntu0.15.10.1, 2.7.4-0ubuntu0.15.10.1), libavformat-ffmpeg56:amd64 (2.7.3-0ubuntu0.15.10.1, 2.7.4-0ubuntu0.15.10.1), python-samba:amd64 (4.1.17+dfsg-4ubuntu3, 4.1.17+dfsg-4ubuntu3.1), libswresample-ffmpeg1:amd64 (2.7.3-0ubuntu0.15.10.1, 2.7.4-0ubuntu0.15.10.1), aptitude-doc-en:amd64 (0.7.3-1ubuntu1, 0.7.3-1ubuntu1.1), libpng12-0:amd64 (1.2.51-0ubuntu3.15.10.1, 1.2.51-0ubuntu3.15.10.2), grub-common:amd64 (2.02~beta2-29ubuntu0.2, 2.02~beta2-29ubuntu0.3), libnss3-1d:amd64 (3.19.2.1-0ubuntu0.15.10.1, 3.19.2.1-0ubuntu0.15.10.2), grub2-common:amd64 (2.02~beta2-29ubuntu0.2, 2.02~beta2-29ubuntu0.3), libnss3-nssdb:amd64 (3.19.2.1-0ubuntu0.15.10.1, 3.19.2.1-0ubuntu0.15.10.2), samba-common-bin:amd64 (4.1.17+dfsg-4ubuntu3, 4.1.17+dfsg-4ubuntu3.1), libldb1:amd64 (1.1.20-2, 1.1.20-2ubuntu0.1), libpostproc-ffmpeg53:amd64 (2.7.3-0ubuntu0.15.10.1, 2.7.4-0ubuntu0.15.10.1), linux-image-4.2.0-23-generic:amd64 (4.2.0-23.28, 4.2.0-23.28), libswscale-ffmpeg3:amd64 (2.7.3-0ubuntu0.15.10.1, 2.7.4-0ubuntu0.15.10.1), samba-libs:amd64 (4.1.17+dfsg-4ubuntu3, 4.1.17+dfsg-4ubuntu3.1), libpng12-dev:amd64 (1.2.51-0ubuntu3.15.10.1, 1.2.51-0ubuntu3.15.10.2), aptitude-common:amd64 (0.7.3-1ubuntu1, 0.7.3-1ubuntu1.1), libnss3:amd64 (3.19.2.1-0ubuntu0.15.10.1, 3.19.2.1-0ubuntu0.15.10.2), grub-pc-bin:amd64 (2.02~beta2-29ubuntu0.2, 2.02~beta2-29ubuntu0.3), grub-pc:amd64 (2.02~beta2-29ubuntu0.2, 2.02~beta2-29ubuntu0.3), aptitude:amd64 (0.7.3-1ubuntu1, 0.7.3-1ubuntu1.1), libavcodec-extra:amd64 (2.7.3-0ubuntu0.15.10.1, 2.7.4-0ubuntu0.15.10.1), libavutil-ffmpeg54:amd64 (2.7.3-0ubuntu0.15.10.1, 2.7.4-0ubuntu0.15.10.1), linux-libc-dev:amd64 (4.2.0-22.27, 4.2.0-23.28), python-ldb:amd64 (1.1.20-2, 1.1.20-2ubuntu0.1), samba-common:amd64 (4.1.17+dfsg-4ubuntu3, 4.1.17+dfsg-4ubuntu3.1), libavcodec-ffmpeg-extra56:amd64 (2.7.3-0ubuntu0.15.10.1, 2.7.4-0ubuntu0.15.10.1), libsmbclient:amd64 (4.1.17+dfsg-4ubuntu3, 4.1.17+dfsg-4ubuntu3.1)
End-Date: 2016-01-08  17:43:09

Start-Date: 2016-01-08  17:44:37
Commandline: apt-get install dkms
Install: dkms:amd64 (2.2.0.3-2ubuntu6.1)
End-Date: 2016-01-08  17:44:38

Start-Date: 2016-01-08  17:45:14
Commandline: apt-get autoremove
Remove: linux-image-extra-4.2.0-19-generic:amd64 (4.2.0-19.23), linux-image-4.2.0-19-generic:amd64 (4.2.0-19.23)
End-Date: 2016-01-08  17:45:20

Start-Date: 2016-01-09  13:51:46
Commandline: apt-get upgrade
Upgrade: firefox:amd64 (43.0+build1-0ubuntu0.15.10.1, 43.0.4+build3-0ubuntu0.15.10.1)
End-Date: 2016-01-09  13:51:51

Start-Date: 2016-01-09  14:12:03
Commandline: apt-get dist-upgrade
Install: linux-headers-4.2.0-23-generic:amd64 (4.2.0-23.28, automatic), linux-image-extra-4.2.0-23-generic:amd64 (4.2.0-23.28, automatic), linux-headers-4.2.0-23:amd64 (4.2.0-23.28, automatic)
Upgrade: linux-headers-generic:amd64 (4.2.0.22.24, 4.2.0.23.25), linux-image-generic:amd64 (4.2.0.22.24, 4.2.0.23.25), linux-generic:amd64 (4.2.0.22.24, 4.2.0.23.25)
End-Date: 2016-01-09  14:12:43

Anybody any ideas what went wrong after the first update? Maybe a hardware controller wasn't properly adressed?

Kind regards,
FAbian

---

### Post by wddepooter on 2016-01-09
just a quick update:

If I run apt-get upgrade: problems
If I run apt-get dist-ugrade: bye bye problems

---


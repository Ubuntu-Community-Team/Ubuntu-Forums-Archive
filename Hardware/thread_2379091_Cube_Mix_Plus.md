---
title: "Cube Mix Plus"
date: 2017-11-30
forum: Hardware
---

### Post by moipersoin2 on 2017-11-30
Purchased a 10" cube mix plus with keyboard and Wacom stylus.
This is a Chinese convertible laptop / tablet with intel Kaby Lake hardware.
Performance with Linux is very good.
Ubuntu 17.10 supports all hardware by default and I am very impressed with how this thing performs with Ubuntu , so far so good...
The following is a list of issues I am having:

1: Wacom hardware works, but stylus is not recognised in the Ubuntu settings panel.
2: Auto rotate screen works, but is 180%  (ie: screen ends up upside down in portrait mode)
3: Do not know how to disable touch screen when stylus is in proximity to screen (when sketching I want the touch screen to ignore inputs from everything but the stylus)

I purchased two of these tablet/laptops (One for me, one for my daughter). My daughters will remain on Windows 10, this is a requirement for her school work.
I on the other hand want Linux running on mine. And it is, apart from the above issues.

Any help is much appreciated.

---

### Post by virgosun on 2017-12-04
[Here you are]("https://www.youtube.com/watch?v=GaX797u1MpI&lc=z22ivzdjtonnxryba04t1aokglivvbxxfidckovaj01mbk0h00410")

> **moipersoin2 said:**
> 
Ubuntu 17.10 supports all hardware by default and I am very impressed with how this thing performs with Ubuntu , so far so good...

Does 2 OmniVison camera work? How?
> **moipersoin2 said:**
> 
1: Wacom hardware works, but stylus is not recognised in the Ubuntu settings panel.

I have good news for you.
See attachment
> **moipersoin2 said:**
> 
2: Auto rotate screen works, but is 180%  (ie: screen ends up upside down in portrait mode)

_*Update solved on*_
I am  on 17.04 with systemd 234 
```

uname -a
Linux Wacom-m3-7y30 4.14.3-041403-generic #201711300431 SMP Thu Nov 30 09:32:55 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
virgosun@Wacom-m3-7y30:~$ sudo apt-cache policy systemd
[sudo] password for virgosun: 
systemd:
  Installed: 234-2ubuntu12
  Candidate: 234-2ubuntu12
  Version table:
 *** 234-2ubuntu12 100
        100 /var/lib/dpkg/status
     232-21ubuntu7.1 500
        500 http://security.ubuntu.com/ubuntu zesty-security/main amd64 Packages
     232-21ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu zesty/main amd64 Packages

```
> **moipersoin2 said:**
> 
3: Do not know how to disable touch screen when stylus is in proximity to screen (when sketching I want the touch screen to ignore inputs from everything but the stylus)
Any help is much appreciated.
It is possible, share you driver for Webcam, I'll share mine
Regards

---


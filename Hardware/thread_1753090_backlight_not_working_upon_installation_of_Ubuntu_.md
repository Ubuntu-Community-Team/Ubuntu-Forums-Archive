---
title: "backlight not working upon installation of Ubuntu 11.04"
date: 2011-05-08
forum: Hardware
---

### Post by ryangrannell1 on 2011-05-08
Hello everyone. Very sorry if this post is in the wrong subsection, or if I am being overly vague.

I installed Ubuntu (download) alongside windows 7, and after I get past the purple boot screen the back light on my laptop screen turns off. I am a complete novice, having never used Ubuntu before.

Any advice on how to fix the backlight issue?

---

### Post by mörgæs on 2011-05-08
Hi, welcome to the fora.

If you are not experienced with Ubuntu, I would recommend that you stick to 10.10 for a couple of months more. The backlight error is reported and a fix is in progress.

---

### Post by ryangrannell1 on 2011-05-08
> **mörgæs said:**
> Hi, welcome to the fora.

If you are not experienced with Ubuntu, I would recommend that you stick to 10.10 for a couple of months more. The backlight error is reported and a fix is in progress.

Thanks for the reply. That does bring up a further question though; where can I download Ubuntu 10.10, and can I get it to override 11.04? Thanks :)

---

### Post by mörgæs on 2011-05-09
It is here:
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

You just delete the 11.04 partitions and install 10.10 in stead.

---

### Post by emutier on 2011-05-11
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773740]("https://bugs.launchpad.net/null/+bug/779166")

wait until ubuntu is booted and then blindly to the following

press ctr+alt+F2 to start console
enter your loginname, press enter
enter your password press enter
enter "sudo setpci -s 00:02.0 F4.B=0"
press enter
enter password again, press enter
press ctr+alt+F7 to exit console

---


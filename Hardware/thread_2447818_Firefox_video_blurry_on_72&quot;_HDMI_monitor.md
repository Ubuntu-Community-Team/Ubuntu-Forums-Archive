---
title: "Firefox video blurry on 72&quot; HDMI monitor"
date: 2020-07-26
forum: Hardware
---

### Post by gdesilva on 2020-07-26
Hi,

I set up Ubuntu Studio 20.04 on my old Pentium 5 with nVidia GT 710 1GB gpu, 120GB SSD and an 72" hdmi monitor.

I suspect the native resolution supported by the monitor (a few years old now) is 1360x768 but on my display settings I have the option to set 1920x1080 as well. The highest resolution listed in vbeinfo is 1360x768.

I can set the resolution to 1920x1080 and play and/or stream videos on vlc without any issues. I even tested a 4K HD test clip on available on Youtube and it streams on vlc without a hitch.

However, if I plays the same clip on full screen on Firefox the images are blurry and stuttered - very low quality. In fact, all Youtube video clips suffer the same problem.

I reduced the display resolution to 1360x768 but the problem is still there whereas vlc does not suffer from this issue.

I tried using play on vlc plugins on Firefox which does give a slightly better picture. 

I would appreciate if anyone can provide any comments/suggestions on this.

Thanks in advance.

---

### Post by CatKiller on 2020-07-27
> **gdesilva said:**
> However, if I plays the same clip on full screen on Firefox the images are blurry and stuttered - very low quality. In fact, all Youtube video clips suffer the same problem.
I believe Firefox is still missing hardware accelerated video decoding on Linux. There are builds of Chromium that have it, but I don't know if the default Ubuntu one does yet.

---

### Post by gdesilva on 2020-07-27
@CatKiller, thanks for the info. How can I check whether Chromium build on Ubuntu repos have hw decoding built in or not?

---

### Post by CelticWarrior on 2020-07-29
You can use a PPA for that: [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev)

Everything you need to know and do after installing is also explained there.

---

### Post by gdesilva on 2020-07-30
@Celticwarrior, thanks very much for the link.

I installed Brave browser and now I can get a very good quality image on the screen without having to do any tweaks. I downloaded the official version of Brave so it is quite possible that FF official version may also do the same trick but did not have time to test it out as I am snowed under with other commitments at the moment. It is a work around but will have to live with it for the time being. 

Thanks to both of you for the responses.

---


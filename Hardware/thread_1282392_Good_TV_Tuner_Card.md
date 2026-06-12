---
title: "Good TV Tuner Card?"
date: 2009-10-04
forum: Hardware
---

### Post by coldReactive on 2009-10-04
Do TV Tuner Cards actually work on X/Ubuntu? If so, can someone suggest a good one that accepts Digital TV Signals (ATSC), but won't hurt my wallet? (IE: It can't be more than 65 USD).

I already have a nVidia 1 GB GTS 250 graphics card, so I don't need or want one that is integrated into a graphics card.

---

### Post by howefield on 2009-10-04
I generally have success with Hauppage cards, currently using a usb Nova-T which should be just about inside your budget, and previously used a pci 1100.

[http://www.linuxtv.org/wiki/index.php/Hauppauge](http://www.linuxtv.org/wiki/index.php/Hauppauge)
[http://www.hauppauge.com/Pages/faq/support_faq_linux.html](http://www.hauppauge.com/Pages/faq/support_faq_linux.html)

---

### Post by coldReactive on 2009-10-04
> **howefield said:**
> I generally have success with Hauppage cards, currently using a usb Nova-T which should be just about inside your budget, and previously used a pci 1100.

[http://www.linuxtv.org/wiki/index.php/Hauppauge](http://www.linuxtv.org/wiki/index.php/Hauppauge)
[http://www.hauppauge.com/Pages/faq/support_faq_linux.html](http://www.hauppauge.com/Pages/faq/support_faq_linux.html)

Tried to make v4l-dvb, and guess what, I can't use the tuner now. Have any help on installing it for Ubuntu specifically? xawtv says v4l doesn't exist. Though, I'd rather be able to watch TV in totem.

it's a WinTV-HVR 850 (aka: 950)

Otherwise, I'll have to take it back.

---

### Post by coldReactive on 2009-10-04
Please help...

---

### Post by coldReactive on 2009-10-04
So, I found out dmesg is much more helpful than I thought. For those of you having the same issue as me... download the following file, and copy it (as root) into /lib/firmware and any generic image folders you may have.

w_scan finally picks up channels now.

---

### Post by coldReactive on 2009-10-06
Seems I get a lot of jitter all of a sudden, and the tvtime post-proc in gxine won't work at all.

Also, totem quits whenever I lose TV signal, so I'm forced to use gxine. TVTime itself only gets Analog signals.

---

### Post by Rhubarb on 2009-10-06
Give me-tv a try, it's a nice app for watching tv.
[https://launchpad.net/me-tv](https://launchpad.net/me-tv)

---

### Post by coldReactive on 2009-10-06
> **Rhubarb said:**
> Give me-tv a try, it's a nice app for watching tv.
[https://launchpad.net/me-tv](https://launchpad.net/me-tv)

I need an amd64 deb, and cannot make, I don't have a config.pl

---

### Post by howefield on 2009-10-06
[https://launchpad.net/ubuntu/jaunty/amd64/me-tv](https://launchpad.net/ubuntu/jaunty/amd64/me-tv)

[https://launchpad.net/ubuntu/karmic/amd64/me-tv](https://launchpad.net/ubuntu/karmic/amd64/me-tv)

---

### Post by coldReactive on 2009-10-06
> **howefield said:**
> [https://launchpad.net/ubuntu/jaunty/amd64/me-tv](https://launchpad.net/ubuntu/jaunty/amd64/me-tv)

[https://launchpad.net/ubuntu/karmic/amd64/me-tv](https://launchpad.net/ubuntu/karmic/amd64/me-tv)

I'd rather have 1.0.0 in jaunty though. :|

[s]Also, after installing Me TV from the repo in jaunty, gxine can no longer get DVB.[/s]

Seems Me TV Closes to tray. Also, Me TV gets the wrong program information.

---


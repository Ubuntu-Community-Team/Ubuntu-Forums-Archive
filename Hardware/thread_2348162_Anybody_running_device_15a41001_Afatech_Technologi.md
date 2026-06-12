---
title: "Anybody running device 15a4:1001 Afatech Technologies, Inc. AF9015/AF9035 DVB-T stick"
date: 2017-01-01
forum: Hardware
---

### Post by melsy on 2017-01-01
Hello, 

am a novice Ubuntu user and not that technical.  Before I migrate from Windows, I want to be able to watch terrestrial digital TV on my laptop.  Has anybody installed device 15a4:1001 Afatech Technologies, Inc. AF9015/AF9035 DVB-T stick successfully?  Is there an easy solution to run this device, i.e. a Ubuntu Software Centre Package?  If not, something less technical than this [https://gist.github.com/larsr/b3912c0ac21031ceaecb](https://gist.github.com/larsr/b3912c0ac21031ceaecb) 

Thanks

---

### Post by tea for one on 2017-01-01
> **melsy said:**
>  device 15a4:1001 Afatech Technologies, Inc. AF9015/AF9035 DVB-T stick 

This device appears on row five on the following link:-

[https://www.linuxtv.org/wiki/index.php/Afatech_AF9035](https://www.linuxtv.org/wiki/index.php/Afatech_AF9035)

I suspect that you may have to download the correct firmware and install it in /lib/firmware.

The firmware could be either dvb-usb-it9135-02.fw or dvb-usb-af9015.fw

I use an Aver TV Volar Black HD A850 USB DVB-T device which uses dvb-usb-af9015.fw and it functions fine.

TV viewing in Ubuntu can be a bit of a lottery but It looks like your device "should" be OK

Here is another web page with useful information:-

[https://ubuntu-mate.community/t/how-to-watch-digital-tv-with-kaffeine-or-me-tv-in-ubuntu/906](https://ubuntu-mate.community/t/how-to-watch-digital-tv-with-kaffeine-or-me-tv-in-ubuntu/906)

I notice that you are a new forum member and I would like to know if you have tried or installed Ubuntu?

Kind regards

---

### Post by melsy on 2017-01-02
Hi.  Thanks for the reply.  I have installed Ubuntu on a couple of machines to test, have not replaced my core machines as yet.  So I have to make changes through the terminal line, no other options?

---

### Post by tea for one on 2017-01-02
You have two PCs to use as test machines - splendid.

Have you installed ubuntu-restricted extras?

Have you decided the software package to use for TV?

There is no need to be concerned about using the terminal, it is a bonus for Ubuntu users.

Terminal use will help build confidence, slowly and gently increase knowledge and add a bit of fun to using computers.

Please turn on the PC and log in.

Insert your USB DVB device, open a terminal window and type

```
lsusb 
```

Please copy and paste the results inside code tags.

Good luck

---


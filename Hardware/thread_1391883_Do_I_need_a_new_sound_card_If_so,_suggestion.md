---
title: "Do I need a new sound card? If so, suggestion?"
date: 2010-01-27
forum: Hardware
---

### Post by Phases on 2010-01-27
OK, so I moved (fresh install) from 8.04 to 9.10 because it was getting pretty buggy and I was hoping it would fix some sound issues I was having due to some podcasts I do. 

Well, the sound is, if anything, worse. So. I'm wondering what I need to do. Am I just using bad drivers or should I get a card? 

When Ubuntu starts, the startup sound skips a bit. 8.04 Didn't do that.
When I record skype calls one of us is in right ear, one in left. If I change it to both coming out of both, it seems to sound worse when we both talk - but either way, when we both talk, it cuts one of us out rather than just mixing the two together. 

I have mix unchecked, but they still faintly hear whatever other sounds is playing besides the phone call. On 8.04 I could hit 'mix' and make it all mix in together and uncheck it and they'd hear nothing else.

I guess I'm not sure if I'm using pulse or alsa. Whatever is out of the box, but then I installed alsa-gui of some sort to get the mic working, though the GUI gives an error when I load it. 

SO. Any advice would be appreciated. I realize this is sorta vague so whatever you need to ask, ask.. I guess I'm hoping a simple "yeah go get a (cheap) card cuz yours sucks" might be the answer, though I'm certainly open to someone helping me figure out why it sucks - if it can be fixed.

Here is my mobo: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131540](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131540)

If I do, does anyone know of a inexpensive but good enough sound card that will be supported fine?

Thanks for any help.

---

### Post by Phases on 2010-01-27
[Edit, didn't do...]

---

### Post by Phases on 2010-01-27
No one?

---

### Post by AlexZaim on 2010-01-27
Have you done all the updates?
Sometimes abvious things matter most.

See if installing the latest pulseaudio driver from theyr official site fixes your problem.

my ver is
```
pulseaudio --version
pulseaudio 0.9.19

```
all works ,fine. Not perfect but ok.

---

### Post by Phases on 2010-01-27
Appreciate your reply! I just checked, I'm at version 0.9.19 too..

Do you (or anyone) know if this would be easy to set up:

[http://www.bestbuy.com/site/Rocketfish%26%23153%3B+-+5.1-Channel+PCI+Sound+Card/9180405.p?id=1218047304449&skuId=9180405](http://www.bestbuy.com/site/Rocketfish%26%23153%3B+-+5.1-Channel+PCI+Sound+Card/9180405.p?id=1218047304449&skuId=9180405)

I found [one thread]("http://ubuntuforums.org/showthread.php?t=1188673") on it, which someone was having trouble, but it's old. Someone else eventually posted and said they got it working but didn't explain how.

Edit: Ah but it looks like we're behind.. 

[http://pulseaudio.org/](http://pulseaudio.org/)

---

### Post by Phases on 2010-01-28
Ok, so yesterday I had bought the card linked above, but it didn't work at all, loud static only. 

I just upgraded pulseaudio to:

```
phases@phases78w1:~$ pulseaudio --version
pulseaudio 0.9.21

```

by following the first bit of [this]("http://ubuntuguide.net/make-sound-quality-better-in-ubuntu-9-10karmic-with-pulseaudio-equalizer").

and upgraded alsa to:
```

phases@phases78w1:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Jan 28 2010 for kernel 2.6.31-17-generic (SMP).
```

by following (after several failed tutorials.. this was great!) [this]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/").

I'm not at home but the wife said sound is working fine. Course, it was fine to her before so I'll have to test more later but - she did say on reboots it doesn't static/stutter before the default login sound now so.. it seems to have helped at least a little.

So hopefully it will fix it, or if not maybe the card I bought will work. If not I'll return it and SHOULD be able to use [this]("http://www.walmart.com/ip/Creative-X-Fi-PCI-Express-Sound-Blaster-Xtreme-Audio-Sound-Card-30SB104200000/10893673"), as [alsa's site says]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") it got support in 21, which I just updated past. (minus a couple advanced features)

/crosses fingers.

---


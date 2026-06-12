---
title: "How can i enable my RaLink wireless card?"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by kotick on 2006-08-24
Hi everyone, i have kubuntu 6.06 and wow, is amazing. But, with the wireless ethernet card, well, almost. Kubuntu does recognize my card, it uses the right module (rt2500), assign with ease the address and everything else (ra0) but when i try to activate it, the things go wrong. if i list the wireless cards, kubuntu shows the raLInk as DISABLED, and i've tried everything, but it didn't work. I have an Averatec 3715-EH1, with a RaLink Wireless ethernet card. Somebody, please, give me a hint!

---

### Post by freyes on 2006-08-25
hi
I got the same card working in my laptop, but i cannot make it work with the module (rt2500-source) that is available at the ubuntu repository, so I downloaded [this]("http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz") an worked fine, then I downloaded Rutilt to search/connecto to hotspots (first i tried with wifi-radar, but didn't work).
[IMG]http://static.flickr.com/95/224448308_892ed9160f.jpg[/IMG]
rutilt shot.

I made just two tricky configuration and was this one in /etc/network/interfaces
```

auto ra0

```

and
```

echo rt2500 >> /etc/modules

```

seeya.

---

### Post by videodrome on 2006-09-24
Ok. add the repository in this thread: [http://www.ubuntuforums.org/showthread.php?t=240669&highlight=rutilt](http://www.ubuntuforums.org/showthread.php?t=240669&highlight=rutilt)

I would also suggest then also installing the rutilt config package (this is a connection manager which replaces the gnome network manager), but for me the synaptic debian package was broken. It wouldn't accept passwords, rendering it absolutely useless, since you need to enter your password in order to scan for wireless networks to connect to.

So I went here [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/) and downloaded it and compiled it using the nopasswd flag, and after it installed it worked perfectly on a fully-updated Xubuntu distro using a Netopia RT2500 card.

---


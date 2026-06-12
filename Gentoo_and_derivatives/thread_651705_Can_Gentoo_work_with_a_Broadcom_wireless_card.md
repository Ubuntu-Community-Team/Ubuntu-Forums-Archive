---
title: "Can Gentoo work with a Broadcom wireless card?"
date: 2007-12-27
forum: Gentoo and derivatives
---

### Post by Pogeymanz on 2007-12-27
How difficult will it be for me to install Gentoo and then use either broadcom43xx-fwcutter or ndiswrapper to get my internet working?

I haven't used Gentoo at all yet. Should I print out an installation manual or anything? How hard is it to get it up and running?

---

### Post by SOULRiDER on 2007-12-27
Gentoo can be a biznitch. Gentoo takes time, remember you ahve to compile everything and you will end up reading lots of docs trying to find why your stuff isnt working/broke or wht it wont compile.

If you have the time i say go for it, it can be lots of fun to use gentoo, but id keep another distro installed just in case.

---

### Post by Bachstelze on 2007-12-28
Gentoo's documentation is top-notch. If you stick to it, you'll be just fine (though it *does* indeed take time).

For your wireless, you'll be just fine too. The firmware for bcm43xx is the same for every distro, so you can just copy iy from your Ubuntu id you already have it installed.

---

### Post by zipperback on 2007-12-28
> **EmosSuck777 said:**
> How difficult will it be for me to install Gentoo and then use either broadcom43xx-fwcutter or ndiswrapper to get my internet working?

I haven't used Gentoo at all yet. Should I print out an installation manual or anything? How hard is it to get it up and running?


In general if a distro is using the current updated versions of the required network card drivers and such, then it shouldn't be a problem getting it up and running.

You should be able to get it working.

- zipperback
:popcorn:

---

### Post by johnydoe666 on 2008-01-25
from my own experience with this card: it works like a charm with ndiswrappers and network manager, even with wpa_supplicant. the onyl thing not really working efficiently is aircrack :P

---

### Post by stephenbrazier on 2008-02-27
O.o im not liking your username "Emosuks?" :(

---

### Post by notwen on 2008-02-27
I've installed Gentoo a couple of times and as long as you have plenty of time and the Installation Guide printed out you will be fine.  If you've ever compiled anything in terminal, imagine compiling your whole OS, it will take lots of time.  I did my Gentoo test installs over a weekend when I had plenty of time to walk back and forth and check on it.  Other distros that allow you to custom build your OS that you may wish to consider are [Arch]("http://www.archlinux.org/") or [Foresight]("http://www.foresightlinux.com/").

---

### Post by Crooksey on 2008-02-27
Hasnt this card been supported by default by the gentoo LiveCD for around a year now, a simple emerge will get this working, when you are chrooted into the system just run

```

# emerge net-wireless/bcm43xx-fwcutter
```

Sorted, all ready to go.

---

### Post by ahappydeath on 2008-04-16
Never got the Broadcom card working with Gentoo on my powerbook, but you may have a different experience though.

---

### Post by trimeta on 2008-04-22
I had a Broadcom card working on my old Gentoo laptop; I think there's a built-in driver ever since the 2.6.22 kernel, but I definitely used bcm43xx-fwcutter and such.

---


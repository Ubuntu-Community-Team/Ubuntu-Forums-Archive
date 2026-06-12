---
title: "Can anyone explain an easy way to upgrade from amule 2.2.2 to 2.2.5.1?"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by OGpmpdog on 2009-06-24
Hi,

One negative thing about ubuntu: the software upgrades/installations are quite difficult for beginners.

GDebi package installer didnt work...cant add package in synaptic either.

It's been a real beyotch trying to upgrade to the latest amule...

The script commands are too advanced.

Can someone explain step-by-step, in newbie ubuntuese?

Also, do any repositories have to be added?

---

### Post by dsavi on 2009-06-25
I can't honestly say that a year ago, when I first discovered what Linux was, I was confused by upgrading/installing. On the contrary, I was amazed by the amount of software available to just download and install. Same thing happened to my brother. So I'm not sure that "the software upgrades/installations are quite difficult for beginners" is founded.

That aside, though, it looks like you're on Intrepid Ibex. My guess is that amule 2.2.2 was the current release when 8.10 was released, and that it's frozen at that release now. Looking in the Jaunty repository now, the latest version is 2.2.4-1ubuntu1. What I would recommend you do is update Ubuntu on your machine (By pressing ALT-F2 and typing in update-manager -c) and let it upgrade itself.

---

### Post by spcwingo on 2009-06-25
You could add this amule PPA:

[https://launchpad.net/~amule-releases/+archive/ppa]("https://launchpad.net/~amule-releases/+archive/ppa")

To do so, just copy/paste this in your text editor:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESa3PNgEEANrbVTC5xEo1TfsY/BqallpgWFuTJUYOXbaSR3AqjAMrXL+c0DvQ33BH8Oqy
qlLnQFlWDcCYJMiBfMFhSamCHC+E8bLUEmU61t0yQOLBOvBo4kjaqn7vXxwi3y7w0WMBdzZY
LLhFQ7BzGT/4biSZWypYJKIM3JoT8AFvZVIfUdxjABEBAAG0J0xhdW5jaHBhZCBQUEEgZm9y
IGFNdWxlIHN0YWJsZSByZWxlYXNlc4i2BBMBAgAgBQJJrc82AhsDBgsJCAcDAgQVAggDBBYC
AwECHgECF4AACgkQo82IeUssRZ6HfQQAxon7tEj6XoFI7hZv2P8DnNs6F3RvZC1FOzEaj06i
1oafmCdG7ZvTvedwpPMVCQD+Mb5rMTZ8xT4YZ/8cIB0WKd/3i3wLiOWU6mX9uaUPVchQUrOy
6Vga35+MKXnXhERvaIzHStH76FLkxs5Dru8jLAlBC+OAW2/howzQeXL7kRE=
=/rC7
-----END PGP PUBLIC KEY BLOCK-----
```

Save as amule.gpg to your home directory then press ALT+F2.  This will bring up a run prompt.  In it enter:

```
gksu gedit /etc/apt/sources.list
```

At the bottom of the file that opens enter:

```
deb http://ppa.launchpad.net/amule-releases/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/amule-releases/ppa/ubuntu intrepid main
```

Save and close.  Now open a terminal and enter:

```
sudo apt-key add ./amule.gpg && sudo apt-get update && sudo apt-get dist-upgrade
```

You should now have the updated amule...Enjoy!  ;)

---


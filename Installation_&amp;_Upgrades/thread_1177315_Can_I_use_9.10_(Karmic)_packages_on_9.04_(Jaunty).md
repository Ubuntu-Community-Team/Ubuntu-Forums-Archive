---
title: "Can I use 9.10 (Karmic) packages on 9.04 (Jaunty)?"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by finni on 2009-06-03
I've got a question - can I use 9.10 Karmic packages on 9.04 Jaunty? 

Especially I'd like to use Karmic's Alsa (0.20.XX) instead of jaunty's Alsa (0.18.XX) - is this possible? (I'd rather use Karmic's package than compile Alsa 0.20.XX from source.)

---

### Post by biasquez on 2009-06-03
try this ppa:


# ALSA 1.0.20
deb [http://ppa.launchpad.net/thefirstm/experimental/ubuntu](http://ppa.launchpad.net/thefirstm/experimental/ubuntu) jaunty main

---

### Post by ari5av on 2009-06-03
> **biasquez said:**
> try this ppa:


# ALSA 1.0.20
deb [http://ppa.launchpad.net/thefirstm/experimental/ubuntu](http://ppa.launchpad.net/thefirstm/experimental/ubuntu) jaunty main

I'm looking to do the exact same thing as the original poster, and followed this advice.  I got this error:
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EA7C5B9D44B7E65D
W: You may want to run apt-get update to correct these problems

...when I added it to /etc/apt/sources.list.  s/jaunty/karmic/ and I got the same error, even after sudo apt-get update two or three times.  Did I miss something?

---

### Post by finni on 2009-06-03
> **biasquez said:**
> try this ppa:


# ALSA 1.0.20
deb [http://ppa.launchpad.net/thefirstm/experimental/ubuntu](http://ppa.launchpad.net/thefirstm/experimental/ubuntu) jaunty main

I added Karmic repositories to custom repos and updated alsa-base and other related alsa packages to 0.20.XX and it seems to be working.. *knocks the wood* ;)

---

### Post by zika on 2009-06-03
It works great since 29.05. ... :) "*knocks the wood*" ... with 2.6.30-rc{7,8} but it doesn't complain with 2.6.28-{11,12} either.

---

### Post by biasquez on 2009-06-04
> **ari5av said:**
> I'm looking to do the exact same thing as the original poster, and followed this advice.  I got this error:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EA7C5B9D44B7E65D
W: You may want to run apt-get update to correct these problems

...when I added it to /etc/apt/sources.list.  s/jaunty/karmic/ and I got the same error, even after sudo apt-get update two or three times.  Did I miss something?

NO_PUBKEY EA7C5B9D44B7E65D -> it's normal, doesn't use s/jaunty/karmic/ and do dist-upgrade

---


---
title: "How to manually install a package?"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by bliffle on 2009-08-24
What I mean is: suppose I go to a website and download a tar file or compressed tar or somesuch, instead of installing with 'synaptic' or 'apt-get'? Or is there a way to manually put it in the normal system?

IIRC I've faced this before with some kind of special-purpose code that isn't in the normal update/upgrade repertoire, maybe something like VLC 1.0. This afternoon I'm going to help a friend with his ubuntu system and I suspect I'll run into the same thing because he's installing some kind of CCTV surveillance system, so I thought I'd better research this subject.

Probably, the info I need is in the docs someplace, so I'll go on over to docs after I post this.

TIA for any help or pointers, warnings, etc.

---

### Post by stlsaint on 2009-08-24
first make sure that the software is compatible fully with Linux kernel...than for a tar file you may have to compile some stuff using the "make/make install" cmd. It would be better if you could look for a .deb package to just double click and install...

---

### Post by starcraft.man on 2009-08-24
> **bliffle said:**
> What I mean is: suppose I go to a website and download a tar file or compressed tar or somesuch, instead of installing with 'synaptic' or 'apt-get'? Or is there a way to manually put it in the normal system?

IIRC I've faced this before with some kind of special-purpose code that isn't in the normal update/upgrade repertoire, maybe something like VLC 1.0. This afternoon I'm going to help a friend with his ubuntu system and I suspect I'll run into the same thing because he's installing some kind of CCTV surveillance system, so I thought I'd better research this subject.

Probably, the info I need is in the docs someplace, so I'll go on over to docs after I post this.

TIA for any help or pointers, warnings, etc.

[General installation, including from deb and source.]("http://www.psychocats.net/ubuntu/installingsoftware")
[Wiki page on compiling source.]("https://help.ubuntu.com/community/CompilingEasyHowTo")
[PPA for VLC 1.0]("http://tuxarena.blogspot.com/2009/07/how-to-install-vlc-10-from-ubuntu-ppa.html")

I'd like to note, compiling should be last resort. Preferably, repositores then deb then compiling. I think that answers question. Tar.gz files are almost exclusively source code that needs compiling by the way.

---


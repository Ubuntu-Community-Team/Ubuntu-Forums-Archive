---
title: "Wiki-DMA troubleshooting - Isn't this obsolete?"
date: 2005-12-19
forum: Hardware &amp; Laptops
---

### Post by daller on 2005-12-19
Hi There,

The troubleshooting-part of:

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

...isn't it obsolete?

1) I've never been forced to do anything of that in Breezy (and maybe Hoary too...) - And I've installed Kubuntu on many different pc's

2) Checking /etc/modules, it does not show any of the modules mentioned...

As an example, here's mine:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
nvidia

```

---

### Post by earobinson on 2005-12-19
many problems can be solved by turining on and off dma such as dvd burning and sometimes dvd playback

---

### Post by daller on 2005-12-21
That's not my question...

Is the troubleshooting-part useable for anything/anybody?

...editing /etc/modules, etc....

I'm writing a danish guide, so I'm interested in whether or not I should include this part...

And should it be removed on the wiki?

---

### Post by izm81 on 2005-12-27
I'm currently running Dapper, but with that in mind, here's my **/etc/modules**:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line.  Comments begin with
# a "#", and everything on the line after them are ignored.

psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp
sis-agp
nvidia
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq
amd74xx
ide-cd
ide-disk
ide-generic

```

My file has **ide-cd**, which is mentioned by the troubleshooting part of the DMA page.  I've never had to use the troubleshooting part, but I'd be hesitant to remove it.

---


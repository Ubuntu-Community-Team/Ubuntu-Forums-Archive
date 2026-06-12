---
title: "do we need drivers while using ubuntu?"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by ignitedintelligence on 2009-04-20
hi,

i´&#7743; using lenovo r61 laptop. i´ve installed ubuntu 8.10 in it. do we need drivers for playing audio files and other utilities like in winxp or can it be played without installing those?? kindly help. i&#7743; void of knowledge in that. thanks in advance.

---

### Post by upchucky on 2009-04-20
Drivers for the machine are auto detected on install, well most of them, due to legal stuff some things are not automatically set up, depending on the country of origin.

if you come across a file that will not open/play, google it, or ask here.

there are ways to make most anything work.

---

### Post by Therion on 2009-04-20
Drivers support hardware, like your printer. These come installed as part of the Linux-kernel and do not need to be installed separately.

What you need to listen to .mp3 and other multimedia files are CODECS.

Open a Terminal and then Copy and Paste in the following: ```
sudo apt-get install ubuntu-restricted-extras
```Press enter, input your password, answer the prompts and let it install.  This package will install the codecs you need for the most common multimedia file-types (.mp3, .avi etc.) as well support for Java and other things you'll need.

---


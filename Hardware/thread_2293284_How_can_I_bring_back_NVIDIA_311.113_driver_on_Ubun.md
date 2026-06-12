---
title: "How can I bring back NVIDIA 311.113 driver on Ubuntu 14.04?"
date: 2015-09-03
forum: Hardware
---

### Post by DizNeo on 2015-09-03
How can I bring back NVIDIA 311.113 driver on Ubuntu 14.04?  When I first tried Ubuntu 14.04 about 6 months ago, it has NVIDIA 311.113 driver?  I did some distro hoping and now I'm back to Ubuntu, NVIDIA 311.113 is no longer available. Instead, a newer version is available.  I have a mouse pointer problem with the newer version. Mouse disappear when brought at the top of my screen. I also experience this on Mint on the same laptop. But I didn't have this problem before with 311.113 driver version.  Is there a way to install NVIDIA 311.113 from Driver Manager instead of the newer driver version?  Thanks in advance.

---

### Post by howefield on 2015-09-04
You might be able to get the packages from searching [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by DizNeo on 2015-09-04
I tried searching for nvidia and got some packages including nvidia-304 and a newer package but nothing for nvidia-311 :(

---

### Post by Yellow Pasque on 2015-09-04
It's nvidia 3**3**1

---

### Post by efflandt on 2015-09-04
Which nvidia package do you have installed now? Install **synaptic** (if you do not have that), hit the curly **Reload** icon in that, then when if finishes rebuilding the search index put **nvidia** in Quick search. My 14.04 system shows that nvidia-331 or nvidia-331-updates is now version 340.76, but nvidia-319 or nvidia-319-updates is still version 331.113. But I have xorg-edgers ppa added for newer drivers, so I do not know if that influences what shows up for those versions.

---


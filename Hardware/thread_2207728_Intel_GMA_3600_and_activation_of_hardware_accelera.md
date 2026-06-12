---
title: "Intel GMA 3600 and activation of hardware acceleration."
date: 2014-02-24
forum: Hardware
---

### Post by misha-yudin19 on 2014-02-24
I have a netbook [COLOR=#FF0000]Acer Aspire One D270[/COLOR]. Hardware:[COLOR=#0000FF]Intel N2600[/COLOR] and [COLOR=#0000FF]Intel GMA 3600[/COLOR]. I installed lubuntu 13.10 on him. Graphics card immediately got gma500 driver. But the problem is: there isn't hardware GPU acceleration of 2D and 3D. How do I enable hardware acceleration of 2D (and 3D, if it possible)?

---

### Post by mikewhatever on 2014-03-07
You'll need to switch to 12.04 with the 3.2 non-pae kernel and the origial 1.11 xserver, then install the proprietary cedarview driver. Here is [the ISO]("http://old-releases.ubuntu.com/releases/12.04.1/ubuntu-12.04.1-desktop-i386.iso").  Unfortunately, that driver is only available for that particular configuration, which is a big improvement compared toIntel's "support" of Intel GMA 500 some years ago. The good news is - 12.04 was a very good release with support lasting till 2017.

PS: Note, Lubuntu 12.04 was not an LTS. Try Ubuntu or Xubuntu instead.

---


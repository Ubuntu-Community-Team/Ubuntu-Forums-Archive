---
title: "Recommendation For Sound Card"
date: 2010-10-23
forum: Hardware
---

### Post by tb75252 on 2010-10-23
My sound card (aka audio card) is not working with Linux.
Does anyone have a recommendation for a good sound card that is readily available in the USA?

A few things to keep in mind:
* Must be PCI and not PCIe;
* Must have front panel audio header;
* Must support 7.1 or at least 5.1 speaker configuration.

Thanks.

---

### Post by cascade9 on 2010-10-24
Asus Xonar DS or Xonar DG. The DS has better sound, but costs a bit more. They are the only soiund cards I know iof with a front panel connector (HD audio, no AC97 AFAIK, but I havent checked that). 

There was a way of hacking some creative sound card to use a front panel connetor, but its not fun. See here- 

[http://audigy2zshowto.blogspot.com/2005/05/warning-you-can-damage-or-destroy-your.html](http://audigy2zshowto.blogspot.com/2005/05/warning-you-can-damage-or-destroy-your.html)

---

### Post by EveryWhere on 2010-11-20
Is the Xonar DG supported by Ubuntu, presently? Thanks.

---

### Post by tb75252 on 2010-11-20
> **EveryWhere said:**
> Is the Xonar DG supported by Ubuntu, presently? Thanks.


According to this link:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus)
the Xonar DG appears to be working with Linux.

Whether every feature works just like with Windows might be a different story...  Maybe somebody else on this forum can answer that.

---

### Post by Yellow Pasque on 2011-03-10
I got my Xonar DG today and it won't work with stock maverick install. ALSA 1.0.24 is needed (see alsa upgrade script: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577) ). My initial impression is that it's a great card for upgrading from onboard audio for someone with high quality headphones (I use vintage Sony MDR-V6). It's not as good as my M-Audio Revolution card, but that was twice the price of the Xonar (thrice if mail-in rebate works out). I don't know about the digital out or surround, but if anyone's interested, post in this thread, and I'll play with it some more.

---

### Post by mantaor on 2011-10-10
Hi guys,

I know that this post is old and [solved] but I need to know if the frontal input for headphones (xonar DG) is working.
My frontal input works well under win7 but with ubuntu 11.04, alsamixer 1.0.24, it's mute. Could anyone post any feedback?

Thank a lot

---

### Post by nazaroo2 on 2012-01-31
> **Temüjin said:**
> I got my Xonar DG today and it won't work with stock maverick install. ALSA 1.0.24 is needed (see alsa upgrade script: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577) ). My initial impression is that it's a great card for upgrading from onboard audio for someone with high quality headphones (I use vintage Sony MDR-V6). It's not as good as my M-Audio Revolution card, but that was twice the price of the Xonar (thrice if mail-in rebate works out). I don't know about the digital out or surround, but if anyone's interested, post in this thread, and I'll play with it some more.

How did you get it to work? 
I have a xonar DG too, and can't get Ubuntu to see it there in the PCI slot.
Can you help?

---


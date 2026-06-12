---
title: "No HDMI audio"
date: 2010-09-15
forum: Hardware
---

### Post by applegrew on 2010-09-15
Hi,

It's been hours now, but still am unable to get HDMI audio to work. The video works fine though. **I have now beginning to doubt that I have a HDMI audio device.**

My motherboard is Desktop Board DG35EC ([http://www.intel.com/Products/Desktop/Motherboards/DG35EC/DG35EC-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/DG35EC/DG35EC-overview.htm))

I have Kubuntu 10.04.
Graphics Card: Nvidia Geforce 250GTS
Audio devices I can see by using lspci: Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

**Do I have a HDMI audio device?**

---

### Post by applegrew on 2010-09-15
Bump!

---

### Post by BobVila on 2010-09-16
> **applegrew said:**
> Hi,

It's been hours now, but still am unable to get HDMI audio to work. The video works fine though. **I have now beginning to doubt that I have a HDMI audio device.**

My motherboard is Desktop Board DG35EC ([http://www.intel.com/Products/Desktop/Motherboards/DG35EC/DG35EC-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/DG35EC/DG35EC-overview.htm))

I have Kubuntu 10.04.
Graphics Card: Nvidia Geforce 250GTS
Audio devices I can see by using lspci: Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

**Do I have a HDMI audio device?**

You DO have an HDMI audio device... have you connected the SPDIF loop cable from the motherboard to the video card?

ATI has everything built in, but I believe Nvidia requires a cable to be connected to the video card to output sound.

---

### Post by applegrew on 2010-09-17
> **BobVila said:**
> You DO have an HDMI audio device... have you connected the SPDIF loop cable from the motherboard to the video card?

ATI has everything built in, but I believe Nvidia requires a cable to be connected to the video card to output sound.
Oh! I didn't know that. And thanks a lot for confirming that I have HDMI audio.

Now I understand why my card has SPDIF-in. I guess now I will have to buy a SPDIF cable.

---

### Post by rlara333 on 2010-09-17
Hello, 
Have you tried using alsamixer to make sure you do not have any audio outputs muted. to use it open a terminal and type alsamixer. Hope this helps.

---

### Post by lidex on 2010-09-17
This may help:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

---

### Post by applegrew on 2010-09-18
Hi all,

Thanks for the reply. I really did play with the mixers, but as BobVila pointed out, I need to connect my card's spidf-in with my motherboard's spdif-out. I don't have that connector right. Will get that in a month and then will be able to test it.

---

### Post by BobVila on 2010-09-20
Don't mind me.

---

### Post by lkjoel on 2010-09-25
> **applegrew said:**
> Hi,

It's been hours now, but still am unable to get HDMI audio to work. The video works fine though. **I have now beginning to doubt that I have a HDMI audio device.**

My motherboard is Desktop Board DG35EC ([http://www.intel.com/Products/Desktop/Motherboards/DG35EC/DG35EC-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/DG35EC/DG35EC-overview.htm))

I have Kubuntu 10.04.
Graphics Card: Nvidia Geforce 250GTS
Audio devices I can see by using lspci: Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

**Do I have a HDMI audio device?**
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by applegrew on 2010-09-26
Well I will try these once I get the hdmi cable... :)

---


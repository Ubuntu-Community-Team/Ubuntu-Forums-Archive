---
title: "Installing an audio interface driver (Behringer and Ardour)"
date: 2018-11-13
forum: Hardware
---

### Post by pardeek on 2018-11-13
Hello! I am trying to install the driver for an audio interface (Behringer XENYX 1204USB) to run with a digital audio workstation (Ardour). I am hoping someone can tall me if it's possible, or what I am doing wrong. I am very new to linux.
Here is the driver zip file: [ATTACH]281623[/ATTACH]
I extracted the file, but I'm not sure what to do next. I can't open the setup.exe file. I found a forum post on the Behringer website that said that people do use this interface with linux, but it seems like maybe it's not supported? 
Any help is much appreciated. Thanks!

---

### Post by Autodave on 2018-11-13
Exactly what is this file supposed to do or give you?  I don't use Ardour, but I do use Audacity. While Audacity doesn't have a lot of the bells and whistles that Ardour has, I found out a long time ago that it just works!  And, without JACK.  I use it to record 18 channels via USB cable from an Allen & Heath mixer.

As far as the file you are trying to open: that is a Windows file and will not work on Linux unless you were to try and run it using WINE.

---

### Post by slickymaster on 2018-11-13
*Thread moved to **Hardware**.*

---

### Post by #&amp;thj^% on 2018-11-13
This device should be suported under linux>> "Module ALSA : snd_usb_audio".
I would check in :
```
alsamixer
```
make sure you pick the right device via "F6" and then make sure nothing is muted.

This page is in french but should be easily translated:
> Cards on the official website:

****Behringer 1204 USB [http://www.behringer.com/EN/Products/1204USB.aspx](http://www.behringer.com/EN/Products/1204USB.aspx). 
****Behringer X1204 USB [http://www.behringer.com/EN/Products/X1204USB.aspx](http://www.behringer.com/EN/Products/X1204USB.aspx). 

Connectivity: USB.
ALSA module: snd_usb_audio.
Sound chip used: Texas Instrument PCM2902. Specification sheet: [http://www.ti.com/lit/gpn/pcm2902](http://www.ti.com/lit/gpn/pcm2902).

Note: The information on this page applies to both models. The X1204 USB model has just one more effects processor than the 1024 USB model.
Source: [http://linuxmao.org/Behringer+Xenyx+1204+-+X1204+USB](http://linuxmao.org/Behringer+Xenyx+1204+-+X1204+USB)
And they claim:
> 
Product Highlights

    Built-In USB Audio Interface
    Easy-to-Use 1-Knob Compressors
    "British" Style 3-Band EQs
    Mac, Windows, and Linux Compatible


---


---
title: "About webcam of VAIO SZ on Ubuntu, can't work for Skype"
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by jutirain on 2007-10-07
Hi,

I've followed [this article]("http://lsb.blogdns.net/ry5u870/") and install r5u870 by download .deb file from [here.]("http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/")

It seems the driver is installed properly, since there is no error message when i dpkg it.
(Actually, how can I confirm the driver works fine?)

However, I still can't use my microphone on Skype...

Have any idea?

Thanks a lot!

---

### Post by bazzard on 2007-11-03
I have the same laptop and neither the built in webcam or mic work, nor the mic socket for your headset. Does anybody know how to get these working please?

There is a supposed solution for the webcam here, but it didn't work for me: [http://ubuntuforums.org/showthread.php?t=289836&highlight=vaio+sz+camera&page=6](http://ubuntuforums.org/showthread.php?t=289836&highlight=vaio+sz+camera&page=6)

---

### Post by jutirain on 2007-11-03
I am considering whether I should upgrade my distribution to 7.10.

Does 7.10 has the same webcam problem?

Also, anyone have used vaio vn-cx1? the skype gadget for vaio.
[http://blog.tmcnet.com/blog/tom-keating/gadgets/sony-vaio-vncx1b-mouse-and-skype-gadget.asp](http://blog.tmcnet.com/blog/tom-keating/gadgets/sony-vaio-vncx1b-mouse-and-skype-gadget.asp)

I am wondering if it can work on my laptop...

---

### Post by bazzard on 2007-11-04
I'm using 7.10 but still no joy. There's gotta be someone out there who can help us get our mics and webcams up and running.

---

### Post by bazzard on 2007-11-06
Is there anybody who can help us out? My parents are getting annoyed that I can't speak to them on Skype!

---

### Post by cow_racer on 2007-11-06
Does linux version of skype support video?  I couldn't find that feature.

---

### Post by bazzard on 2007-11-07
> **cow_racer said:**
> Does linux version of skype support video?  I couldn't find that feature.

Nope. Not currently, which is annoying. I think I'm going to install VirtualBox/VMWare to get some things working in WIndows until I resolve them under linux.

---

### Post by boom2k1 on 2007-11-08
try the latest beta version of skype 2.0. It now supports video (although I am still trying to get mine to work.)

---

### Post by bazzard on 2007-11-08
> **boom2k1 said:**
> try the latest beta version of skype 2.0. It now supports video (although I am still trying to get mine to work.)

FANTASTIC! webcam works perfectly in the beta version of skype! Thanks a lot!

---

### Post by bazzard on 2007-11-08
> **boom2k1 said:**
> try the latest beta version of skype 2.0. It now supports video (although I am still trying to get mine to work.)

FANTASTIC! webcam works perfectly in the beta version of skype! Thanks a lot!

Don't suppose any of you have got the built in mic and the line-in mic jack working have you?

---

### Post by jutirain on 2007-11-09
Great! I've also get my webcam work in the skype 2.0!

However, why can't I use it in the "Video" plugin of Facebook?
The light of webcam is on, and it seems correctly drived, however, what I record is only noises...

Besides, bazzard, why do you need extra mic?
Isn't the hole on the left of webcam a built-in mic?
But I can't get it to work, very odd...
Video input is correct in Skype but audio not work

Thanks a lot for the information, anyway :)

---

### Post by avilella on 2007-11-09
The webcam mic works for me when doing this on 7.10 (also 7.04):

[http://avilella.googlepages.com/vaiosz](http://avilella.googlepages.com/vaiosz)

    The gnome-volume-control has:

HDA Intel (Alsa Mixer)

Edit->preferences->mark [v] Capture

then
           Master (max) -- PCM (almost max) -- Capture (everything switched on almost max) -- Switches (Microphone - on -- Line-on - off)

Cheers,

    Albert.

---

### Post by jutirain on 2007-11-11
In my case, you should also configure "SigmaTel CXD9872RD/K (OSS Mixer)" besides "HDA Intel"

Edit->preferences->mark [v] Capture

then
In-gain (max)

However, still can't work in video plugin of facebook (audio ok but not video..)

---


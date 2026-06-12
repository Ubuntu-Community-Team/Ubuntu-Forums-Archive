---
title: "USB soundcard that works OTB?"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by otakuj462 on 2007-02-08
Hi, I've finally given up getting my Dell Inspiron's built-in hda-intel soundcard to fully work. The mic input dies after suspend/resume. Heaven knows why. I'm using the latest alsa (14rc2), and this problem was noted as being fixed in the Alsa 13 changelog. Alsactl indicates that the soundcard's state is the same on resume as it is on suspend. So, basically, I'm stuck on this problem, and I'm on to famous Plan B: acquire an inexpensive USB adapter from Hong Kong!
The alsa website indicates that any usb adapter which is "standards compliant" will work with ALSA. Nevertheless, I'd like to hear of somebody else's success story before I plunk down $10 on a new piece of hardware. I'm think I'm basically looking for something like [this]("http://cgi.ebay.ca/USB-Size-5-1-Channel-3D-Sound-Audio-Adapter-Mic-Blue_W0QQitemZ320078445595QQihZ011QQcategoryZ3701QQrdZ1QQcmdZViewItem").
Or [this]("http://cgi.ebay.ca/USB-2-0-stereo-AUDIO-sound-card-ADAPTER-PC-Microphone_W0QQitemZ110087328344QQihZ001QQcategoryZ3701QQrdZ1QQcmdZViewItem").
Or anything else if somebody has a better recommendation. I just need my mic to work.
If anyone has had any experience selecting a usb sound device that worked out of the box, I'd greatly appreciate it if you could post and tell me.
Thanks!

-Jake

---

### Post by treesurf on 2007-03-03
I'll bump this thread, because I'm in the same boat.  After trying just about everything posted about hda-intel sound I still cannot get my mic to work.  Does anyone have suggestions for a USB soundcard or USB microphone that will work easily with Edgy?  I'd like to use this mainly with Gizmo Project.

---

### Post by otakuj462 on 2007-03-04
Hello treesurf! I have some new information that you might be interested in:

1) You may already know this, but adding 
```

options snd-hda-intel model=ref

```
to your /etc/modprobe.d/alsa-base file might get your onboard soundcard working. This allowed me to get my onboard soundcard to work, but it still breaks on suspend/resume. You may have more luck though.

2) I did buy the hardware i linked to above. It cost about $10 CAD with shipping. I'm fairly pleased with it. It worked for me right out of the box -just plug it in, and alsa installs it as a new soundcard. Then you can use gizmo or skype to select a different audio input device. The only problem with it is, essentially, that it is a very cheap, crappy piece of hardware. I don't know anything about soundcard technology, and so I'm going to describe this very crudely and perhaps you can make sense of it... My experience with it has been that it has a very limited range of volume that it takes before it disintegrates into static. So, for example, if I have the mic somewhat close to my face, and I'm talking normally, then most words will sound fine, but any word in which I make the "s" sound will sound crackly and bad. Also, there is a slight, high-pitched whine that comes through as well, but I think that this is fairly hard to notice on the receiving end if you're using a VOIP client. 
The goal behind purchasing this device was primarily to allow me to test the alsa usb drivers. Now that I know that they work, I may purchase a Logitech USB headset. I expect the sound quality to be far superior. But I'm happy using the cheap hardware as a temporary solution.

Hope this helps you out.

-Jake

---

### Post by treesurf on 2007-03-04
Thanks very much for the advice Jake.  I have tried adding that linel to my /etc/modprobe.d/alsa-base, but it didn't seem to help me much at all.  

My sound works fine except for the mic, which I only plan to use for VoIP, so that USB soundcard looks like it'll do the trick for me.  For ten bucks it's at least worth a try!

thanks again!

---


---
title: "Headphones not detected. No sound. Speakers work fine."
date: 2012-02-27
forum: Hardware
---

### Post by WikedX on 2012-02-27
I'm using Elementary OS which modeled of 10.04 I believe.

I'm on a Thinkpad x120e(lenovo) and when I plug in my headphones(standard jack, not USB) I cannot get sound to come through them, no matter what settings I try to mess with in audio.

I've done some Googleing but none of the solutions have seemed to work so far. I have a theory that it has to do with the fact the headphone and microphone jack are the same thing, which may be confusing the system. 

Any idea on what I can do? Any more info you need?

---

### Post by WikedX on 2012-02-27
Analog Stereo Output and Analog Stereo Duplex are the two options that work. They produce sound via speakers

IEC958, which I'm sure in my headphone jack, produces no sound.

Sorry I'm not providing much info. Tell me what you need and I will provide it

---

### Post by Yellow Pasque on 2012-02-27
IEC958 is digital out (i.e. not your headphones). You probably need to set the jack explicitly to headphone output using: [http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

---

### Post by WikedX on 2012-02-29
This may do the trick but it says dependency not met, libglib2.0(>=2.3)

I have my system fully up to date but only 2.0 is in my repos. Is there anywhere I can get 2.3?

---

### Post by Yellow Pasque on 2012-02-29
Are you trying to build from source or are you trying to install a .deb?
I think you need to build from source, and I have no idea if even that will work :\

---

### Post by Yellow Pasque on 2012-02-29
Actually, it looks like you won't need to build anything.
```
wget https://launchpad.net/~diwic/+archive/hda/+files/hda-jack-retask_0.20111129.tar.gz
tar xzf hda-jack-retask_0.20111129.tar.gz
cd retask
./hda-jack-retask
```

---


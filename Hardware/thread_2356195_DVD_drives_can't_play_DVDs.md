---
title: "DVD drives can't play DVDs"
date: 2017-03-20
forum: Hardware
---

### Post by lysander6662 on 2017-03-20
Now to be honest this is not only a problem with Ubuntu, W7 had this issue as well. What I don't understand is that my drives can be seen by the OS, but when you put a DVD in, it doesn't play. However, I was able to install Lightroom from a CD in them [one of them, can't remember which now]. If you put a DVD in they sit there and do nothing - both of them.

sudo lshw -short sees them

```
/0/3/0.0.0       /dev/cdrom  disk        DVD+RW ND-2100AD
/0/3/0.1.0       /dev/dvd    disk        DVD_RW ND-2510A

```

Any ideas as to why they can be seen but DVDs just sit in them? Maybe its a cabling issue but strange that it's both of them.

---

### Post by TheFu on 2017-03-20
I'm assuming you are talking about video DVDs, not data DVDs.  Data DVDs should "just work."

As for Video DVDs, things are a little more complicated thanks to DRM and different laws around the world related to breaking that DRM.  Microsoft paid for licenses so that everyone could watch DVDs legally on Win7, but not for Win8.1 and later.  Ubuntu doesn't do that because their OS is free and in some parts of the world, it is perfectly legal to install the necessary software without breaking any laws. 

Anyway - your question is common, so there are a few webpages which explain what is necessary: 
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

If your real question is something else, please explain.

---

### Post by lysander6662 on 2017-03-21
Interesting, and I may well have to look at that, thank you. But I think my question is slightly different. When I put a DVD [video] in the player, the OS doesn't even see the DVD. It should at least come up by name in the drive display or spin up, and it does neither. This is why I am wondering whether this is a hardware issue rather than a software issue. I may be wrong though.

---

### Post by TheFu on 2017-03-21
Did you mount the storage?  On my systems that is a manual thing.

**sudo mkdir /cdrom; sudo mount /dev/sr0 /cdrom**

Of course, if the media is corrupted, that won't work. Also, optical drives do wear out over many years. If nothing is working, try different cables and check that the power connection/cable isn't loose or broken.

---


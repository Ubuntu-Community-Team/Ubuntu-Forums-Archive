---
title: "Accidentally removed important software 9.10"
date: 2010-01-19
forum: Hardware
---

### Post by cdanderson04 on 2010-01-19
Hey

I am a new user Ubuntu 9.10 and I have been trying to learn how to do things.  I had most of it set up the way wanted expect that I was trying to get it to work with my iPod Touch.  In doing so I tried removing some of the software first and following some of the guides online.  I clicked Complete Removal and I do plead ignorance on this.  I am guessing I removed some important pieces of software.  The programs I was dealing with were things like libusb and stuff like that.  I was trying to get iFuse to work.

Anyways, now when I restart it says that I am running in low graphics mode and that there were errors with my HP Webcam and some other hardware and boots to command prompt.  With me having no knowledge of how to repair things like this I was looking to the community to see if they can help me out.

So I am wondering if there is a way to do a restore or something like that that will download the right drivers and what could have been uninstalled by my stupidity.

Thank you in advance.

--Colin

---

### Post by sgosnell on 2010-01-19
You need to reinstall the stuff you deleted.  If you don't know what it was, it may be difficult.  Open Synaptic Package Manager and see if you can find the packages you deleted.

---

### Post by pi/roman on 2010-01-19
Maybe this will get it up?

sudo apt-get install ubuntu-desktop

---

### Post by Sef on 2010-01-19
> Maybe this will get it up?

sudo apt-get install ubuntu-desktop

Application > Accessories > Terminal

copy and paste these commands:

```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

That will ensure you get the latest versions of anything being installed.

---

### Post by cdanderson04 on 2010-01-20
I am pretty sure this worked!  Thank you so very much for your help.  I really appreciate it.  I will think twice about removing things completely now without looking into it more!  Thanks again!

---


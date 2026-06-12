---
title: "Can't get Radeon X600 drivers installed"
date: 2015-12-15
forum: Hardware
---

### Post by Matt76 on 2015-12-15
I am new to Ubuntu, and I just installed it on my old Dell Dimension E510, which has a Radeon X600 card in it. I've looked through tons of forum posts with instructions on how to install it tried a few, but I kept running into errors that weren't posted. Again, I'm new to this, so I don't know how to proceed. Hopefully someone can help me through this step by step.

---

### Post by QIII on 2015-12-15
Hello!

The default open source Radeon driver installed when you installed Ubuntu is the correct driver for that hardware.

You will not be able to install a proprietary driver from AMD because AMD dropped support for that GPU in about 2008.  There is no way to install a proprietary driver.

---

### Post by Matt76 on 2015-12-15
That's what I thought at first, but I installed Cinnamon, and when I loaded it for the first time, a message came up and said something to the effect of it was using software rendering since there wasn't a video driver installed. Also, Unity was very laggy, wish seems to support that as well.

---

### Post by QIII on 2015-12-15
There is a video driver installed, called the Radeon driver, which is open source.  What *isn't* installed is a driver from AMD (ATI as it what known when those were manufactured.)

That is a very old card.  Unity is very heavy, so the GPU may struggle somewhat.  A lighter desktop environment might work better.  You could give Xubuntu or Lubuntu a try.

---

### Post by Matt76 on 2015-12-15
So is there no way to fix this problem then without upgrading hardware?

---

### Post by QIII on 2015-12-15
Unfortunately not.  That card is very old and AMD does not support it with a Linux driver.  

Again, however: a less graphics intensive DE might be better on that machine.  Before you go spending your hard-earned cash, that is worth a try.

---

### Post by Yellow Pasque on 2015-12-15
> **Matt76 said:**
> a message came up and said something to the effect of it was using software rendering since there wasn't a video driver installed.

Googling around a bit, I see Cinnamon can be finicky with older Radeon cards. So to make sure this is a Cinnamon issue and not an issue with your drivers, check:
```
glxinfo | grep -i string
```

---

### Post by MartyBuntu on 2015-12-15
> **QIII said:**
> There is no way to install a proprietary driver.

Well, technically there's *one* way...though it's rather arcane...

Installing the original 12.04 release of Ubuntu, which will still have security updates.

---

### Post by QIII on 2015-12-15
Actually, with that graphics adapter, the OP would have to install 9.04, since that particular group of cards lost ATI support in 2008.

---

### Post by Smokin Whale on 2015-12-15
If you want to run something from this decade, your best bet for that machine is Windows 8.1. I've got one working fine before with that old card. Windows 10 will BSOD on driver install from my experience.

---

### Post by MartyBuntu on 2015-12-16
> **QIII said:**
> Actually, with that graphics adapter, the OP would have to install 9.04, since that particular group of cards lost ATI support in 2008.

Wow. That card is prehistoric...

---


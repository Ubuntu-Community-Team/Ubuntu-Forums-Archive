---
title: "Diamond VC500 has trouble recording"
date: 2016-09-24
forum: Hardware
---

### Post by Ben_Rog-Wilhelm on 2016-09-24
I recently picked up a somewhat-cheap Diamond VC500 USB recorder in order to dump some VHS tapes. This was meant to replace an ancient bottom-of-the-barrel EasyCAP device. The EasyCAP device works fine, just with low quality. The VC500, unfortunately, does not; it crashes most software. ffmpeg seems to lock up while trying to figure out what video modes it's capable of.


The VC500 *does* work fine on Windows, but I'd really rather not use Windows for this - the tools are much worse.


I've tried various versions of Linux without any luck, as well as various tools on Linux. I finally found v4l2-compliance which exhibits the same behavior - it halts midway through testing. Note that it gets through the EasyCAP driver in less than a second, it's just the VC500 that gives it problems.


This all feels like a problem with the driver being used for the VC500, but I don't know where to start debugging. Any suggestions on what the next step is?

---

### Post by Bucky Ball on 2016-09-24
Welcome. I'd suggest you install one Ubuntu release, preferably the lastest supported one, 16.04. Flipping between various releases and flavours just gets confusing and we don't know what you're doing from one post to the next. Settle on one and install. Then plug the device in and run this:

```
lsusb
```

Post the output here between code tags (see green link, first line of my signature, bottom of this post) along with which release and flavour of Ubuntu you are using (Xubuntu 16.04 for instance).

Then I suggest you give a detailed description of what exactly is happening when you try to access the device with one particular software app. 'It crashes most software' gives us nothing to work with and doesn't mention which, if any, software it doesn't crash.

You also tell us you've tried various tools. Which? Unfortunately, we are not psychic and the more information you can give us about your hardware, the exact issue you're having and exactly what you've tried to fix it and the outcomes the quicker you are going to get support and hopefully a fix. :)

---


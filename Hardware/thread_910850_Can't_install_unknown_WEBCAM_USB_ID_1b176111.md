---
title: "Can't install unknown WEBCAM USB ID: 1b17:6111"
date: 2008-09-04
forum: Hardware
---

### Post by El Potro on 2008-09-04
Dear folks,

I just bought a generic webcam, in windows it works OK, but it keeps there unnamed. (I mean, it installs only because the cd-driver, but says only GENERIC WEBCAM)

So, back in ubuntu 7.10, it just recognizes it as: (as listed in lsusb)

Bus 005 Device 002: ID 1b17:6111  

But doesn't work. And much less auto-load modules nor anything like that.

I'm not so much into linux, that's why I ask for somebody's hand.

Does anybody know how to install this webcam? Isn't there a generic driver for it? Works at 480k and 2mp. Says NogaNet (local brand but I think it's just generic, imported from China).

Hope anyone can give me a hand.

Thank you very much in advance,

Mauricio

---

### Post by IntuitiveNipple on 2008-09-05
Does the camera have anything that looks like a model number on it? Does it include a microphone?

Maybe it looks like this?

---

### Post by Crafty Kisses on 2008-09-05
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by El Potro on 2008-09-05
Hi, thank you for helping IntuitiveNipple.

It certainly doesn't look like that one. This one looks awesomely weird. Grab a look.

And YES, does have a microphone.

How that info will help?

Thanks a lot

---

### Post by IntuitiveNipple on 2008-09-05
PCI Vendor 0x11B7 (11b7) is "ShenZhen E-Loam Technology Co.,Ltd", who trade as "E-LOAM". They have an [English-language web-site](http://en.eloam.cn/).

They have a large range of cameras with product IDs around 0x6111 (6111).

The one you have appears to be in the A0380 series, and is known as the "USB2.0 PC Camera".

The chip-set and/or camera is, I think, manufactured by [CNLTF](http://www.cnltf.com/), possibly translated poorly as "Guangzhou blue sky HSBC Electronic Co., Ltd".

Possibly this information may get you closer to finding out if there is any driver that will support the chipset.

**Update**: Just seen your photo... that'll be the [E-LOAM 6642](http://en.eloam.cn/product_detail.asp?pid=455)

Having looked at the Windows .inf driver file and the other supporting files it appears to be a USB Video Class device so in theory, if we add the device ID to the [Linux uvcvideo driver](http://linux-uvc.berlios.de/), it should work.

I'll do that tomorrow and let you have a custom driver to test.

---

### Post by El Potro on 2008-09-05
Hi everyone!

Codename, thank you, I've tried it, but it doesn't recognize the camera as it should, therefore it doesn't find it nor in Ekiga, nor in any other program.

IntuitiveNipple, I'm impressed! You've managed to find the model and everything about the camera so fast. Thank you a lot!

You say you can make out a driver? that's so great, I'll be glad of trying it. Please inform me when you're done and I can try it.

Once again, thank you all very much.

---

### Post by IntuitiveNipple on 2008-09-05
I've created a Launchpad bug report [#264948 "uvcvideo: camera IDs that should be added"](https://bugs.edge.launchpad.net/ubuntu/+bug/264948) to track these potential uvcvideo cameras. We will be better to post testing comments there to ensure the information can be found easily.

---

### Post by El Potro on 2008-09-05
Well done, let's hope everything will turn out ok.

---

### Post by Crafty Kisses on 2008-09-05
> **El Potro said:**
> Well done, let's hope everything will turn out ok.

Hopefully, I'm hoping more support for webcams will be present with Intrepid Ibex, but it also depends on the kernel.

---

### Post by IntuitiveNipple on 2008-09-05
> **Codename said:**
> Hopefully, I'm hoping more support for webcams will be present with Intrepid Ibex, but it also depends on the kernel.
For the growing number of UVC cameras with imperfect support for the 'standard', it is going t require a lot of upstream work in the uvcvideo project to keep up with the sheer numbers. At least it is better than the former situation where almost every new camera chip-set required a new driver!

Through my experimental uvcvideo-dkms driver package we will have a quick way for a non-technical user to discover if the camera device is UVC compliant (partially or fully) and then get the PCI IDs added into the uvcvideo driver as an Ubuntu patch until the upstream version catches up.

---

### Post by kubug on 2009-03-02
Was there any progress on this? I got one of these cameras too now, and it's not recognized. 

I tried building the uvc driver from source, but am getting some wierd error messages.

---

### Post by El Potro on 2009-03-02
Hello kubug, if progress is what you're asking for, I'm sorry but there's nothing (As far as I know).

Our cameras can still be used as many things, like paperweight for instance! What do you think about it? ;)

If you find out a solution or anything related, please be so kind as to posting it here.

Good luck,

Mauricio

---

### Post by kubug on 2009-03-24
Ok, I installed the latest UVC drivers from the website. It wasn't as hard as it originally looked. I didn't get the ebay-cheapy-webcam running, but I was able to get my Microsoft VX-3000 running well.

I am guessing they might be adding the ID to the drivers soon to the UVC drivers. Hopefully soon this will enable this little camera.

Here is what I did to install the drivers. Maybe in a little while this will work.

```

sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget http://linuxtv.org/hg/~pinchartl/uvcvideo/archive/tip.tar.bz2 && tar xf tip.tar.bz2 && cd uvcvideo-* && make && sudo make install && sudo depmod -ae $(uname -r)

```

Just copy and paste **the whole thing** in a terminal and wait 20 minutes or so for it to compile. Then reboot and see if it worked.

---

### Post by Jack Fear on 2009-07-21
Just to confirm that I have a similar eBay webcam which does not work. 

lsusb reports "ID 1b17:6111"

I've tried as suggested to installed the latest UVC drivers.

---

### Post by El Potro on 2009-07-21
When is this webcam going to be supported on Ubuntu?

It is about day...

---

### Post by kubug on 2009-07-21
Yeah, I tried last week to install with the latest drivers, but it's still a no go. 

I wonder if shipping that camera off to the developers would get it done?

---

### Post by El Potro on 2009-07-21
I think their answer would be: 

"Sorry, we have no time. Do it yourself please !!"

---

### Post by Jack Fear on 2009-07-22
I had a different ebay special that I bought last year that originally did not work on ubuntu.  I made a post about it and in about 2 days there was a patch.  I just forget where I asked about it.  Probably some place more specific to gspca.   :)  Often its about finding the right people to ask.

---

### Post by Jack Fear on 2009-07-22
_[U]any suggestions?_[/U][]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264948")

---

### Post by El Potro on 2009-07-22
May I suggest: If you really want to get it working: Use windows.

I talk through skype in a daily basis, and I have to go to windows if I want to have a video... It's a shame! I know, but that's how ubuntu is with its dear users.

Anyhow when I tried to buy an Ubuntu-compatible webcam (just for stop using windows) nobody knew which one to suggest me. (Usually the most compatible ones are from big brands, that means more money).

If you have any news please post them down.

---

### Post by kubug on 2009-07-22
Actually I have two webcams that work great under Ubuntu (other than the one in question here, which I bought for $12 on ebay... not a great loss).

The first one is a **Philips SPC 900NC**, which works out of the box. Great colors, great contrast (even in low light). The only thing is that under ubuntu it will only do 640x480. It could do more under windows, but for skype you won't need more than that resolution.

The other one is a **Logitech 9000 Pro**, which cost around $100.00 and thus is one of the more expensive models. BUT... if you want to be really happy with your webcam, and don't want to waste money on lower end models, I can't recommend it more. It has to be the best webcam I ever owned. The colors are rich, lots of contrast, great in low light, high refresh rate (60 fps). Everything looks awesome in it. Seriously, if you are going to use a webcam for Skype or anything else, get that one. Of course, you will need to be able to afford it. 

So those are my recommendations. Neither model is especially cheap, but I guarantee you, you will love either one of those webcams.

---

### Post by no2498 on 2009-09-07
any of you try to see it in 
gstreamer-properties

do you have

cheese

wxcam 

installed

---

### Post by El Potro on 2009-09-07
Hi no2498,

There is no module loaded, so this programs you have mentioned don't recognize the webcam at all. It's a pity, but the driver is needed, the modules, and haven't been developed so far :-S

---


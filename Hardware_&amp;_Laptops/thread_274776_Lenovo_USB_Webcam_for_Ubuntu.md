---
title: "Lenovo USB Webcam for Ubuntu?"
date: 2006-10-10
forum: Hardware &amp; Laptops
---

### Post by Aleksandersen on 2006-10-10
Hi,

Will this [Lenovo USB Webcam](http://www.lenovoblogs.com/design/design-innovation/2006/10/05/usb-web-camera-shaken-not-stirred/) run on Ubuntu -- or any other Linux distro?

And yes, it does look like a James Bond gadget or some kind of spycam. ;) And I like it!

[[img]http://bildr.no/image/14243.jpeg[/img]](http://www-131.ibm.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=-840&langId=-1&partNumber=40Y8519&storeId=10000001)

---

### Post by x64Jimbo on 2006-10-10
I don't have a definite answer, but with lenovo's recent decision to begin including SUSE on one of its notebook models, I can't imagine that there is a lot of their hardware that doesn't work with Linux. Finding out what's inside that camera would help a lot too. It could just be a reshaped and rebranded Logitech or something.

---

### Post by Aleksandersen on 2006-10-10
If you were to do a wild guess... What do you think? Will I be able to use it on Ubuntu or not?

And since it is such a new product I should not expect to get third party drivers, right?

---

### Post by uhajo on 2007-01-15
> **Aleksandersen said:**
> Hi,

Will this [Lenovo USB Webcam](http://www.lenovoblogs.com/design/design-innovation/2006/10/05/usb-web-camera-shaken-not-stirred/) run on Ubuntu -- or any other Linux distro?
[[img]http://bildr.no/image/14243.jpeg[/img]](http://www-131.ibm.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=-840&langId=-1&partNumber=40Y8519&storeId=10000001)

Aleksandersen,

I have it, I like it but it definitely does not work under Ubuntu Edgy. Funnily, Ubuntu registers it as an audio device (lshw shows:)
 *-usb
                   description: Audio device
                   product: Lenovo USB Webcam
                   vendor: Primax
                   physical id: 2
                   bus info: usb@5:2
                   version: 1.00
                   capabilities: usb-2.00 audio-control
                   configuration: driver=snd-usb-audio maxpower=480mA speed=480.0MB/s

But I can't even get Ubuntu to use the built in (very nice sounding) microphones. I gave up and use it with Windows (too bad) until a driver is available (someday, sometime ... in 2010). But what the heck, I just found out Skype under Linux is so outdated it does not even support Video (the very reason I bought this camera for).

Summary: Cool camera, good to fair picture quality, top sound quality (to my ears) but just no support using Ubuntu. SOS - Same old sh ... :( 

But ... get it anyway - it's a cool toy :-)
uhajo

---

### Post by david2b on 2007-03-22
I've got the Lenovo 3000 v100 with a built-in webcam too

lshw shows : 
*-usb UNCLAIMED
                   description: Generic USB device
                   product: USB2.0 Camera
                   physical id: 5
                   bus info: usb@1:5
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s

does not seem to work with feisty. Any news on this ?

---

### Post by Aleksandersen on 2007-03-23
I just got my Lenovo N100 3000. When I bought it I did not realise it had a built in web cam!

Anyhow, there is currently no working drivers for this cam. But there are an alpha version of the driver, but that curently only works on the ThinkPad version of the camera.

---

### Post by david2b on 2007-03-24
Hi

I'm very interested! Do you have an URL to get drivers ?
TIA

---

### Post by Aleksandersen on 2007-03-24
No, sorry. I cannot find my way back to it. But it is the same camera, only in some ThinkPad model instead.

---

### Post by zorkerz on 2007-11-26
I just bought a x61 with a usb webcam. I don't know how to get it to work or even find out anything useful about the webcam. It has a model name 40Y8519 and nothing else. I have seen apparently the same camera with the last 4 digits in the model name different.

Any ideas where to start?

---


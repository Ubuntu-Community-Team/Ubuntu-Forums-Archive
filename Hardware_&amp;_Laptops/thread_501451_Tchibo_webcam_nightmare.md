---
title: "Tchibo webcam nightmare"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by carriecomputers on 2007-07-15
I had a nightmare finding windows drivers for my Tchibo 226878 laptop webcam, it took hours of searching through German websites!

Now that I've switched to Ubuntu though it doesn't even acknowledge that the webcam is plugged in. Does anyone have any suggestions to get it up and running again?

---

### Post by w4ett on 2007-07-15
Does it show up in lsusb as any kind of device on the bus?  BTW, I googled for a driver in linux and can't find one either.

---

### Post by carriecomputers on 2007-07-15
I'm not entirely sure how to enterpret this output to be honest

> Bus 001 Device 002: ID 093a:2600 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  


---

### Post by carriecomputers on 2007-07-15
I have looked up pixart imaging on google and found these two pages which apear to be talking about supporting this webcam on linux (?). Does anyone think I'm on the right track? if so what do I do next?

I'm getting the hang of linux in leaps and bounds but every day something new still stumps me!

---

### Post by w4ett on 2007-07-15
> **carriecomputers said:**
> I'm not entirely sure how to enterpret this output to be honest

On Google....search this string:

093a:2600 Pixart Imaging, Inc.  Linux

Most results need to be translated........the bus id 093a:2600 Pixart Imaging, Inc.  is your cam, Ubuntu is recognizing it, but does not have support out of the box..  There are literally thousands of different chipset combos in webcams.....a lot of them do not have linux support and need kernel patches for them to work.

---

### Post by w4ett on 2007-07-15
Just for grins, install Camstream from Synaptic....it's the most simple Webcam app out there...if your cam can get working, it will work with that program.

---

### Post by carriecomputers on 2007-07-15
Ok, that program didn't identify the camera. I have downloaded the driver that is supposed to work

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

but I don't have a clue about how to install it, there is absolutely no documentation on that site.

---

### Post by w4ett on 2007-07-15
> **carriecomputers said:**
> Ok, that program didn't identify the camera. I have downloaded the driver that is supposed to work

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

but I don't have a clue about how to install it, there is absolutely no documentation on that site.

Here's a tutorial on installation in Ubuntu:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Probably one of the best how-tos I have found.

---

### Post by skynexus on 2007-10-10
I purchased a web camera with the same vendor id and product id and was also having problems getting it to work with Feisty. You were on the right track in pointing out the [correct website]("http://mxhaard.free.fr/download.html") for the driver. Theoretically, Ubuntu should have helped you along since it provides the required driver in the [gspca-source]("http://packages.ubuntu.com/feisty/graphics/gspca-source") package (that was my mistake - I assumed the package would suffice and went ahead). In practice though, this will not work  because you need a later version. In particular, version 1.00.18 since it adds support for Pixart PAC7311, which is what you want.

Installing the driver is very simple. You only need to unpack the archive that you downloaded, open a terminal and go to the directory that you just unpacked, and inside it type the following commands:

```
make
sudo make install
```
That is it. You should now be able to verify that you camera is working by connecting it to your computer and seeing if the file /dev/video (or similar) becomes available. Following that, you may start a suitable video application such as Camorama to assert that the camera is functioning properly. Note that you will need to repeat the above steps everytime you upgrade the kernel.

Unfortunaly, Gutsy is suffering from the same problem, that is, it also has an outdated version of the gspca driver with no support for PAC7311. I should probably file a bug report since this should be fixed before the official gutsy release.

To whom it may concern, I purchased my camera at a swedish retail store, Clas Ohlson, very low-end and cheap and with the not so appealing name of "Webbkamera" model TWC-30AP. This was a no-name camera with zero technical information online (not even the manufacturer, so I had to resort to the lsusb command to get the basic data needed to know what I was dealing with). The quality of the picture is extremely low, and the video flickers a little too much. I would recommend anyone considering a camera with PAC7311 to use another model instead. Cheers.

---


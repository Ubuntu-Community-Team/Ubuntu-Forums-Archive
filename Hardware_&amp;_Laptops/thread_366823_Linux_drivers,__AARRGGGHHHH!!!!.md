---
title: "Linux drivers,  AARRGGGHHHH!!!!"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by stchman on 2007-02-21
Hello all, I am somewhat new to the linux world.  One thing I have noticed is that Linux drivers are the most difficult thing to install.  I was lucky that my laptop worked out of box not including wireless card (I have a PCMCIA wireless card that linux supports).

I recently tried to install Ubuntu 64bit on my Athlon 64.  Everything went well until I had to install drivers for the GeForce 7600GT PCI-E card.  I still have not gotten the video card to work properly.

The last linux hurdle is going to be device drivers.  If linux can have easy to install drivers then and only then will it challenge Windows or OSX.

All in all I like Ubuntu and it works very nice on my laptop and an older desktop as Ubuntu has all the drivers present.  As far as software installation, Ubuntu makes this a snap with teh Add/Remove and synaptic package manager.

I do predict that in the next 3-5 years linux will be a big player in the desktop/laptop market.

---

### Post by christhemonkey on 2007-02-21
Is this a support request?
Or just general musings?

To install nvidia drivers, enable universe repo then type:
```
sudo apt-get install nvidia-glx 
```

---

### Post by vigleik on 2007-02-21
There are many ways to install the nvidia driver for your video card. For example, you can use easyubuntu (google for it). It's really easy, you just have to run it and check the "install nvidia driver" checkbox.

But I agree, sometimes installing (and configuring) the correct driver for a piece of hardware is hard. Sometimes it's impossible, as there is no driver. This will most likely not change until linux has a bigger market share, big enough that hardware manufacturers take linux seriously. When that will be I don't know, but I'm confident the day will come.

---

### Post by stchman on 2007-02-21
> **christhemonkey said:**
> Is this a support request?
Or just general musings?

To install nvidia drivers, enable universe repo then type:
```
sudo apt-get install nvidia-glx 
```

I did that through the synaptic package manager.  When I try to use the it linux tells me I have the wrong kernel but I have the proper one installed.

---


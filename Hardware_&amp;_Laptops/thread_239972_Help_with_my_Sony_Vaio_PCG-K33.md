---
title: "Help with my Sony Vaio PCG-K33"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by Kanybus on 2006-08-20
Hey guys,

I'm new to the Linux community and decided to try Ubuntu on my laptop. So far I love it, but in doing so I lost the use of my function key so I can't figure out how to change my screen brightness or volume... screen issues more important. Is anyone familiar with Sony Vaio laptops and able to over come this annoyance?

---

### Post by coffeecat on 2006-08-20
Hello Kanybus. I managed to get the Fn key combinations working in my Sony Vaio FS215B, but if you're new to Linux you may find the links I'm giving you hard to follow. It involves compiling scripts and delving around in configuration files. Also, I don't know whether this will work on your Sony because the instructions are for the FS series.

First of all you will need to install the Ubuntu build-essential package otherwise the scripts won't compile. You can do this from Synaptic, or from a terminal with:

```
sudo apt-get install build-essential
``` 
The method I used you can find [here]("https://www.granny.homelinux.org/%7Elinho/files/delta.ubuntu"). The 'cute feedback' is a slider bar that appears near the bottom of the screen when you change screen brightness or volume. It looks much better than the Windows one - but of course. :wink:

The following two links seem to have the same instructions (without the cute feedback) but I haven't gone through them in detail - there might be differences. You can find them [here]("http://users.skynet.be/thomasvst/linux-on-laptop/") and [here]("http://www.linux-laptop.net/hosted/ubuntu_sonyvaiovgnfs315b.html"). All the links are for Breezy but the Fn key howto (in the first link) worked fine in Dapper.

Lastly, have a look for your Sony model at [linux-laptops.org]("http://www.linux-laptops.org/") and [linux-laptop.net]("http://www.linux-laptop.net/"). You might find something more specific for your model.

---

### Post by Kanybus on 2006-08-20
Thanks Coffeecat, I'll try those out later today once I wake up and actually get some coffee in my system.

---

### Post by coffeecat on 2006-08-20
> **Kanybus said:**
> ...once I wake up and actually get some coffee in my system.

Excellent idea. :wink:

Best of luck.

---


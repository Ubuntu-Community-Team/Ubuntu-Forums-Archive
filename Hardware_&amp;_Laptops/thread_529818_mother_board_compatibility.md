---
title: "mother board compatibility"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by Z.K. on 2007-08-19
I am looking to buy a new mother board and I have found several that I would like to buy, but I am wondering if linux supports these boards and if there are any other concerns that I need to be aware of.  The boards I am looking at are:

Gigabyte GA-965P-DS3
Gigabyte GA-965G-DS3
Gigabyte GA-P35-DS3R

Asus P5K SE
Asus P5B
Asus P5KC

I am concerned that being so new, they might not be supported by Linux.  Also, I have heard that there might be problems with the SATA II and the IDE controllers on the 965 chipset.  I am kind of looking to go with the P35.  I was wondering if anyone has any suggestions or advice on this.  It has been a while since I bought a new mother board and I am not really up on all the new technology though it seems like the P35 with a core2 processor is the way to go.

   Z.K. :confused:

---

### Post by linuxwizard on 2007-08-20
Look through here you might find something that will help you

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by tommy18crowe on 2007-08-20
I would recommend the Asus, I seem to have better performance(In Ubuntu that is) and better easy of use with them. However if you have onboard sound, they have a tendacy to not work, get a Sounblaster Audigy for this.

---

### Post by Westerberg on 2007-08-22
> **Z.K. said:**
> I am looking to buy a new mother board and I have found several that I would like to buy, but I am wondering if linux supports these boards and if there are any other concerns that I need to be aware of.  The boards I am looking at are:

Gigabyte GA-965P-DS3
Gigabyte GA-965G-DS3
Gigabyte GA-P35-DS3R

Asus P5K SE
Asus P5B
Asus P5KC

I am concerned that being so new, they might not be supported by Linux.  Also, I have heard that there might be problems with the SATA II and the IDE controllers on the 965 chipset.  I am kind of looking to go with the P35.  I was wondering if anyone has any suggestions or advice on this.  It has been a while since I bought a new mother board and I am not really up on all the new technology though it seems like the P35 with a core2 processor is the way to go.

   Z.K. :confused:
I recently bought the GA-965P-DS3.
It works fine after some tweaking.  You have to patch the linux kernel to get the motherboard to work with Ubuntu.  The problem is the default Linux network driver, sky2, doesn't work well with the motherboard's Marvel Tech network controller.  Symptoms are eth0 dropping under heavy transfers and freezing.  I was going to RMA the motherboard until I found this thread:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104929](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104929)

Basically, you download the driver from Marvell's site and run the installation script, which will also deactivate the sky2 driver.
I've had no problems since installing the new driver.

---

### Post by calvinandhobbes on 2007-08-22
my abit ip35 seemed to work out of the box for ubuntu.  on board audio and network worked like a champ, though i need to make sure the audio sound levels are as high as they are supposed to be (crappy speakers versus real reported problems).  only "problem" i would say is that i cannot get a proper reading of each CPU core temp working.  the guides here are quite thorough, the process just doesn't work for my board (i think it is because it is just new enough the driver is not available yet for linux).

---

### Post by eeried on 2007-09-20
> I recently bought the GA-965P-DS3.
It works fine after some tweaking. You have to patch the linux kernel to get the motherboard to work with Ubuntu. The problem is the default Linux network driver, sky2, doesn't work well with the motherboard's Marvel Tech network controller.

Is the network the only problem. you speak of patching the kernel then you add installing the right driver is the solution. So no need to patch the kernel then, is there?

I'm interested in that mobo

---

### Post by Westerberg on 2007-09-25
I may have misspoke.
They only thing I did was deactivate the default network driver and install the Marvell Tech driver folowing the directions in cocopop's post (second from bottom) in this thread:
[http://ubuntuforums.org/archive/index.php/t-395190.html](http://ubuntuforums.org/archive/index.php/t-395190.html)
I've had no network problems since doing that.  No problems whatsoever, in fact.

---

### Post by eeried on 2007-09-26
Many thanks for the helpful link Westerberg :)

---


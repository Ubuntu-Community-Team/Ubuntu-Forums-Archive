---
title: "ATI Mobility Radeon 9200 drivers and external monitors"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by markcgriffiths on 2008-04-07
Hi,

I have a [Compaq Presario 2500]("http://www.ciao.co.uk/Compaq_Presario_2500__5800184")

It worked fine, I had advanced desktop settings, wobbly screens etc..  But I had an external monitor, which I wanted to play movies on.  I could play movies already on the laptop monitor.  Then I did this:

Method 1: Install the Driver the Ubuntu Way

This will install the driver that is currently in the repositories. It may be older than the current version from AMD.

sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

and Method two.

[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

Now.  I don't have those Compiz settings or video working on my second monitor.  How do I get videos on my second monitor and those advanced desktop settings back?  Currently the video plays on the laptop's monitor but I get a black screen on my external monitor.  I only need to use one monitor at a time.

I only get a black screen when I play movies at other times it works fine.  I tried that flgrx driver but then my computer didn't work.  Those open source ATI ones seem better.

---

### Post by yekibud on 2008-04-12
I have the same problem connecting my Dell Inspiron 1500 with ATI Radeon Mobility 7500 via PC/CRT monitor cable to a 40" Samsung LCD TV.  Screen displays fine but video/ movies just give a black screen on the LCD TV while playing on the laptop fine.

Any tips, anybody?

---

### Post by markcgriffiths on 2008-04-13
Hi,

I forgot about this.

Install xserver-xgl and the it will work but will ruin Compiz.

---


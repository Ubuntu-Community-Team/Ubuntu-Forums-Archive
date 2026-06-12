---
title: "Samsung Series 5 Chromebook on Ubuntu?"
date: 2011-06-29
forum: Hardware
---

### Post by sunwatt on 2011-06-29
This notebook appeals to me for afew reasons. The SSD, the dual core processors, screen size and price.

Amazon.com said I can return it within 30 days. 

Does anyone have anything I should know on the laptop itself?

I'm not interested at all in Chrome OS. 

thanks!!

Jim
Dell Mini 9 16gb SSD

---

### Post by genbeany on 2011-07-04
Apparently this guy did it: [http://www.youtube.com/watch?v=XjNlec45ly4](http://www.youtube.com/watch?v=XjNlec45ly4)

BUT HOW

---

### Post by sunwatt on 2011-07-04
He says this...." i followed the&#65279; instructions for installing ubunutu on the cr-48".

Now I have to find these instructions.... 

thanks

Jim

---

### Post by sunwatt on 2011-07-04
I'd like to just give the SSD to Ubuntu, and wipe out Chrome OS, isnt the install the same for any other computer? Just wondering why is it necessary to follow the cr48 instructions.

I have not found those yet.

---

### Post by Dsmithjr on 2011-07-08
You can find everything you need to know here: [http://cr-48.wikispaces.com/Home](http://cr-48.wikispaces.com/Home)

You can't just install Ubuntu like any other system because Chromebooks don't have a normal bios and cannot boot from USB.  I have Ubuntu on my Series 5 and everything works great except I haven't been able to get the 3G working yet.  

Good luck.

P.S. If you want to know what the script is doing, it's everything from these instructions: [http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48](http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48)

---

### Post by sunwatt on 2011-07-08
Thank you!  Are you running dual boot, or does Ubuntu have the whole 16gb?

---

### Post by Dsmithjr on 2011-07-08
I'm dual booting.  It's not possible to give Ubuntu the whole 16GB without installing a new BIOS which requires taking apart the Chromebook.  The Ubuntu you'll be installing will still be using the Chrome OS kernel so you have to keep it there for it to work.  If you want Ubuntu only, you need to look into installing a new BIOS.  There's one called Lugi, but as I said it involves taking apart your Chromebook and voiding your warranty.  It's also not tested on the Samsung Series 5 so flashing the new BIOS will probably brick your system.

You can dual boot Ubuntu and give Ubuntu up to 10GB of space if you think you'll spend most of your time in Ubuntu.  That only leaves around 1GB of space for Chrome OS.  However, Chrome OS doesn't need much space because it only using it to save system setting and cache.  The default Ubuntu install will take up around 2.6GB of space.

Again read this link to find out more: [http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48](http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48)

---

### Post by sunwatt on 2011-07-08
This is a little deep for me, when my Chromebook gets here, I'll have to return it unopened.

Too bad, dual processors, 12" screen, SSD (non spinning wheel!) and $429....  

I'm willing to do a little hacking, if I can do it without blowing the warranty. 

This is more than I can do myself.

You really saved me a huge headache.. I'm really glad I came here and asked.

Thank you!

---

### Post by sloggerkhan on 2011-07-10
It's pretty disappointing that there don't seem to be any normal netbooks around these days with chromebook like specs for anywhere near the price, let alone free internet.

---

### Post by Dsmithjr on 2011-07-14
You know, that's not really true.  Along with my Chromebook, I also own a Asus 1215P-MU17 which has -basically- the exact same specs as the Samsung Chromebook but which cost about $70 less vs the WIFI only version.  Yes, the Chromebook uses the N570 processor vs the N550 in the Asus; and, yes, the Chromebook comes with 2GB of RAM vs the 1GB of RAM found in the Asus, but you can always upgrade the Asus to 2GB and still come out ahead cost wise.  The Asus is really a nice netbook.  You have the same size screen as the Samsung Chromebook but with a better resolution, and you still get some really good battery life.  About the only thing I really like more on the Chromebook is its SSD.  But even then, the 16GB SSD in the Chromebook probably isn't enough space for your average Ubuntu install once you start adding on programs, documents, videos, music, ect...

---

### Post by sunwatt on 2011-07-14
My Ubuntu 10.04 install and all the software I need toped out at 5.3GB. So 16gb ssd is plenty for me.

I sent my Samsung series 5 Chromebook back today for refund.

It cant bootup on a live USB, and installing Ubuntu is a PAIN to do.

The bios will not allow Ubuntu.

Im not interested in living on a cloud... the hardware was sweet, but no sale.

---

### Post by emreg00 on 2012-02-01
In a couple of mins, I managed to dual-boot ubuntu using the instructions on this web page (no USB hassle -- requires only internet connection): [http://www.devchronicles.com/2011/10/installing-ubuntu-on-samsung-series-5.html]("http://www.devchronicles.com/2011/10/installing-ubuntu-on-samsung-series-5.html").

Hope this helps.

---

### Post by 23senick on 2012-10-03
Just installed 12.04 on Samsung 550 4gb chromebook following the instructions here:

[http://chromeos-cr48.blogspot.co.uk/2012/04/chrubuntu-1204-now-with-double-bits.html](http://chromeos-cr48.blogspot.co.uk/2012/04/chrubuntu-1204-now-with-double-bits.html) 

Apparently this script will also work with older Samsung Chromebooks.  Thought I'd post in case anyone else thinking about it.

Generally very easy to install, and Ubuntu is so fast on this machine  it's untrue, 10 second boot etc.  Great battery life, nice design, good value.  Loving it!

Only downsides thus far - small SSD, quirky keyboard (no "delete" key, two-finger click instead of right click) and the WiFi connection looks slow [1Mb/s - though in reality seems very fast and smooth).

---


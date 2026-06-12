---
title: "Hardware advice sought"
date: 2014-01-03
forum: Hardware
---

### Post by lshepley on 2014-01-03
I would like to by the following for a Ubuntu machine

amd 64 bit 4 core processor
compatible atx (which I hope means full size) motherboard
appropriate memory

prefer APu, which I hope means on board graphics.
would like something fairly cheap, out of date but still available fine, mainly reliable

my first post, so if I messed up, please tell me that too.

thanks.

---

### Post by king.of.random on 2014-01-03
What is your budget? Most amd products are much cheaper than there intel/nvidia equivalents. You rightly surmise that the latest amd apu's have good on-board grphics as long as you're not a video editor! :) Atx boards are the standard large size. My big question though is what do you intend to do with this pc build and consider what you may be wanting to do in 12-18 months time. Getting the Motherboard right will mean that you can at a later date upgrade you other hardware to higher specs. for example faster processor, more RAM. USB3 is the latest standard and could be useful to you if you regularly import photos/videos from a camera.

Buying an off the shelf pc is the easy option but working out your needs and a little background research ans building your own is much more fun. There are numerous forums and sites that can help with this. Just remember that electronics hate static electricity so always earth yourself befor handling... ie touch a tap :)

Happy adventures!!!!

---

### Post by lshepley on 2014-01-04
Thank you for your thoughtful answer.

Actually, I've been "making" my own computers for years but without a real understanding of what I was doing.  I used to know something, but that was in the 80's, and a lot has changed.

I do intend to upload quite a bit of video from a new camera and hope to be able to write a fairly long program, which I wrote a long time ago in dbase (dos) in perl, which I don't know yet.  I intend to learn.  I haven't written any code for decades, but I loved it.  As you've probably guessed, I am retired.

As to budget, I'm not poor, but I am cheap.  I definitely want USB3 and a number of SATA connections, as I may use a number of disk drives for various reasons.  Also, I have several old computers running here (I don't throw much away), and I'd like to make the new one a data repository and use its printer.  All in good time and, frankly, for the fun of it.

Actually, I'm not so worried about fine tuning as I am about getting something that works.  If I have to replace it later when I know more, that could be part of the fun.  As you can see, I have time on my hands.

Thanks very much again.

---

### Post by sudodus on 2014-01-04
I have an old hp xp 8400 workstation according to this link

[http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12132708-12132710-12132712-12132712-12132712-12431664-80700761.html?dnr=1](http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12132708-12132710-12132712-12132712-12132712-12431664-80700761.html?dnr=1)

but with ***two*** dual core xeon processors. It is quite old, but still going strong, for example good for converting video with ffmpeg with all four processor cores. I got it second hand, and I have added two things: a sound card because the original sound did not work, and a graphics card to be able to play high definition video (1920x1080-50p), nvidia geforce GT 430, that can use vdpau with an nvidia proprietary driver. I'm running Ubuntu 12.04.3 with Xubuntu-desktop right now.

It is well equipped for running many SATA drives, and if you find such a computer, it might be an alternative for you.

---

### Post by Yellow Pasque on 2014-01-05
If I was building an AMD box for your intended usage, I'd focus on building around this APU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819113288](http://www.newegg.com/Product/Product.aspx?Item=N82E16819113288)
With the APU, you can try the integrated graphics and add in a discrete GPU if you find they aren't usable.
Alternatively, you can save $25 (to use towards a discrete GPU) and get an equivalent standalone CPU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819113329](http://www.newegg.com/Product/Product.aspx?Item=N82E16819113329)

Personally, I'd shy away from integrated graphics on the AMD side. The open-source radeon driver for modern RadeonHD (7000-series and later) graphics just isn't there yet, especially if you don't want to use experimental code that doesn't come with a stock Ubuntu install. That forces one to use Catalyst binary driver, which which is less than ideal for video playback acceleration (and has all kinds of issues with serious gaming).

For a discrete GPU, a GT640 is ideal for a cheap, low-end card that does great video playback. Unless you want to do more demanding gaming, it will be sufficient.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130969](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130969)

Intel doesn't seem appropriate if you're trying to get a cheap quad core, but I like this chip because it has a lower power envelope and HD4600 graphics: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819116953](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116953)

---

### Post by lshepley on 2014-01-15
Thank you, sir.

---

### Post by Willyweasel on 2014-01-16
If you're going to be getting a APU one thing to consider is ram speed. The faster the memory you use the better the onboard graphics performance will be. Also not knowing what your exact budget is makes it difficult when recommending hardware, but here goes.

Motherboard [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131937](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131937)
APU [http://www.newegg.com/Product/Product.aspx?Item=N82E16819113333](http://www.newegg.com/Product/Product.aspx?Item=N82E16819113333)
Memory [http://www.newegg.com/Product/Product.aspx?Item=N82E16820313416](http://www.newegg.com/Product/Product.aspx?Item=N82E16820313416)

I think the above would suit your needs nicely, and leave room for upgrades in the future.

---


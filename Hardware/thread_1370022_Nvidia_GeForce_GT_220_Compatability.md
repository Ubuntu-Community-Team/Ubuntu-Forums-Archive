---
title: "Nvidia GeForce GT 220 Compatability?"
date: 2010-01-01
forum: Hardware
---

### Post by hfourxzeror on 2010-01-01
Hi Everyone!
This is my first time using the Ubuntu forum!
I've been using Ubuntu on and off for several years, but I've decided to use Ubuntu for a dedicated media center (Boxee 0.9.20).

I've had my system up and running for a couple weeks now running a Dell Optiplex GX270.

Some general specifications:
2.8 GHz processor
768mb RAM (I'm purchasing an additional 1GB of ram)
Integrated Intel Video + Audio
Visio 52' LCD tv

Now, I'd like to add a new video card that has faster processing and HDMI output.
I've found this video card and wanted to know if I could get it to work with Ubuntu 9.10!

**ASUS ENGT220/DI/1GD2(LP) GeForce GT 220 1GB 128-bit DDR2 PCI Express 2.0 x16 HDCP Ready Low Profile Ready Video Card**

Newegg Link: **[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121347](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121347)**

I've been trying to find out if the Nvidia GeForce GT 220 would be compatible with Ubuntu 9.10?! So would it work? Or not?

Thanks in advanced!
Dale :)

---

### Post by epz on 2010-01-01
Hello,  it looks like you are not going to have any problem with your nvidia gt 220.  
I don't want to say something wrong but as far as I know ubuntu would recognize it without any driver, but of course I might be mistaken.
   In any case here is the link for nvidia geforce gt 220 drivers.  
For linux 32 bit [http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html)  
For linux 64 bit [http://www.nvidia.com/object/linux_display_amd64_190.53.html](http://www.nvidia.com/object/linux_display_amd64_190.53.html)  
I don't really get what ' on and off ' means but, if you have any doubts on how to install those drivers you can check in
 'Administration / Proprietary drivers (sorry my english -.-)' if there is something for a '1 click' install
  Hope it helped.

---

### Post by hfourxzeror on 2010-01-01
Thanks mate. I ordered it.
I'll post my results! :D

---

### Post by cascade9 on 2010-01-02
Sorry to tell you this....

Dell Optiplex GX270 has only AGP and PCI slots, not PCI-E. So while a PCI-E GT 220 should work fine with ubuntu, its not going to fit into your computer.

---

### Post by hfourxzeror on 2010-01-02
Gosh! Thanks man! You saved my skin!
Looks like I'll have to purchase a new computer from Craigslist.... (I found a Dell for 100 bucks! :D)

The Dell Optiplex GX280 DOES support PCI-E, correct?

Thanks,
Dale

---

### Post by cascade9 on 2010-01-03
Yeah, the GX280 does have PCI-E.

---

### Post by jjhuopa on 2010-01-03
I have used a Palix Geforce GT 220 512MB PCI-E card with Ubuntu 9.10 for a few days without any problems, the newest driver works fine with me. I am so relieved to get rid of my ATI Radeon HD3650 card, it almost made me buy Windows 7.

---

### Post by hfourxzeror on 2010-01-03
> **jjhuopa said:**
> I have used a Palix Geforce GT 220 512MB PCI-E card with Ubuntu 9.10 for a few days without any problems, the newest driver works fine with me. I am so relieved to get rid of my ATI Radeon HD3650 card, it almost made me buy Windows 7.

Thanks mate. How does it do with processing? Any information on HDMI?

---

### Post by jjhuopa on 2010-01-07
What do you mean with "processing"? Haven't tested with any FPS-program but the picture is sharp, Compiz works and Skype is clear. That's all I need. Haven't tried HDMI, I use DVI.

---

### Post by mobrien118 on 2010-01-11
I just bought a GeForce 220 GT card (the MSI one with 512 RAM) but... it is not playing nice with my monitor over HDMI :-(

I have a dell W3201C which has a native resolution of 1360x768. I can use 1080i, but the compression makes the screen fuzzy and the edges are not visable.

Also, there is no sound, but the "sound card" part of the card shows up in 'lspci'. Anyone have any ideas to get this thing fully working with Ubuntu?

Curiously, it only made the 185.x nVidia drivers available, while I thought you could use 190.x in Ubuntu.

Thanks,

--mobrien118

---

### Post by pherilux on 2010-02-02
Hello all, I have not tried my gt 220 vard with HDMI or DVI, only VGA and it works perfectly with the 190.53 driver. I posted [here]("http://phrlx.blogspot.com/2010/01/how-to-install-nvidia-drivers-in-linux.html") a tutorial on how to install the drivers (RUN) in Linux mint 7 and 8 which are the same as ubuntu 8 and 9, respectively.

I hope this helps as I was lost in this matter a little while ago.

---


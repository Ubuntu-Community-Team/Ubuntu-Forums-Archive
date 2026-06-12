---
title: "Media PC build, Drive?"
date: 2014-03-12
forum: Hardware
---

### Post by bucket81 on 2014-03-12
Hello!

So this is what I want to put together. 

CPU: AMD A4-5300 3.4GHz Dual-Core Processor  
Motherboard: ASRock FM2A88X-ITX+ Mini ITX FM2+ Motherboard  
Memory: Corsair XMS3 4GB (2 x 2GB) DDR3-1600 Memory  
Storage: A-Data Premier Pro SP600 64GB 2.5" Solid State Disk   
Case: Cooler Master Elite 130 Mini ITX Tower Case  
Power Supply: Silverstone Strider Plus 500W 80+ Bronze Certified Fully-Modular ATX Power Supply 
[PCPartPicker part list"]Parts list]("http://pcpartpicker.com/p/38fn1) 

Im planing on this being a HTPC, I have a couple drive with movies and music that will be installed. What I'm worried about is drivers. I've read that AMD doesn't have as many drivers for Linux available and Im not sure where to look.  Do you guys think I can successful run Ubuntu and XBMC on this system?

---

### Post by open2reason on 2014-03-12
Hi,
If you are using the 7480d [http://shop.amd.com/us/All/Search?SearchTerms=%20A4-5300](http://shop.amd.com/us/All/Search?SearchTerms=%20A4-5300) on 12.04lts 64bit then

> Version : Ubuntu 12.04 LTS 64bit

Processor : AMD A4-5300 (FM2) 3.4 GHz, TDP 65W
Video : AMD Radeon HD 7480D integrated
MOBO : Asus F2A55-M (FM2)
Memory : Kingston HyperX 8GB 1600MHz DDR3 CL9 XMP (2x4GB)
Lite-On DVD RW/CD RW SATA Drive
Storage : Seagate 7200rpm SATA 500gb

Works flawlessly, using [AMD Catalyst 12.10 drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29"). I don't know if there should be, but no problems with UEFI bios either, it just booted right away to GRUB.                 
via [http://ubuntuforums.org/showthread.php?t=361236&page=84&p=12387917#post12387917](http://ubuntuforums.org/showthread.php?t=361236&page=84&p=12387917#post12387917) suggests the graphics may well work. 

As with all things AMD Radeon then [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) and [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) are worth browsing.

---

### Post by bucket81 on 2014-03-12
So from what that says the open source drivers will work... I'm not sold on the AMD does Intel have more drive support?

---

### Post by open2reason on 2014-03-13
Bucket81,
On the whole the on chip / cpu graphics processing offered by Intel works right "out of the box" whereas that from  AMD/ATI rely upon closed source offerings from the vendor or whatever the Ubuntu community can supply.
May well be a contest between price / availability, ease of use with Ubuntu releases and the performance of the applications you wish to run.

Hope this helps and if not then someone else will be along soon to correct my advice.

---

### Post by Yellow Pasque on 2014-03-13
Forget about the proprietary AMD drivers (i.e. fglrx/Catalyst) because they're not ideal for running XBMC anymore. The XBMC devs used to offer direct support for libxvba (what Catalyst uses for video accel), but they have switched to recommending open-source radeon driver and VDPAU. The best thing you can do in  that case is use Ubuntu 13.10 and this PPA to enable VDPAU: [https://launchpad.net/~oibaf/+archive/graphics-drivers/?field.series_filter=trusty](https://launchpad.net/~oibaf/+archive/graphics-drivers/?field.series_filter=trusty)  (or run 14.04 where VDPAU is enabled in the repo). Even that's not foolproof as VDPAU support for Radeons is a relatively recent feature... Oh, and don't forget to manually enable DPM and HDMI audio (if desired) on Ubuntu 13.10 and older ( [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) )

As for Intel, I'm sure you'll find some complaints about Intel GPU's running VA-API as well (no guarantees in Linux). Nevertheless, these low-power chips look very promising for an HTPC:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116947](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116947) (dual)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116953](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116953) (quad)

You could also go with a cheaper Intel chip and throw in a discrete Nvidia card (maybe something like a GT610)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116950](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116950)

As for PSU, 500W is gross overkill. A system like this should pull no more than 200W at full load (i.e. gaming or benchmarking). A 350-450W PSU is more appropriate, so you can save a few $$ there:
Seasonic G360 - [http://www.amazon.com/Seasonic-80PLUS-ATX12V-Supply-SSR-360GP/dp/B008XEYT5M/ref=pd_sxp_grid_pt_0_2](http://www.amazon.com/Seasonic-80PLUS-ATX12V-Supply-SSR-360GP/dp/B008XEYT5M/ref=pd_sxp_grid_pt_0_2)
FSP Aurum 400W - [http://www.newegg.com/Product/Product.aspx?Item=N82E16817104172](http://www.newegg.com/Product/Product.aspx?Item=N82E16817104172)

---

### Post by mastablasta on 2014-03-14
that's what i wanted to say - the setup is overkill for media PC.

there are some very good preset boxes on dealextreeme. for abotu 130-150 USD  or something like that (without disk). read a review on some forums i think openelec. apparently a company thta is no-name to us makes a very high quality build at a very good price. depends all on how many users and what the PC will be doing exactly. 

i use raspbery pi for media center. the whole setup including external 2GB hard disk cost me 130 EUR.

also media center is usually on all the time so you will want to reduce energy output as well as trying to have as few fans as possible. who wants to listen to those while watching a movie.... :-)

raspbery pi fits this in my case. no fans, fast enough for playing movies and you tube videos. i also use it for torrents. low energy footprint (per years should use abotu 4-5 eur of electricity)

---

### Post by Yellow Pasque on 2014-03-14
Raspberry Pi might be a bit too light, but an Intel NUC could be just what the doctor ordered: [http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1)
The main thing to avoid if you're looking at this kind of system is the older Atom processors (the ones with PowerVR graphics, i.e. Cedar view/Trail).

---

### Post by bucket81 on 2014-03-14
Well I forgot to put that I was going to put 3 3.5 drives in there for storage. And I think I miss calculated my power needs. 

I'm liking the NUC idea and had looked into it a bit but dismissed it because of my storage needs. but I could run one of these   [http://www.newegg.com/Product/Product.aspx?Item=N82E16817392056](http://www.newegg.com/Product/Product.aspx?Item=N82E16817392056)

I also have some laptop ram collecting dust in a drawer.

---


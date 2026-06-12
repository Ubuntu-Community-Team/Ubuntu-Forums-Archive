---
title: "ASUS A8R-MX/SI Chipset Compatibility questions"
date: 2006-12-26
forum: Hardware &amp; Laptops
---

### Post by The Iron Curtain on 2006-12-26
Hi, I found an [    ASUS A8R-MX/SI Socket 939 ATI Radeon Xpress 200 Micro ATX AMD Motherboard]("http://www.newegg.com/Product/Product.asp?Item=N82E16813131049") on Newegg.com

I looked at the specs for the mobo, and I want to know if the LAN, video and audio chipsets are compatible. I'm not a gamer, so I'm not going to buy a video card unless I would need one. When i do do i have to buy ATI? I've heard that Nvidea is better, is that true? 

Here are the Chipsets:
North Bridge 	ATI Radeon Xpress 200
South Bridge 	ULi M1573
Onboard Video Chipset 	ATI Radeon X300-based 2D/3D
Audio Chipset 	Realtek ALC880
LAN Chipset 	Marvell 88E8053



I've looked around the compatibility sites, but I haven't found any answers.  I googled    linux compatibility  ASUS A8R-MX/SI   and found nothing helpful. I also looked at these sites/threads and couldn't find any help either:  [HCL]("http://doc.gwos.org/index.php/Asusmobo"), [Linux Hardware Compatibility HOWTO]("http://tldp.org/HOWTO/Hardware-HOWTO/motherboards.html#AEN251"),  [Desktop Hardware Compatibiliy List]("http://ubuntuforums.org/showthread.php?t=183664"). 

I decided to google each chipset as   linux compatibility <chipset>:
ATI Radeon Xpress 200: I got [this]("http://www.fys.uio.no/~henger/htpc/radeon_xpress_200.html") and [this]("http://www.linuxquestions.org/questions/showthread.php?t=342987"). both reference Fedora Core.
ULi M1573: I ended up at this[ site]("http://www.linux-tested.com/results/asus_a8r-mvp.html") that tested a similar mobo.
ATI Radeon X300-based 2D/3D: nothing relevant
Realtek ALC880: nothing relevant
Marvell 88E8053: [this]("http://www.linux-tested.com/results/asus_P5LD2-V.html") place said the LAN chipset wasn't recognized and needed to load a driver.

Is there anything else I should have checked?

Thank you in advance for your help!

---

### Post by logos34 on 2006-12-26
[QUOTE=The Iron Curtain;1931454]When i do do i have to buy ATI? I've heard that Nvidea is better, is that true? 

Allegedly, although in my experience it's not so easy to manually install Nvidia's latest official drivers (the one in the repos, on the other hand, goes in easily and works just fine).

Shouldn't have any problems with that board.  Radeon X200 is a very common integrated graphics chipset that has been around for more than a year and half (I almost got an msi board with radeon 200 when it first came out).

The xorg-driver-fglrx in the Ubuntu (restricted) repos should work.

Install instructions are here:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

If you want to get fancy you can try installing the official ATI driver:
[http://ati.amd.com/support/drivers/linux/linux-firegl.html](http://ati.amd.com/support/drivers/linux/linux-firegl.html)

Make sure to carefully read the Readme and install instructions.

Hope that helps you out

---

### Post by The Iron Curtain on 2006-12-26
Thank you! I'm glad that ATI drivers are supported.  I found a bundle deal that has the mobo, CPU and half gig of Kingston RAM, so that was why I wanted to know about it. I hope everything works out.

---

### Post by The Iron Curtain on 2006-12-30
Right. I just found out that ASUS doesn't support that product ... at least under that name. I'll put all the info I found so that future generations might be helped....

Apparently, ASUS supports a barebones set called [Vintage-AH1]("http://support.asus.com/download/download.aspx?SLanguage=en-us&model=Vintage-AH1"). This is the same mobo...but a different name. I honestly don't know If I can/should update the BIOS from that site because it keeps saying it's for Windows. Could someone with more knowledge help me out on this one? I've never updated a BIOS before, so i don't know if it's platform-independent.

Some help I've found was on the [newegg.com user reviews]("http://www.newegg.com/Product/CustratingReview.asp?item=N82E16813131049"). Apparently, SATA has some issues. You can read more about it there. BTW, I've noticed only a few Linux users comment (I think one Ubuntu).

So, I found some help for drivers for the chipsets. If you know of any better ways to get drivers, I'm all ears.
[ Northbridge  ATI Radeon Xpress 200 and  Onboard Video	ATI Radeon X300-based 2D/3D]("https://help.ubuntu.com/community/RadeonDriver") - logos34 kindly pointed me to some Free drivers, and both are supported (X300 3D is experimental). Thanks!
[URL="http://www.nvidia.com/page/uli_drivers.html"]
Southbridge ULi M1573 [/URL] -  Go to Integrated220 (top one). I found this on the newegg review thread. It's proprietary, so if you know of any Open-Source drivers, that would be great. Also, it seems Linux isn't supported for the chip, so once again, I don't know what to do.
Onboard Audio Realtek ALC880 - I found two places to get drivers [URL="http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false"]
realtek site[/URL],   and [Open Drivers]("http://www.opendrivers.com/company/2358/realtek-free-driver-download.html"). I don't know if these are good, but it's what I've found.

As for the LAN chipset Marvell 88E8053 - As per [this place]("http://www.linuxforums.org/forum/linux-networking/38952-marvell-88e8053-driver.html"), I [googled]("http://www.google.com/search?num=100&hl=en&lr=&newwindow=1&safe=off&q=sk98lin+drivers+linux&btnG=Search") for a sk98lin driver and couldn't find anything. However, I ended up [here]("http://www.marvell.com/drivers/driverDisplay.do?dId=153&pId=36") and found a driver.


I hope those are correct drivers and I hope that this will help other people. 

Thank you for your help.

---

### Post by in_flu_ence on 2007-03-12
I have a vintage AH-1 at home. It runs out of the box for me. Even using the 64bit ubuntu. There is of course abit of warning here and there but it doesn't stop the machine to perform. At least to my needs.

If there is a chance to perfecting my machine, i would love to hear that too.

---


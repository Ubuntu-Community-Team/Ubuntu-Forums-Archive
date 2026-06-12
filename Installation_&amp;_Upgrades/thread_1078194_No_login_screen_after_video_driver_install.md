---
title: "No login screen after video driver install"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by dirtydata on 2009-02-23
Hello all!  I hope this finds you doing well ... or at least better than myself at the moment.  Let me begin with a description of my issue.

I have recently upgraded some of my PC components.  Here is a list of my current[new] components:

[Foxconn P45A-S LGA 775 Intel P45 ATX Intel Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813186148")
[Intel Core 2 Duo E8500 Wolfdale 3.16GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115036")
[MSI N9800GT 512OC GeForce 9800 GT 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127387")
[OCZ Fatal1ty Edition 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel Kit Desktop Memory]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227364")
[Antec EA650 650W ATX12V Ver.2.2]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817371015")

The issue: Currently I can install Ubuntu 8.10 [on a side note this exact same issue is happening when I attempt to install Windows 7/Vista 32 or 64 bit] on my machine and it will run as it should.  All the installation process happen as they always have and taking just as long as they should.  Once the install is done and I'm on the Desktop I install JUST the video card driver [I've done this specifically to try and nail down the issue].  Once the driver is installed, I am prompted to restart [this is the same in all OS].  Once I restart the BIOS start the same but once I get past the BIOS I don't see anything [the screen is black].  In Ubuntu, I don't see the first load screen or anything after that [this is the exact same for the other OS I've tried].  

I am assuming the video card is having issues with the motherboard but I currently have no idea what it is.

Any help you can give would be a HUGE help.

Thank you very much for your time.  Have a great day!

-DirtyData

EDIT: I have been thinking about this issue and decided it MIGHT be the power supply.  If someone could take a look at these components to see if they work correctly together, I would GREATLY appreciate it.  I'm thinking that when the driver it loaded for the card it begins to draw more power, but if there is not enough power it may result in the problem I'm having.  Thank you in advance.

---

### Post by Dj TweeX on 2009-02-23
you can try using your old video card, boot & confirm it is the new one.
if it is,
what kind of driver are you using, if its an open source driver try using the restricted driver, if you are installing a restricted driver try using an open source one.
try to completely rule anything else out
let us know how it goes

---

### Post by dirtydata on 2009-02-23
My old video card doesn't work well [it flashes the screen] and that is the reason it was replaced.  When I've done this in windows, I've loaded the driver off the cd and the issue happened.  When I've done this in Ubuntu, I wasn't prompted to put the cd in.  I do believe it prompted me to download nVidia driver 173 [I'm not sure on the number].  There was one that was recommended and one that wasn't.  I choose the recommended one.

-Dirtydata

---

### Post by dirtydata on 2009-02-23
Pleeeaasseee.

-DirtyData

---

### Post by soltanis on 2009-02-24
So your video card works fine with the nv driver, it's the binary driver that screws you over?

Are you sure you installed the card properly? I'd check the physical connections.

Try attaching a $ dmesg | tail as well.

---


---
title: "Video card for an HTPC"
date: 2012-10-14
forum: Hardware
---

### Post by Laucien. on 2012-10-14
Hi!. 

First of all, wasn't sure if this should go here or on the multimedia/video section. 

Right now I have a build that's a Gigabyte GA-E35N for the motherboard with a RADEON HD 6310 as the VGA. I've tried using Ubuntu on a couple occasions but I always have a lot of problems getting the card to output sound through HDMI and enabling the hardware acceleration needed to handle 1080 or even 720 video playback. Last time I tried I managed to fix the sound problem but couldn't get videos to play properly and XBMC even refused to start until I switched to software rendering. 

Was hoping to get help on two points. 
Is anyone running an HTPC setup with that motherboard/vga? is there a way to make it run smoothly or are ATI drivers not that good with that card?. 

I've been thinking about buying a cheap nvidia card to use instead and I'm looking at the low profile XFX GT520 (1gb - DDR3). Would that one work correctly? I've read that nvidia drivers are better supported than the ATI ones. 


Thanks!.

---

### Post by papibe on 2012-10-14
I've set up a couple of HTPC both using Nvidia cards and XBMC. I would recommend an Nvidia card, specially for video acceleration.

Disclaimer: both machines are running 10.04 and I haven't have the time to update them yet.

Regards.

---

### Post by Yellow Pasque on 2012-10-14
For the ATI card, you want to make sure you're using XBMC with xvba support for the best ATI experience: [https://launchpad.net/~wsnipex/+archive/xbmc-xvba](https://launchpad.net/~wsnipex/+archive/xbmc-xvba)

For a new Nvidia card, a GT630 or GT640 would be ideal. You just want to make sure that the one you get is based upon the newer Kepler architecture and is not a rebadged Fermi/GT5x0 card (though those make good HTPC cards too). Unfortunately, you can't tell by just the model number (nvidia likes to confuse consumers to help its resellers get rid of the old stock). Looking at core clock speed is probably the easiest way to tell since vendors usually don't disclose the most detailed technical info. See this page for a guide: [http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units#GeForce_600_Series](http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units#GeForce_600_Series)

---

### Post by Laucien. on 2012-10-14
> **papibe said:**
> I've set up a couple of HTPC both using Nvidia cards and XBMC. I would recommend an Nvidia card, specially for video acceleration.

Disclaimer: both machines are running 10.04 and I haven't have the time to update them yet.

Regards.

Great thanks!. 


> **Temüjin said:**
> For the ATI card, you want to make sure you're using XBMC with xvba support for the best ATI experience: [https://launchpad.net/~wsnipex/+archive/xbmc-xvba](https://launchpad.net/~wsnipex/+archive/xbmc-xvba)

For a new Nvidia card, a GT630 or GT640 would be ideal. You just want to make sure that the one you get is based upon the newer Kepler architecture and is not a rebadged Fermi/GT5x0 card (though those make good HTPC cards too). Unfortunately, you can't tell by just the model number (nvidia likes to confuse consumers to help its resellers get rid of the old stock). Looking at core clock speed is probably the easiest way to tell since vendors usually don't disclose the most detailed technical info. See this page for a guide: [http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units#GeForce_600_Series](http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units#GeForce_600_Series)

I'll give my current setup a try again with the link you posted, maybe I'll get lucky and it works. 

A GT630 is a bit expensive (twice as much as the 520 here in Argentina) and I think it's a bit overkill for a build that will only be used for media. 

Thank you both.

---

### Post by Laucien. on 2012-10-15
It took me a bit to get everything working as it should (for some reason it took me ages to get the apt-add-repository command working) but thanks to the guy Temujin posted I think I got everything working as I wanted. Just played a couple of 1080p music videos and they played smoothly and great. 

Thanks both for your help! :D.

---

### Post by Yellow Pasque on 2012-10-15
You're welcome. Please mark thread solved ("Thread Tools'" menu at top).

---


---
title: "[SOLVED] Best Video Card for Ubuntu Feisty/Gutsy"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by bwethington on 2007-09-27
Hello all;  I have a server at home (AMD x64) that I am going to convert to a desktop for general use around the house.  Currently, it is running Ubuntu 7.04 server and I thinking about putting MythTV on it.  I am also just using the on board VGA for video as I just need video for maintenance when VNC isn't working right.  

But, since I am going to convert to a desktop (and a dual boot because the missus prefers WinXP, but this might be my chance to convert her finally, so I might just run winxp in VMware), I'd like to set up as a dual head machine with a decent video card so I can run a game or two on it with a new 22" widescreen monitor and run better than average video to a larger screen (37" or 42" HDTV).  

With that in mind, does anyone have any recommendations for a video card?  It must be AGP and I have been eyeing this card:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814102071](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102071)

Model
Brand 	SAPPHIRE
Model 	100171L
Interface
Interface 	AGP 4X/8X
Chipset
Chipset Manufacturer 	ATI
GPU 	Radeon X1950PRO
Core clock 	580MHz
PixelPipelines 	12(36 Pixel shader processor)
Memory
Memory Clock 	1400MHz
Memory Size 	512MB
Memory Interface 	256-bit
Memory Type 	GDDR3
3D API
DirectX 	DirectX 9
OpenGL 	OpenGL 2.0
Ports
DVI 	2
TV-Out 	HDTV / S-Video / Composite Out
VIVO 	No
General
Tuner 	None
RAMDAC 	400 MHz
Max Resolution 	2560 x 1600
RoHS Compliant 	Yes
Cooler 	With Fan
Dual-Link DVI Supported 	Yes
Features
HDCP Ready 	Yes
Features 	Anti-Aliasing and Anisotropic Filtering
3Dc+
Avivo Video and Display Engine
________________________________

The thing I don't like about it is that it doesn't have Direct 10x support (but I won't be doing THAT much gaming on it really) or support ShaderModel 3.0...but I don't know that there are many AGP cards that would...plus, it is bit more expensive that I REALLY want to spend.  I could step down to a X1650 (for less than half the cost), but then I don't have dual DVI, which I'd really like to have because I would use this for some of my work 3D modelling as well as watching HD video on the TV.

Any thoughts on how the new ATI open source drivers should/would work with this card and Ubuntu?

Better suggestions from your experiences?  Thanks all.

Edit: Just found this card for a bit less and, from what I can tell, isn't quite as powerful as the one above:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150174](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150174)
 XFX PVT71KUDF3 GeForce 7900GS 256MB 256-bit GDDR3 AGP 4X/8X Video Card

I have ATI on my laptop and got it working with compiz fusion (x1600 Radeon Mobile) finally, so I have no experience with Nvidia and ubuntu.  ATI was a pain the a**.  Would Nvidia be easier to get working properly with dual monitors (ie, twinview, etc.)

brian

---

### Post by w4ett on 2007-09-27
I'd opt for the Nvidia card at this point due to the fact that at present, it has better driver support in linux.  AMD/ATI are moving ahead tho, and are releasing an aiglx capable driver in October.  

Personnaly, I use both ATI and Nvidia, and have good 3D capability with both, but as I said before, I'd opt for the Nvidia.

---

### Post by hessiess on 2007-09-27
nvidia is dead easy to get working;)

---

### Post by Dark Hornet on 2007-09-27
I agree...I had nothing but issues with my ATI card, and eventually bought a nVidia card....everything has been easy with the new card...I have 3D acceleration, and Compiz...life is good.  :guitar:

---

### Post by DarkDancer on 2007-09-27
If what I understand is correct, it won't matter that much that the card won't do dx10 because you will not be able to game with dx10 in XP anyway....

---

### Post by bwethington on 2007-09-28
good point on the DX10 on XP.  If I can convince the missus to stick with Ubuntu, then maybe I won't ever have to "upgrade" to Vista.  

I think I'll stick with the Nvidia card, per everyones input.  Thanks!

---

### Post by w4ett on 2007-09-28
If you are not a gamer, DX10 is a bit of a moot point anyway.

---

### Post by garba on 2007-09-28
i had an old radeon 8500 laying around on gutsy it works wonderfully well with the open source drivers, compiz runs great at 1600x1200

---


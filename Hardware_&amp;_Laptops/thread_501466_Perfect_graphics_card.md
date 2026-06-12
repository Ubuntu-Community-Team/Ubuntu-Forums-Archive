---
title: "Perfect graphics card"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by groeswenphil on 2007-07-15
Hi group,

I'm getting really slow action on video. Maybe its because I have an on-board graphics card.

I think I'll go and spend some money but before I do. can anybody recommend a graphics card that works well with Ubuntu.....one that just works or has Linux drivers available would be nice.

Thanks,
Phil

---

### Post by zek725 on 2007-07-15
nVidia has Linux support.

---

### Post by w4ett on 2007-07-15
Nvidia has the best support, Which specific card depend on your wallet and needs.   What kind of card do you need?   PCI, AGP, PCIe?  

When you decide of the specific card you need,  go to [www.pricewatch.com](www.pricewatch.com) and you'll find all the big web retailers prices (with shipping)

EDIT:  Sorry...didn't notice you are in Wales, all still applies, but pricewatch will be US/Can shipping only.

---

### Post by Ex-Cyber on 2007-07-15
For Linux support (and free OS support in general), the best GPU I know of that's still sold is the Radeon 9250, but that has an AGP interface. I doubt anyone bothered to make a PCIe card with it.

---

### Post by w4ett on 2007-07-15
> **Ex-Cyber said:**
> For Linux support (and free OS support in general), the best GPU I know of that's still sold is the Radeon 9250, but that has an AGP interface. I doubt anyone bothered to make a PCIe card with it.

The 9200/9250 RV280 PCI and AGP cards are no longer supported by ATI, so you have to use the xorg driver.  (I am using one now) and there are a number of bugs with that card  (4 I can remember at this point)
It's well supported in MS Windows, but in Linux, it's seriously lacking.  :frown:

---

### Post by nwadams on 2007-07-15
my nvidia card is well supported i have a 7600 gs, go with nvidia

---

### Post by syadnom on 2007-07-15
> For Linux support (and free OS support in general), the best GPU I know of that's still sold is the Radeon 9250, but that has an AGP interface. I doubt anyone bothered to make a PCIe card with it.

not to be rude here, but all ATI Radeon cards currently have terrible accelerate drivers and not many are well supported by the open source driver.  this is a very well know fact on any linux forum.  the unfortunate truth is that for solid 3D the only really good option is nvidia and their proprietary driver.  i have had some luck with some radeon cards but it is a lot of work and trail and error plus you have to use Xgl to get desktop effects.  I have had really good luck with intel integrated chipsets as far as getting them to work right but the performance is not great but at least they can use AIGXL.  

with ATi and Xgl on a laptop you get a very abreviated usage because Xgl runs the GPU at fully speed and suck battery.  AIGXL seems to be quite a bit more battery freindly.

for reference here, i have a radeon x1400 mobile, radeon 9000 & 9200, radeon 8500, radeon 9700, and a x850 crossfire with an x850 in crossfire mode.  i have successfully configured all of these in linux BUT they were all a hassle and the drivers are buggy and they dont perform anywhere near the windows equivelent drivers.  I also have a geforce ti4400, 600gt,4200 and an 8600gs which all work very easily though i have to install via the alternative installer..

---

### Post by jespdj on 2007-07-16
> **Ex-Cyber said:**
> For Linux support (and free OS support in general), the best GPU I know of that's still sold is the Radeon 9250, but that has an AGP interface. I doubt anyone bothered to make a PCIe card with it.
Where did you get this idea?!
[list]
[*]ATI does not have open source Linux drivers.
[*]ATI's current Linux drivers lack important features which make it hard or impossible to use 3D graphics acceleration.
[*]The 9250 is a very old card. It is not supported by ATI anymore and compared to current GPU's it is SLOW. It is most likely slower than the onboard graphics chip that the original poster uses.
[/list]
Getting an ATI Radeon 9250 is not a good idea, this will not help you to get fast 3D accelerated graphics. Forget about ATI if you want good graphics support for Linux. Actually Intel is the only company that has open source graphics drivers (as far as I know) but Intel graphics cards are not as powerful as ATI or nVidia cards. nVidia's drivers are proprietary, but at least they are a lot better than ATI's drivers.

The best choice for graphics under Linux is currently nVidia.

---

### Post by misfitpierce on 2007-07-16
Yeah some day ATI will get their s*** together and bring out good drivers but until then nvidia is better... hurts me to say that too :(

---

### Post by jespdj on 2007-07-16
Actually, in May I read a news article somewhere in which some director of ATI was interviewed, and he explained that they are currently working on a whole new set of video drivers for Vista as well as Linux. The support for 3D graphics for ATI videocards should become much better when these drivers are ready.

But they didn't say anything about when this would be... So for now, better not get an ATI card if you want good OpenGL support on Linux.

---


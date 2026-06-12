---
title: "ATI Drivers on a dell Latitude D531"
date: 2010-02-04
forum: Hardware
---

### Post by cormon on 2010-02-04
Hi Guys,

Just installed ubuntu 9.10 on a ATI Drivers on a dell Latitude D531. I am trying to activate either the flgrx driver or any other options really.

My video card details are 

pci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series].

When I try and download the drivers from the AMD site my card is not listed there is a 1250 and 1300 card but not for 1200. ( typical amd fingers up to open source )

I tried to install via ENVYNG but the driver was not recommended or supported in the list and cause a reinstall of the OS as the screen when haywire.

the output of a fglrx command  is

 fglrxinfo
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Segmentation fault.

Any ideas as to what the best option is ????.

Thanks

---

### Post by Yellow Pasque on 2010-02-05
The best option is to use the pre-installed open-source ati driver because it's your only option. In fact, you made things worse and you should purge the proprietary driver off if you tried to install it: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

> typical amd fingers up to open source
Actually, AMD is moving from proprietary(fglrx) to open-source drivers on Linux, which is why they stopped supporting legacy devices like yours in Catalyst/fglrx.

---

### Post by waynefoutz on 2010-02-11
> **cormon said:**
> Hi Guys,

Just installed ubuntu 9.10 on a ATI Drivers on a dell Latitude D531. I am trying to activate either the flgrx driver or any other options really.

My video card details are 

pci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series].

When I try and download the drivers from the AMD site my card is not listed there is a 1250 and 1300 card but not for 1200. ( typical amd fingers up to open source )

I tried to install via ENVYNG but the driver was not recommended or supported in the list and cause a reinstall of the OS as the screen when haywire.

the output of a fglrx command  is

 fglrxinfo
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Segmentation fault.

Any ideas as to what the best option is ????.

Thanks


Corman. i have that laptop. The best option I've found is to stick with 8.10, Intrepid Ibex, and install ATI's catalyst 9.3 on it. You should get everything working. Wifi and everything works out of the box on intrepid. When you get to 9.10 and above, it starts breaking things.. The last ATI closed source driver that works with the ATI X1270 is 9.3, which will not run on Jaunty or later. So you are stuck with open source. The open source drivers will work, will give you some desktop effects, but no 3d what so ever. Google earth will not run for example. With Intrepid and Catalyst 9.3, everything works perfectly. 

They were claiming that the newest 2.6.32 kernel would give us 3d, but so far I haven't seen it. If 3d isn't important to you, just Install the latest build 9.10, and you'll get 2d and desktop effects out of the box.

---

### Post by waynefoutz on 2010-12-14
> **waynefoutz said:**
> Corman. i have that laptop. The best option I've found is to stick with 8.10, Intrepid Ibex, and install ATI's catalyst 9.3 on it. You should get everything working. Wifi and everything works out of the box on intrepid. When you get to 9.10 and above, it starts breaking things.. The last ATI closed source driver that works with the ATI X1270 is 9.3, which will not run on Jaunty or later. So you are stuck with open source. The open source drivers will work, will give you some desktop effects, but no 3d what so ever. Google earth will not run for example. With Intrepid and Catalyst 9.3, everything works perfectly. 

They were claiming that the newest 2.6.32 kernel would give us 3d, but so far I haven't seen it. If 3d isn't important to you, just Install the latest build 9.10, and you'll get 2d and desktop effects out of the box.

To anyone revisiting this thread, I now have Lucid, 10.04, running flawlessly with full 3d. OpenGL games or Google Earth did not work out of the box, but adding the PPA from [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") fixed everything. At this point in time, 10.10 is the current latest version of Ubuntu, and it runs sluggish on this laptop with 2 gigs of ram. I ended up going back to 10.04. The open source drivers are all grown up now. You just need to  add the xorg-edgers PPA to get the latest version.

---


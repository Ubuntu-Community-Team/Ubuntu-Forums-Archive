---
title: "Ubuntu 9.04 and ATI Mobility Radeon X1600"
date: 2009-05-26
forum: Hardware
---

### Post by bdw on 2009-05-26
I just upgraded to 9.04 from 8.04 and it appears that the fglrx driver is not compatible with ATI Mobility Radeon X1600.  It will freeze with a corrupted display.

I did try to install the driver for the ATI Mobility Radeon X1600, version 9.3 released 3/26/2009.  It doesn't appear to be compatible with Jaunty as I get the following error when installing:

```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-12-generic; make sure that the version is being
correctly set by --iscurrentdistro
```

The 9.2 release also generates the same error.

Is this a compatibility issue with the 1.6 Xserver?

Video info from lspci:
```
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
```

---

### Post by rizman on 2009-05-26
> Is this a compatibility issue with the 1.6 Xserver?

Indeed. As of catalyst drivers 9.4, older (some are apparently not even a year old) graphics cards are no longer supported, including your X1600.
See here for a complete list: [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.17&lang=English&rev=9.3&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.17&lang=English&rev=9.3&ostype=Linux%20x86)

Unfortunately, Xserver 1.6 does not support older catalyst drivers. So you are bound to either using the open-source ATI drivers, or revert back to Intrepid/Hardy.

---

### Post by bdw on 2009-05-26
Many thanks for the heads up on this - I did see on other forums that the X1600 was being phased out, interesting that graphics cards not quite a year old are no longer being supported.

Jaunty works just fine with the open source drivers, Google Earth works but not Streetview or other 3D functions.  Desktop effects are very sluggish.  Hibernation works perfectly and the system does seem more responsive.

This is one of the hazards with laptops, you can't replace the graphics card as easily as you can with with a desktop system.

I think I'll limp along with what I have untill I afford a new laptop, looks like I may go with System76.

---

### Post by zgornel on 2009-05-26
> **bdw said:**
> Many thanks for the heads up on this - I did see on other forums that the X1600 was being phased out, interesting that graphics cards not quite a year old are no longer being supported.

Jaunty works just fine with the open source drivers, Google Earth works but not Streetview or other 3D functions.  Desktop effects are very sluggish.  Hibernation works perfectly and the system does seem more responsive.

This is one of the hazards with laptops, you can't replace the graphics card as easily as you can with with a desktop system.

I think I'll limp along with what I have untill I afford a new laptop, looks like I may go with System76.

Strange that effects are sluggish, the x1600 should handle them without any problem. You can try a live cd and see if it is an upgrade-related problem or with driver/compiz.

---

### Post by seijling on 2009-07-07
How would one then un-install said discontinued drivers?  

I was running generic mesa drivers with my x1600 and it worked reasonably well. when I decided to connect another display, I noticed I needed to install ATI fglrx drivers and the Catalyst control center.

Now the display is corrupted due to incompatibilities and I'm not sure how to reconfigure it to use the generic mesa drivers.

I tried etc/X11/xorg.conf but it appears that file/configuration has become vestigial.  Is there another configuration file I can modify?

Seijling

---

### Post by GnuSense on 2009-07-11
seigling, have a look here to uninstall fglrx and re-enable the open source driver:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by seijling on 2009-07-12
Wicked response - shall do.  

Thank you!

Seijling

---

### Post by yirgen on 2009-07-20
Hello forums and everyone! :)
 
Can I still use the above solution if I have a clean install of Xubuntu Jaunty Jackalope? 
I have the ATI x1600 Mobility on a HP nx9420 (pieace of crap) laptop. 
 
And correct me if I'm wrong, but can I then use Compiz with it's effetcs?
 
Or is there another way to revert back, enabling cool desktop features with Compiz?
 
Thanks in advance!
 
):P

---

### Post by seijling on 2009-07-20
Hey Yirgen,

To be honest, I didn't try this after all - I simply did a fresh install (it was time anyway) so it was worth it.

At any rate, compiz, its effects and "configurability" seems unaffected on my x1600 except for something quite strange it does AND did a long time ago when fglrx drivers were marginally available for ubuntu (6.04):  The card literally squeaks when under load. 

i.e. The card when utilizing GL features (I guess) actually makes a high pitched squeaking noise at the frequency of my fps. (Frames per second) 

It not terrible enough to change, but it is noticeable. And in fairness, I have noticed my laptop running quite a bit cooler on the generic drivers anyway. 

The only negative is the multiple screen management with is now handled through Ubuntu directly. 

Hope this helps,

Seijling

---

### Post by winz on 2009-07-22
> **seijling said:**
> At any rate, compiz, its effects and "configurability" seems unaffected on my x1600 except for something quite strange it does AND did a long time ago when fglrx drivers were marginally available for ubuntu (6.04):  The card literally squeaks when under load. 

i.e. The card when utilizing GL features (I guess) actually makes a high pitched squeaking noise at the frequency of my fps. (Frames per second)

Same here. ATI Mobility Radeon X1600, Acer TravelMate 8204WLMi - squeaking noise when doing something like minimizing/maximizing windows, or opening a web page with an animation banner etc.

---

### Post by GnuSense on 2009-07-24
Yirgen, I believe your card is supported by the open source Radeon driver and apparently has decent 3D support.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Anything that can run the radeon driver will do 3D, AFAIK.  I have some first generation Radeon 7000 cards tat will handle compiz, albeit not very gracefully.  But enough to demonstrate the technology.

---

### Post by yoszik on 2009-08-22
> **GnuSense said:**
> Yirgen, I believe your card is supported by the open source Radeon driver and apparently has decent 3D support.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Anything that can run the radeon driver will do 3D, AFAIK.  I have some first generation Radeon 7000 cards tat will handle compiz, albeit not very gracefully.  But enough to demonstrate the technology.

Demonstration without ability to use it is nothing!!!

---

### Post by winz on 2009-11-06
No strange noise after upgrade to 9.10. Also, X1600 performs much much better now!

---


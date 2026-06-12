---
title: "No Video drivers"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by zoomiest on 2008-01-30
I just loaded Xubuntu, and found that out of the box, wide screens are not supported.

the motherboard manufacturer (onboard video) doesn't have any Linux drivers at all. (GIGABYTE).

Do I have any other options? (other than live with a stretched screen?)

The LCD is an LG.

---

### Post by oldsoundguy on 2008-01-30
Yes .. blow the onboard video off and install an nVida card.  Works for me! (use generic drivers first and then get the third party program Envy to do the install.)

---

### Post by Yellow Pasque on 2008-01-30
The last time I checked, Gigabyte doesn't make video chipsets. So the question is, what kind of video chipset do you have? Run this for me and post the output:
```
sudo update-pciids; lspci | grep VGA
```

> Yes .. blow the onboard video off and install an nVida card. Works for me!
Maybe it will come to that, but first, one should exhaust other options that don't waste hard-earned coin or good electronics.

---

### Post by zoomiest on 2008-01-31
Thanks for the help. I ran that and came up with

```


--15:46:23--  http://pciids.sourceforge.net/v2.2/pci.ids.bz2
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 129,871 (127K) [text/plain]

100%[====================================>] 129,871      205.32K/s             

15:46:24 (204.82 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [129871/129871]

Done.
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

```

---

### Post by Yellow Pasque on 2008-01-31
Ok, now we're getting somewhere.
```
sudo apt-get install xserver-xorg-video-unichrome
```
Now you have a video driver. Run the following command and select the unichrome driver. Hopefully, this will get you to the point where you can use the Screens & Graphics applet to get the resolutions you need.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Duncan Pierce on 2008-02-10
I've been struggling to get a decent graphics driver installed for 2 days now. I'm stuck on 800x600 VESA drivers with a 1920x1200 LCD :-(

I've tried the above (and many other suggested fixes) but don't see Unichrome driver in the list. (I tried to get the Openchrome driver to work and didn't see that either).

Any idea what I might be missing here?

---

### Post by oldsoundguy on 2008-02-10
Yes, what is missing is co-operation between the video chip maker and the open source community.  When some piece of hardware does not work, there is a very good chance that the job of  "reverse engineering" has missed something very proprietary.  It is a common problem and, without co-operation from the manufacturer of the hardware, a LONG process to figure out.

The hardware compatibility list is a valid list.  as is the INCOMPATIBILITY list.

Some stuff just ain't ready for prime time unless you are into dinkning with it until blue in the face.

Nobody involved in Linux is going to be able to buy a campus on Lake Washington, so they just cant counter the greasing of the palms of CEO's to keep their stuff out of open source's hands!

---

### Post by Yellow Pasque on 2008-02-10
> **Duncan Pierce said:**
> I've been struggling to get a decent graphics driver installed for 2 days now. I'm stuck on 800x600 VESA drivers with a 1920x1200 LCD :-(

I've tried the above (and many other suggested fixes) but don't see Unichrome driver in the list. (I tried to get the Openchrome driver to work and didn't see that either).

Any idea what I might be missing here?
[http://packages.ubuntu.com/gutsy/x11/xserver-xorg-video-unichrome](http://packages.ubuntu.com/gutsy/x11/xserver-xorg-video-unichrome)

---


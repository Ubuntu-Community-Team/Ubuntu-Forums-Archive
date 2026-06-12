---
title: "Radeon 7870 Drivers"
date: 2013-07-02
forum: Hardware
---

### Post by Penguinnerd on 2013-07-02
Hello all,

I would typically use Debian Testing, but network connectivity issues are preventing me from installing it onto my new PC. Netinstall keeps getting messed up by the intermittent connection.
The internet connectivity situation is beyond my control, and the landlady won't do anything about it.
So I'm here, just wanting to get proper drivers installed to test my new hardware before it's too late to return anything that might fail. (Thank you, LiveCD installer!)

My video card is a Radeon 7870, on an asrock FX-990 extreme9 board with a Vishera 8350 CPU.

I have installed Ubuntu 12.04 from a live CD a few times, and due to my network issues, the updates each time take ages. I'd rather not redo this too many more times.
I have been installing the 32-bit version as it's what I already had a copy of. I might try downloading the 64 bit one, but I'd just like to test my hardware and worry about installing my prefered OS later. The network issues would make it difficult to get the 64-bit version.

I was just wondering if anyone has recently installed drivers for this card in 12.04, and what method you used to make it work.
I have tried the drivers utility that comes with Ubuntu, but it dod not seem to make a difference. Plus, the general understanding seems to be that it's a good idea to get the latest ones directly from AMD.

I went here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)
And installed the "latest beta driver", version 13.6, and my system would no longer boot.

Next I'll try the 13.4 driver listed at that page. While I wait for that to finish, does anyone have suggestions?

---

### Post by Yellow Pasque on 2013-07-03
If you're going to install Catalyst manually on Ubuntu 12.04, you should use this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

I'm not sure what went wrong with the beta driver, but it may have been something as simple as not running amdconfig.

---

### Post by Penguinnerd on 2013-07-03
I followed those instructions, and got to the part where I test the installation. The output for fglrxinfo was:

display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7800 Series
OpenGL version string: 4.2.12217 Compatibility Profile Context 12.104

The instructions say that the vendor line should reference ATI. Mine references AMD. I known AMD owns ATI, but does that mean it worked?
What is another way to test it, other than downloading a demanding game to run?

---

### Post by Yellow Pasque on 2013-07-03
Yes, AMD == ATI, that's fine.
I think this command still exists:
```
fgl_glxgears
```

---

### Post by Penguinnerd on 2013-07-03
I get about 480 fps at fullscreen 1080p.
That seems decent, but is it what I should expect? I have seen much higher framerates posted from this program.

---

### Post by Penguinnerd on 2013-07-03
Well, I downloaded a few games on steam and it seems to be working. "Don't Starve" works great, and "Portal" only slows down while it is still loading.
Thank you for your advice.

---


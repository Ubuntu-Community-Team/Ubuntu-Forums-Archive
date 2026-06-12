---
title: "Problem with ati and fglrx drivers on Dapper: is there an alternative to VESA?"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by antartida on 2007-01-23
I'm running Ubuntu Dapper 6.06 (2.6.15-23-386) on an Acer Aspire 5050 with ATI Radeon Xpress 1100. The ATI driver provided by Ubuntu causes the since the first boot X server to crash (giving messages of "insufficient memory when loading the module) so I must  edit xorg.conf to substitute "ati" with "vesa" in the device section. 

I tried with with the last version of fglrx (ati-driver-installer-8.32.5-x86.x86_64) and the HOW TO I found here:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

But still the same problem.

I will very much appreciate some help in this issue.

---

### Post by Stemp on 2007-01-23
I'm not sure but I think the X1100 is a X200M so you should try the [ATI Radeon/Ati Driver]("https://help.ubuntu.com/community/RadeonDriver")
But no 3D Hardware acceleration.

---

### Post by antartida on 2007-01-23
In fact, the "device" section in my xorg.conf says:

[I]Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"[/I]

Thanks for the link. I will try that.

:)

---

### Post by antartida on 2007-01-23
oh, no!  

I've taken a look at the HOW-TO. I'm affraid it's only for Edgy ](*,)

The *libgl1-mesa-glx* library is not available for Dapper. Is there a new version of the ATI-RADEON driver that could work on my Dapper (taking into account that the version provided crashes the X server)?

For me, it would be enough if I could set the screen resolution to 1200X800 even with VESA...:(

---

### Post by Stemp on 2007-01-23
Are you sure ? 
Your card is a RV370 not far away from my ATI 9600 rv350.

---

### Post by antartida on 2007-01-24
quite sure unfortunately...

if you search *libgl1-mesa-glx* in [packages.ubuntu.com]("http://packages.ubuntu.com") you won't get nothing under Dapper unless you select Edgy.

and the rest of the needed libs are already installed in Dapper, so I am basically repeating the same initial experiment with ATI driver that lead me here... :(

---

### Post by prof818 on 2007-01-24
Well, I have the same problem as you.   Have you done an apt-get update?  Because its actually better to keep the old x server ( cant remember the version, just not anything 7.1 and greater)   Mine seems to work, although I havent had a chance to test it, properly.

---


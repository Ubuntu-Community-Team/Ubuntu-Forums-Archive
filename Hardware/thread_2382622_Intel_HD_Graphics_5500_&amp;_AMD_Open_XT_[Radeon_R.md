---
title: "Intel HD Graphics 5500 &amp; AMD Open XT [Radeon R7 M265]"
date: 2018-01-15
forum: Hardware
---

### Post by advancecoder on 2018-01-15
Hi,

How do I install the HWE stack on Ubuntu 17.04 for the hybrid chip combination of Intel HD Graphics 5500 & AMD Open XT [Radeon R7 M265]?  

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[COLOR=#333333][FONT=monospace] sudo apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04
[/FONT][/COLOR][COLOR=#333333][FONT=monospace] sudo apt-get install --install-recommends linux-generic-hwe-17.04 xserver-xorg-hwe-17.04[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace][FONT=arial]
The command(s) won't work above.  What should I do?[/FONT][/FONT][/COLOR]

---

### Post by Yellow Pasque on 2018-01-15
If you're on 17.04, you do not have HWE's. Only LTS releases (like 16.04 and 18.04) have HWE's.

Give output of:
```
xrandr --listproviders
glxinfo | grep string
DRI_PRIME=1 glxinfo | grep string
```

---

### Post by Bashing-om on 2018-01-15
advancecoder; Ouch ! 17.04 !

I hate to be that harbinger of ill news, but ->

> 
Ubuntu 17.04 (Zesty Zapus) was the 26th release of Ubuntu. Support ended on January 13th, 2017. See !eol and 
               !eolupgrade


Strongly advised to upgrade to a supported release - asap before the 17.04 repo is turned off .


[INDENT][INDENT]all good things must end
[/INDENT][/INDENT]

---

### Post by DuckHook on 2018-01-15
> **Bashing-om said:**
> advancecoder; Ouch ! 17.04 !…Strongly advised to upgrade to a supported release - asap before the 17.04 repo is turned off…
&#8593;&#8593;&#8593;&#8593;&#8593;+

I believe that users are given a grace period of approximately one month, but yes, the repos are eventually retired and moved. This means mid-February. Patching and security updates stop on the EoL date. No grace period at all for those. That means in two days.

With the recent flurry of upgrades for Meltdown and Spectre, you ***do not*** want to be running obsolete kernels.

---


---
title: "Can't Detect Wacom Bamboo Pen Connect"
date: 2011-12-25
forum: Hardware
---

### Post by ServerStorm on 2011-12-25
Hi,

I have been working all day trying to get a Wacom Bamboo Pen Connect graphics tablet working form my son.

I have had little to no success to date.

These are the things that I have tried.

[LIST=1]
[*]Making input-wacom-0.12.1
[*]Manually compiling linuxwacom-0.9.0 driver
[*] Followed this "[http://ubuntuforums.org/showthread.php?t=1038949]("http://ubuntuforums.org/showthread.php?t=1038949")" post carefully and used Git-Clone Method and resolved all missing dependancies.
[/LIST]

Tried:
Manually compiling linuxwacom-0.9.0 driver

Used Git-Clone Method of "" post and resolved all missing dependancies.

I upgraded my kernel and am using Linux version 2.6.35-22-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010

It is not getting detected as xinput list shows:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
```

In Synaptic I also tried installing:
- xserver-xorg-input-wacom
- wacom-dkms
- wacom-utility

Can you help resolve detecting this tablet? 

Many happy Holiday returns to you and your family!

---

### Post by Favux on 2011-12-25
Hi ServerStorm,

The linuxwacom-0.9.0 driver does not have your model in it.  Making input-wacom-0.12.1 [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949) would have worked if you had Natty (the 2.6.38 kernel) or higher.

The packages you installed through Synaptic are too old and wacom-dkms especially is a problem if you were in Natty or higher instead of Maverick.  That's because the dkms wacom.ko, which is too old, would overwrite any new wacom.ko, that had your Pen, you compiled.  So you would have had to remove it through Synaptic anyway.

See the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") for an explanation and instructions.  The basic problem is that Chris just added his 3.3 kernel support for the third generation BambooPTs to input-wacom-0.12.0, and it only works for the 2.6.38 kernel or later because it is the first kernel to have the mt.h (multi-touch header).  Chris has no plan to further backport support for the third generation BambooPTs or the second BambooPT's touch to kernels before 2.6.38.  That's because it would be a lot of work and touch for the models that have it wouldn't work well anyway.  So you can't get your model working in Lucid or Maverick.  Sorry.

Happy Holidays to you.

Favux

---

### Post by ServerStorm on 2011-12-25
Hi Favux,

Thank you for your concise post and your many _expert_ posts in the ubuntu forums, you are a champ!

I will have to upgrade my sons distro then.

Thanks
Steve

---

### Post by ServerStorm on 2011-12-27
Hi,

Just reporting that The Bamboo Pen Connect tablet works perfectly on an AMD 64 bit Ubuntu 11.10.

After upgrading my Son's OS to Ubuntu 11.10.1, I followed the instructions on the [HOW TO Set Up the Bamboo Pen & Touch in Lucid]("http://ubuntuforums.org/showthread.php?t=1515562") thread, using steps I & II - I did not need to do any configuration like in step III

MyPaint, Inkscape, and the version of GIMP you point to in the aforementioned post work great!

Again thanks for all the hard workers that give so much to the Ubuntu/Linux community!

Regards,
Steve

---


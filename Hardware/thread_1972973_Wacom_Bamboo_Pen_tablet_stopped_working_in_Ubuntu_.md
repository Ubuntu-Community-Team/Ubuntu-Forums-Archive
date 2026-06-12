---
title: "Wacom Bamboo Pen tablet stopped working in Ubuntu 11.10"
date: 2012-05-04
forum: Hardware
---

### Post by chickendude on 2012-05-04
I had my tablet working great for several months without a problem, but all of a sudden it isn't recognized anymore. The tablet lights up when plugged in and reacts (the light gets brighter) when i bring the pen close to the tablet, but it doesn't move the mouse. The only thing i can really think of having down is installing some system updates and playing around with the Compiz settings.

I don't know if any of this information will be useful, but here it is just in case:
> $ lsusb | grep Wacom
Bus 002 Device 005: ID 056a:00dd Wacom Co., Ltd 
> $ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; WebCam SCB-0385N                        	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

Thanks :)

---

### Post by Favux on 2012-05-04
Hi chickendude,

It depends how you got the DD working in the first place.  The third generation BambooPT tablets have support in the 3.3 kernel.  So to have gotten it working in Oneiric's 3.0 kernel you must have compiled input-wacom.  Input-wacom supplies an updated wacom.ko (the kernel driver/module) i.e. patches backported from later kernels.  Your model is supported by input-wacom in Oneiric.

Was the kernel updated?  That will "break" things because it will contain the old non-working wacom.ko, not the one you compiled.  You have to recompile or use a dkms setup.

The [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") shows you how to compile input-wacom (now at 0.13.0) in part I. and just before that is a link to a PPA that installs input-wacom-0.12.1 in a dkms package.  Also near the top is a look at the various models and how to get them working.

---

### Post by chickendude on 2012-05-04
Great! Thanks! Yeah, i believe i had updated the kernel at some  point. I had installed it before (i think) from Lekensteyn's ppa and had the 0.12.1 version installed, so i decided just to try installing the 0.13.0 version. I had a little trouble getting it to install as there wasn't any config file, but running the autogen script worked like a charm, a reboot later and everything's working great!

I've seen your name in pretty much every single thread related to the tablets, thanks for all the help you've given me and everyone else. I really appreciate it!

---


---
title: "Acer aspire 9920 sound"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by Dark-archon on 2008-03-16
I've just installed gutsy on my new laptop (aspire 9920) , got almost everything working
but no sound ... 

  > sudo lshw |grep -i Audio

output : 

> SCSI                      
       slot: HD-Audio
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram


> lspci 

output : 

> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

>  modinfo soundcore

output : 
> filename:       /lib/modules/2.6.22-14-generic/updates/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.22-14-generic SMP mod_unload 586 

i've tried compiling the newest alsa with hda-intel driver but no luck

any help would be appreciated,

D-A

---

### Post by Yellow Pasque on 2008-03-16
Try these scripts for building latest alsa.
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

You might want to also try congfiguring alsa-base to use model=acer or model=lenovo (yes,  I've seen the lenovo option work on non-lenovo laptops) [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

If none of that works, you could always try OSS4 (link in sig). Their HDA driver usually works well IIRC, except that it sometimes doesn't do jack sensing properly.

---

### Post by Dark-archon on 2008-03-22
alsa didn't work 
but OSS4 works perfectly :)  (no jack sensing though)
thanks 

:guitar:

---

### Post by Yellow Pasque on 2008-03-22
> (no jack sensing though)
Yeah, it was one of my suggestions for anyone looking to contribute to their Google Summer of Code Project. Glad to hear you got sound.

---


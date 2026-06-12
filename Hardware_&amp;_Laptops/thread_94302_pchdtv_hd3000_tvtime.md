---
title: "pchdtv hd3000 tvtime"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by dguido on 2005-11-23
I'm trying to get my HD-3000 card to work and can't seem to do it right.  I just switched here from Gentoo where I was stuck at the same place.  Breezy seems to have installed all the neccessary drivers for me already, so I just installed tvtime (with broadcast and NTSC) and scanned for channels.  What I get are 3 spanish channels that all look analog instead of digital HD (I think the hd3000 has both an analog and digital tuner).

I don't want MythTV at the moment, I'd just like to watch HDTV.

EDIT: I guess I should also be asking whether TVtime can even do ATSC

---

### Post by dguido on 2005-11-23
I got dtvscan from the tools archive on pchdtv's website ([http://www.pchdtv.com](http://www.pchdtv.com)) and ran dtvscan but it gives me an error:
No such file or directory - couldnt open file /dev/dtv

I'm trying to follow this [http://www.penlug.org/twiki/bin/view/Main/DigitalTelevision](http://www.penlug.org/twiki/bin/view/Main/DigitalTelevision) to get it to work with xine.

---

### Post by tman on 2005-11-29
dguido,

I am also trying to get the HD-XINE package working on Ubuntu with my HD3000 card.  The card is recognized and the device files adaptor0, adaptor1, etc. are setup.  The default for the dtvscan is /dev/dtv.  This dev node was not setup.  I have tried to set it up as a character device with different major and minor numbers.  No luck.  The bigger issue for me is trying to get the XINE library package and application compiled.  Since gcc 4.0 came along, the compilation restrictions are much tighter.  I know of no other application that will display true HD resolution.  If there is another already working on ubuntu that would be great.

Thanks
TMan (H)

---


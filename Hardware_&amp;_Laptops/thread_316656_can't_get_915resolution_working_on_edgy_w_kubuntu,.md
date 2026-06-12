---
title: "can't get 915resolution working on edgy w/ kubuntu, tried almost everything   :("
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by jongt on 2006-12-11
ok, I used adept to get 915resolution, and I changed /etc/default/915resolution, its listed below.  I added a new modeline to my monitor section, and modes to the display subsections.  ive tried just about every config with my xorg.conf, including only one depth, multiple depths(1,4,8,16,24,32), along with one resolution, 1280x768 and multiple resolutions. in my current xorg.conf, ive commented out every resolution other than 1280x768, and it still loads into 1024x768.  im on intel 945gm chipset, laptop with native resolution 1280x768.  help appreciated.  xorg.conf and Xorg.0.log are both below as well

xorg.conf -- i know the refresh rates may not be right, i used gtf, but it was doing this long before i had added that modeline.
[http://paste.uni.cc/12122](http://paste.uni.cc/12122)

Xorg.0.log
[http://phpfi.com/183697](http://phpfi.com/183697)



# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=61
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1280
YRESO=768
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
#BIT=32

---

### Post by jsc1328 on 2006-12-12
What is the output of "915resolution -l"?

---


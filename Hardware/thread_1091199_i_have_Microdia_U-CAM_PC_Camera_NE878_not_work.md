---
title: "i have Microdia U-CAM PC Camera NE878 not work"
date: 2009-03-09
forum: Hardware
---

### Post by sfareg on 2009-03-09
[B][COLOR="DarkRed"][SIZE="5"][CENTER]i have web cam 
Microdia U-CAM PC Camera NE878
i want install this drive [/CENTER][/SIZE][/COLOR][/B]

---

### Post by joejoseph00 on 2009-11-11
> **sfareg said:**
> [B][COLOR="DarkRed"][SIZE="5"][CENTER]i have web cam 
Microdia U-CAM PC Camera NE878
i want install this drive [/CENTER][/SIZE][/COLOR][/B]

Please read:
A) Execute the following command 

    #lsusb

If you see any of the following numbers, you have a "microdia" webcam

0c45:6240 0c45:6242 0c45:6243 0c45:6248 0c45:624b 0c45:624c 0c45:624e 0c45:624f 0c45:6253 0c45:6260 0c45:6262 0c45:6270 0c45:627a  0c45:627b 0c45:627c 0c45:627f 0c45:6280 0c45:6282 0c45:6283 0c45:6288 0c45:628a 0c45:628b 0c45:628e 0c45:628f 0c45:62a0 0c45:62b0 0c45:62b3 0c45:62ba 0c45:62bb 0c45:62bc 0c45:62be

(basically 0c45:<xxxy> above is enough to conclude you have a microdia webcam) 


Q>How do I install Microdia Webcam Driver? go here: 
[http://groups.google.ca/group/microdia/web/testing-microdia-driver-draft](http://groups.google.ca/group/microdia/web/testing-microdia-driver-draft)

it's still experimental but you can try it.  It is probably a lot easier (and cheaper) to buy a better supported webcam such as one listed in the gspca compatibility list but you can always try the experimental driver.  I recommend buying a supported webcam listed at mxhaard.free.fr/spca5xx.html .

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
another list showing various webcam support levels below:
[http://www.kaiser-linux.li/index.php/Linux_and_Webcams](http://www.kaiser-linux.li/index.php/Linux_and_Webcams)


Unfortunately if you're like me and have a built-in webcam on your laptop then throw your laptop under a bus and buy a DELL laptop with Linux installed from Dell.  For now I've decided to keep my vestigally equiped laptop and buy a supported webcam for $10 off e-bay that works properly.  It's cheaper than replacing my laptop, however I am looking to replace my laptop with a factory supported Dell with factory installed Linux.  Just look at Mac, they only support a small amount of hardware but they do it well and their customers are happy to pay lots of money.  If you buy good supported hardware it is worth the extra money.

---

### Post by forkandles on 2009-11-23
You could try having a look at this link:

[http://ubuntuforums.org/showthread.php?t=1137793](http://ubuntuforums.org/showthread.php?t=1137793)

Alternatively, if you think life is just too short to waste time on your Microdia, do yourself a BIG favour and buy a cheap Linux compatible webcam.

I can recommend the Logitech Quickcam E3500 or E3500 Plus (includes stereo headset) for use with Ubuntu 9.10. The E3500 works out of the box with Skype with one minor tweak.
Make sure the speaker symbol in the Ubuntu top toolbar is not muted.
Also using the same icon, set the Sound Preferences correctly, making sure the Input Volume is also not muted.


[http://www.play.com/Product.aspx?r=P...57&source=9593](http://www.play.com/Product.aspx?r=P...57&source=9593)

---


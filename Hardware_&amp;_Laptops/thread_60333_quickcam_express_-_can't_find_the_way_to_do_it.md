---
title: "quickcam express - can't find the way to do it"
date: 2005-08-27
forum: Hardware &amp; Laptops
---

### Post by yhotg on 2005-08-27
Hi, 
how the title of the thread says i have quickcam express;
kubuntu hoary (working very very very nice and smoothhhhh lol)
but i can't get the webcam working
I installed , with apt-get : 
qcam,
qce-source,
qc-usb-source,
qc-usb-utils.

then i , well tried to install, the source of:
sqcam for kernel 2.6.etc
qce-source
qc-usb
qc-ga-etc

i got it almost right, 
i use the ./quickcam.sh
and all went fine till the script needs to detect the device, and there it says it can't detect no device, and of course no program cam see the cam.
on the kinfocenter in usb device i can see connected the quickcam express with all the data:

QuickCam Express

Class             255             (Vendor Specific Class)
Subclass       0
Protocol        0
USB Version  1.10

Vendor ID      0x46d          (Logitech, Inc.)
Product ID     0x920          (QuickCam Express)
Revision         0.01

Speed            12 Mbit/s
Channels       0
Max. Packet Size              0


so.... I don't know what to do
i looked every place i could think of  for "how-tos". i read the post here etc etc
(right now i have a problem while doing searchs on the forum, i get an error message...  :-? )

so, I hope there's somebody that can explain to me in a very very easy - step by step - way what to do to get the webcam working. 
thank u very much 
yhotg

pd: i want to say that there r 3 reasons why i can't make the full change to linux:
1. the webcam not working (needed to talk with the family on the other side of the ocean)
2. clamav not auto-running because i can't get dazuko working neither.
3. i couldn't find a how-to to easy scripts (like to make a button for my wife to get connected/disconnected to/from internet without having to do nothing else, no pass, no nothing. just clicking)
and i am so feeded up of xp  :? 

well thank u

---

### Post by yhotg on 2005-08-29
Well i found a way!!!
 \\:D/ 

I found this thread-------> [http://ubuntuforums.org/showthread.php?t=55482&highlight=quickcam](http://ubuntuforums.org/showthread.php?t=55482&highlight=quickcam)
that linked here -------------> [http://home.mag.cx/messenger/](http://home.mag.cx/messenger/)
and from there went to --------------> [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)
that said that this was the way to go ----------------> [http://home.tiscali.dk/tomasgc/labtec/](http://home.tiscali.dk/tomasgc/labtec/)

and there i found this file 
" [COLOR=Teal]spca5xx-20050701.tar.gz[/COLOR] "  that I downloaded
from here: [COLOR=DarkOrange][http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)[/COLOR]

extracted it, 
did make and make install
and as root: modprobe spca5xx
since then i have webcam  :-P 

the colors are wrong, the definition is horrible but i got webcam working!!!!
now i will start to try to get it working in a prettier way :)
& that's it.

thank u.
yhotg

---

### Post by Burbruee on 2005-09-23
[QUOTE=yhotg]Well i found a way!!!
 \\:D/ 

extracted it, 
did make and make install
and as root: modprobe spca5xx
since then i have webcam  :-P 

thank u.
yhotg[/QUOTE]


Thank you!  :grin: 
Been trying to get my webcam ( Quickcam express. ) working for hours.
Made a little searches and found some driver qce-ga-0.40d.tar.gz and qc-usb-0.6.2.tar.gz but neither of them worked.

But your way worked excellent!
And I don't have color problems.
I know this thread is old, but I just wanted to say thank you.  \\:D/

---


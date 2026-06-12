---
title: "graphic card or driver problem?"
date: 2010-01-08
forum: Hardware
---

### Post by miroslav_karpis on 2010-01-08
Hi, please can you help me with this?

I have a Toshiba Qosmio notebook with graphic card Nvidia GeForce 9800M GTX. 2 months ago they needed to change the display and graphic card - so the graphic card should be new.

Today after work (am using 2 monitors) have started after 'suspend', changed xserver to use only one monitor and got some strange behavior - generally slow, after I log in the screen just turns black and does not react on anything.

I have made a fresh installation (with a format) and until I installed driver for the graphic card everything worked well. But after I install the driver the same (slow, screen turns black). 

The driver is found by Ubuntu so I guess that that should be correct. 

The question is - is it a graphic card issue, or? do you have any ideas?


Thank you in advance..

---

### Post by miroslav_karpis on 2010-01-08
I was just thinking - is it possible that in case I disabled in nvidia xserver the wrong display (as I mentioned before I had dual monitor then I suspended the PC and unplugged the additional one) so that the 2nd monitor that was unplugged was set as main one?
The thing is that the display does not turn black - it gets the background desktop I have. 

The question is if the _hardware can 'remember'_ this? - is it possible? If yes, can I somehow fix it?
As I mentioned I made a fresh installation of Ubuntu with disk format.

---

### Post by miroslav_karpis on 2010-01-09
PLEASE - any ideas?, suggestions?

---

### Post by miroslav_karpis on 2010-01-09
I have a feeling that it has something to do with the last ubuntu update - unfortunately I don't know the details but yesterday showed up update manager and installed something (have already reinstalled ubuntu so I don't know how to figure that out...)

does anybody if was recently something released that could 'touch' the graphic driver?

---

### Post by theham on 2010-01-18
i'm experiencing what i think is a similar a black/blank screen in karmic after the ubuntu boot logo is finished on a dell studio xps 1340 running a nvidia 9400m (+ 9200m but doesn't run due to no nvidia hybrid sli support) with karmic 64-bit. Though the screen is black I can switch back to a text based login using ctrl + alt + f1 etc. Also if i revert back to the nv driver everything works fine. I've tried both nvidia drivers 190.53 and 195.30 in the hope that it was a compatibility issue with newer software installed in a ubuntu update but neither worked. I tried going back through kernels 2.6.31-17-generic back to 2.6.31-14-generic in the hope that one would work ... which it hasn't. 

this bug filed by someone else sounds to me exactly like my problem [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/507979](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/507979) . You might want to check it out.

---


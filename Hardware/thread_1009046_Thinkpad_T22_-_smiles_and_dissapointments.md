---
title: "Thinkpad T22 - smiles and dissapointments"
date: 2008-12-12
forum: Hardware
---

### Post by louisella on 2008-12-12
Well this is my first look at Ubuntu (on the recommnedation of a friend) we tried other linux flavours a few years ago, but found them too unfriendly.

So I got myself an IBM Thinkpad T22 and Ubuntu 8.10 install disk and off I went.  About 2/3 into the install and was faced with the notorious T22 blank screen.  I followed the advice of older threads, removed the PCI daughterboard (modem and ethernet support) slotted in a Xircom PCMCIA card and bingo install successful internet connection successful!

My only problem now is getting the screen to understand a resolution better than 600x800 (any pointers would be gratefully received)

Once I have resolved that problem I only need to get my printer driver working and then I will be a convert to Ubuntu.

What a great job that has been done on this operating system, I am so impressed!

---

### Post by linux_tech on 2008-12-12
First type in xrandr to see what the available resolutions are.
Then ```
xrandr -s 1024x768 
``` or whatever resolution

---

### Post by albinootje on 2008-12-12
Here are reports from other (10 or so) people with the same laptop 
[http://www.linux-laptop.net/ibm.html](http://www.linux-laptop.net/ibm.html)

And here people write about trying the "vesa" driver for the T22 :
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/thinkpad-t22-intermittent-bootvideo-problem-582168/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/thinkpad-t22-intermittent-bootvideo-problem-582168/)

---


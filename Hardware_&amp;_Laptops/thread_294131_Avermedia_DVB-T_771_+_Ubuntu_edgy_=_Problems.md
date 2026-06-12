---
title: "Avermedia DVB-T 771 + Ubuntu edgy = Problems"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by sexus6 on 2006-11-06
Hi to all, this is my first post ...
I have a trouble with the AVERMEDIA DVB-T 771 card with my Ubuntu Edgy Eft 6.10 linux.
My kernel version is : 2.6.17

I use this howto to configure with Ubuntu:
[http://www.pvrweb.com/bbs/lofiversion/index.php?t5052.html](http://www.pvrweb.com/bbs/lofiversion/index.php?t5052.html)

In this Howto the kernel version is 2.6.10, but in that howto says that there isn't any problem with upper versions (like my 2.6.17).
The problem is, that in the howto's step when "make menuconfig", there is some options to check in the menuconfig...I have all the options, except one :

Device Drivers --> Multimedia devices --> Digital Video Broadcasting Devices=>Nebula/Pinnacle PCTV/Twinhan PCI cards

I haven't this option to check with <M> option, and nothing similar.  All the other options are correct and checked like this tutorial.
Although there is not that option, I try to continue with the tuto. The next step is to modprobe the next modules :
bttv
mt352'
dvb-bt8xx'
The 3 modprobes works (there are not error displays).

But when I make a dmesg: "dmesg | grep DVB" I have not results :(

Obviously, when I try to scan chanels (the next step in the howto) doesn't works...The error is "no such device /dev/DVB/adapter0/fronted0".

Additionally I try to create the nodes adapter0,adapter1, etc  with a sh script that I found  in the avermedia website howto :
  [http://www.avermedia.com/docs/pdffiles/Setting%20up%20AVerMedia%20A771%20DVB%20for%20Linux.doc](http://www.avermedia.com/docs/pdffiles/Setting%20up%20AVerMedia%20A771%20DVB%20for%20Linux.doc)) and there is creates....but the same error in the channels scan...

I Think that the card is not recognized by my system, I don't know if the trouble is :
1.-  My menuconfig haven't the "Nebula/Pinnacle PCTV/Twinhan PCI cards" option
2.- The howto is not valid for me
3.- My system doesn't detects my card
4.- Other?

Tests? Sollutions? Please help me

Thanks for your time and sorry for my poor english!

---

### Post by scto on 2006-11-13
hi,

im not completely sure but you've forgotten the card und tuner settigns

something like bttv card=10 tuner=39 (just an example)

the vaules for card an tuner corespondent with the values from the following 2 files:

Here is the most complete TV card list I could find taken from linuxtv.org (attachement):

---


---
title: "Old hardware questions"
date: 2008-08-13
forum: Hardware
---

### Post by gummo on 2008-08-13
I recently got my hands on 2 P3 systems which I am gonna combine to make a home server to be able to quickly get important data from any location without having to store it online, use it as a mailserver, etcetc.

One CPU is a 500Mhz Katmai model, the other one is a 400Mhz Coppermine. I've been reading up a bit and it seems the Coppermines are a lot better then the Katmais. Notice however that in this case the Mhz of the Katmai is 25% more then that of the Copperfield.

One motherboard uses the VIA Apollo Pro133 chipset while the other one uses the Intel 82440 BX chipset.

Now my question: Which combination would give me the best performance? 

I was thinking of using the VIA chipset and the Coppermine but I don't know if that would be the best setup. So instead of spending all day benchmarking both setups (i can only boot/bench one at a time) I figured I'de ask here if someone has any ideas on this.

Thanx in advance!

---

### Post by tamoneya on 2008-08-13
the coppermine processor is better from the view point of performance/watt.  Also the 500MHz coppermine is the bottom of the series while the katmai is the top of the series.  Therefore I would choose the katmai processor based on the increased performance.  As for the board I dont know the small differences between the boards since the chipsets are so old.  However I would opt for the intel board because it should get better driver support.

---

### Post by gummo on 2008-08-16
turns out that intel board had a 100Mhz fsb, thats why the coppermine only reported as a 400Mhz, while in reality it's a 533Mhz (4x multiplier). Sticking it on the VIA board gave me the correct 533Mhz (it has a 133Mhz fsb), so i went with that combo.

I did however run into some trouble with proftpd:
[http://ubuntuforums.org/showthread.php?p=5602942#post5602942]("http://ubuntuforums.org/showthread.php?p=5602942#post5602942")

---


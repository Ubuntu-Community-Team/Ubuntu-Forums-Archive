---
title: "are there VGA drivers for ATI 5870"
date: 2010-03-24
forum: Hardware
---

### Post by creatxr on 2010-03-24
I built my new computer for 1 day.
it seems that it doesn't gaming well as what I think. (e.g. warzone2100)
and it seems that the video card is also very hot even if I doesn't run a game.
how to well test my video card?
or maybe it need a right driver for 5870.
----------------------------------------
creatxr@creatxr-desktop:~$ lspci | grep VGA 
02:00.0 VGA compatible controller: ATI Technologies Inc Device 6898
----------------------------------------
i7 920 D0
Diamond 5870
12GB memory
EVGA X58 micro
ubuntu x64 10.04

---

### Post by cascade9 on 2010-03-25
Yes, there are drivers for the 5870. Try going-

System-> Administration-> Restricted Drivers Manager.

If that doesnt work, then you might have to dl the linux drivers from ATIs site- 

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by creatxr on 2010-03-26
> **cascade9 said:**
> Yes, there are drivers for the 5870. Try going-

System-> Administration-> Restricted Drivers Manager.

If that doesnt work, then you might have to dl the linux drivers from ATIs site- 

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

i don't have "System-> Administration-> Restricted Drivers Manager." 
is it "System-> Administration-> Hardware Drivers"? (ubuntu 10.04 beta1)
it can't find any else.

is video card 5870 always hot even if that it just start the system?

---

### Post by ATOMICplayer on 2010-03-26
> **creatxr said:**
> i don't have "System-> Administration-> Restricted Drivers Manager." 
is it "System-> Administration-> Hardware Drivers"? (ubuntu 10.04 beta1)
it can't find any else.

is video card 5870 always hot even if that it just start the system?

I'm actually looking for drivers for the 5770 as well. I have downloaded Catalyst 10.3 but even 10.3 doesnt support the new Xserver that is in Ubuntu 10.04.

---

### Post by creatxr on 2010-03-26
thanks.
now i return to ubuntu 9.10 and install Catalyst 10.3
it seems it is much better than before -- the video card doesn't so hot to run the fan very fast.

---

### Post by goatgonads on 2010-04-21
Correction as of 4-21-10 this video card (ATI 5870) doesn't run that well, and its not that hot (as in performance) 8800GT runs circles around it.

---


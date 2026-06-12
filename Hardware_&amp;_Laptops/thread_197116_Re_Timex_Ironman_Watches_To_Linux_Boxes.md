---
title: "Re: Timex Ironman Watches To Linux Boxes"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by xe1ufo on 2006-06-15
Dear Friends:
 
I recieved a nice Timex IronMan watch as a gift from my dear
wife a few months ago.  It connects to the PC via a USB cable,
and stores contact and appointment information, as well as notes
and the time for several timezones.
 
I have tried several websearches for any info on linking these to
Linux, and have found nothing.  Does anybody have some ideas?
 
(There is, of course, a program in most Linux distros called timex, which is used to sync your system clock to a time-server on the web.  It has nothing to do with the Timex watches.)

Thanks in advance:
 
Dr. Steve, central old Mexico

---

### Post by Lunar_Lamp on 2006-06-15
The first step is probably to paste the output of "dmesg" when you plug it into your laptop.  Plug in your usb watch, and type "dmesg | tail -f" in a terminal, and past the output here.  This will give us some info about it!

[edit to mod: it may be an idea to move this out of laptop to somewhere it would get mre attention, as it is not specically laptop related.]

---

### Post by donkyhotay on 2007-06-26
this is probably a dead topic but just in case anyone else needed to know I did find:
[http://geni.ath.cx/libdlusb.html](http://geni.ath.cx/libdlusb.html)
which apparently has an unstable library for linking timex data link watches to a linux box.

---

### Post by turbotuba on 2007-12-26
jared@jared-laptop:~$ dmesg | tail -f
[ 3139.992000] usb 5-1: new low speed USB device using uhci_hcd and address 2
[ 3140.116000] usb 5-1: device descriptor read/64, error -71
[ 3140.344000] usb 5-1: device descriptor read/64, error -71
[ 3140.560000] usb 5-1: new low speed USB device using uhci_hcd and address 3
[ 3140.684000] usb 5-1: device descriptor read/64, error -71
[ 3140.912000] usb 5-1: device descriptor read/64, error -71
[ 3141.128000] usb 5-1: new low speed USB device using uhci_hcd and address 4
[ 3141.540000] usb 5-1: device not accepting address 4, error -71
[ 3141.652000] usb 5-1: new low speed USB device using uhci_hcd and address 5
[ 3142.068000] usb 5-1: device not accepting address 5, error -71
jared@jared-laptop:~$ 

I checked out the url from above...
libdlusb: "This software can cause severe damage to your Timex Data Link USB watch. Use at your own risk."
Has anyone used this software?  Why the heck would any use it with a disclaimer like that?

---


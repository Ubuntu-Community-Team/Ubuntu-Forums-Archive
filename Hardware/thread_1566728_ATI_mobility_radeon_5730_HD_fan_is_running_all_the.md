---
title: "ATI mobility radeon 5730 HD fan is running all the time, GPU is cold"
date: 2010-09-02
forum: Hardware
---

### Post by dedalus1337 on 2010-09-02
Hello,

i bought a lenovo ideapad y560 with i7 and ati mobility radeon 5730 hd.
when i started my notebook, the fan runs extremely loud. all 30 seconds it gets quiet for about 3 seconds and afterwards it gets loud again. this is an ubuntu prob, on win 7 it runs quiet. i looked at the system monitoring but the 8 cores are running at max 5%. at the 3 sec quiet period one core is running at 80% but afterwards again at max 3 %. i think its definitely not the cpus fan which is running.

when i use acpi -V the temp is at 54 degree C and all coolings are at 0 of 10 so the cpus fans are not running.
so i continued at looking at the GPU fan.
i installed:
fglrx-amdcccle, 
fglrx-kernel-source, 
fglrx-modaliases, 
xorg-driver-fglrx

aticonfig --odgt tells me a temperature between 53 and 55 degree C. so the gpu is not too hot. i read in another thread that fglrx has no control over fan control so its running on full speed. but it ran on full speed all the time, also on ubuntu installation and without the fglrx driver.

when i type aticonfig --pplib-cmd "get fanspeed 0" it tells me a fan speed between 39 and 41 %. when i use aticonfig --pplib-cmd "set fanspeed 0 10" it tells me "PPLIB command execution successful!" but there is no change in the behaviour of the fan. when i try aticonfig --pplib-cmd "get fanspeed 0" it tells me 10 all the time, so aticonfig accepted the command but it cannot control the fan. someone told me to use aticonfig --set-powerstate 1 but aticonfig does not know this command. i need to get the GPU in powersafe mode or to slower the fan, the temperature of 55 degree is good, so thats a problem of fan control. is there anyone who knows a solution?

thanks!

---

### Post by Angelontu22 on 2011-03-04
Hello,

I also have a Lenovo Ideapad Y560 with ATI mobility Radeon HD 5730 graphics but its an Intel core i5-450m with switchable graphics. It runs Windows 7 64-bit quietly but just like you, the fan is really loud on Ubuntu. I use my laptop on my bed most of the time so it can get quite hot. I've tried installing the proprietary AMD FGLRX drivers downloaded from AMD's site but unfortunately I was presented with a black screen on startup once restarted so I'm forced to use the default opensource drivers (for now). 

Basically, I have the same issue you do, but it seems like your post has been here for a while without response. Hope someone stumbles upon this at some point :/

---

### Post by ibalog on 2011-03-20
Hello everybody,

   I have a Lenovo Y560 with the Mobility Radeon 5730 discrete 
graphics and am running Ubuntu 10.10 64bit with kernel 2.5.36-28 
generic I can not get the fglrx drivers to work in any way. I 
always get the blank screen. I did everything various forums 
and wikis sugest.

Running "aticonf --initial -f" is the first thing I did and it did nothing. 
After that I followed the wiki:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#.22Errors_were_encountered_while_processing:_fglrx-amdcccle.22_.28on_64-bit_systems.29](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#.22Errors_were_encountered_while_processing:_fglrx-amdcccle.22_.28on_64-bit_systems.29)

where they consider troubleshooting the "Problems Starting Xserver". 
Nothing worked and the Xserver still does not start.

 
   When I remove the xorg.conf the X starts, but I suspect that it runs in 
some failsafe mode. Namely, when I try to run the "ATI Catalyst Control 
Center" it says:

"
There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
"

If somebody could shed some light into my problem I would be very grateful!

---

### Post by yeagle on 2011-04-15
My Lenovo Y560 (with i7) works fine with Ubuntu.

I downloaded the latest grapics driver from the original amd page:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Maybe this helps you...

---

### Post by ibalog on 2011-04-29
Ok, in the meanwhile I have upgraded to ubuntu 11.04 and installed AMD Catalyst 11.4. 
Finally the fglrx drivers are working, and I can finally switch graphics in Catalyst Control 
Center.

---

### Post by bukumayank on 2011-06-06
looks like the problem is only with Lenovo Y560(i5 version)
ati drivers are working for the i7 version as it does not have the intel graphics, i5 version comes with intel graphics so catalyst drivers are not working correctly on it.!!

---


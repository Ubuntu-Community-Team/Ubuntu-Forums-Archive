---
title: "AMD drivers on a laptop with missing display and external display?"
date: 2015-12-19
forum: Hardware
---

### Post by mbaucco on 2015-12-19
Hello,

I know this probably a bit off the wall but I hope someone can help. I have an old Toshiba laptop with a Radeon Mobility graphics card (64xx or 74xx) not quite sure) The laptop is missing its internal display so I have it plugged into an external monitor. I'm running Ubuntu 15 64 bit with 8GB RAM and it works pretty well otherwise, but I'd like to play some games on it and take advantage of the video card's 3D acceleration features.

I've tried going to the "Drivers" control panel and using the fglrx drivers, but whenever I switch I lose my screen when I restart. The laptop boots up OK, then it turns  black (sometimes I can just see "tty" on the far left upper corner of the screen and a shaky greyish line down the middle of the display). I'm not a Linux expert so I just revert back to the default drivers to fix this.

Is there any way to get the AMD drivers working right or am I out of luck? 

Thanks in advance, :)

Matt

---

### Post by mörgæs on 2015-12-20
Please run ```
sudo lshw -C video
``` and post the output in CODE tags.

---

### Post by mbaucco on 2015-12-20
Thanks for the reply! Here is the output:

```
 
 *-display               
       description: VGA compatible controller
       product: Seymour [Radeon HD 6400M/7400M Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:50 memory:c0000000-c7ffffff memory:cc400000-cc41ffff ioport:3000(size=256) memory:cc440000-cc45ffff

```

---

### Post by mörgæs on 2015-12-20
You are welcome but this is as far as I'm able to help. 

I have never tried installing closed source AMD/ATI drivers but I hope someone more experienced than me can use the information above.

---

### Post by ajgreeny on 2015-12-20
When you state you have Ubuntu version 15 do you mean 15.04 or 15.10?

Version 15.10 has had problems with the AMD driver available from Additional Drivers, though there are some workarounds if the drivers have not yet been fixed.  See the 15.10 release notes for the information which involves enabling the Proposed repos and updating just the driver, then disabling the Proposed repos again.
See [https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes) and
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888)

---

### Post by mbaucco on 2015-12-20
I'm sorry, I could have sworn I had Ubuntu 15.04 on here, but I only have 14.04, I think I got it confused with my home laptop. Should I upgrade to 15.10 and see if it works better?

Thanks!
Matt

---

### Post by grahammechanical on 2015-12-20
The ATI driver web site lists AMD Catalyst revision 15.9 as suitable for your graphic adapter.

[http://support.amd.com/en-us/download/desktop/previous/detail?os=Linux%20x86_64&rev=15.9](http://support.amd.com/en-us/download/desktop/previous/detail?os=Linux%20x86_64&rev=15.9)

Try searching that web site for yourself to see if I have things correct. Does Additional Drivers offer that version of the Catalyst proprietary video driver? Whenever we activate a video driver using Additional Drivers that driver should be the one loaded by Linux when we restart.

Is the external display screen active when Ubuntu loads? When Linux loads it gets the screen resolution from the monitor each time it loads. To load Linux without a monitor connected will present problems.

Regards.

---

### Post by mbaucco on 2015-12-20
I do have the external monitor plugged in, and the laptop "sees" it as far as I can tell. When I power it on the Toshiba logo appears on the external monitor, the trouble starts after that. The laptop has no display at all but perhaps it still thinks it has one? The 15.9 drivers look right, I'm going to give them a try and see what happens.

Thanks again for all the help!
Matt

---

### Post by mbaucco on 2015-12-20
No luck. :( I installed the drivers and ran "aticonfig --initial" afterwards but got the same thing, after the POST I briefly see "tty8" (I think) in the upper left corner then nothing. I can boot into recovery mode but failsafe graphics mode doesn't work. So far the only way I know to get it working again at this point is to revert back to the default drivers. Is there something else I can try to get it working? I checked the BIOS and didn't see anything that looked helpful.

Thanks,
Matt

---


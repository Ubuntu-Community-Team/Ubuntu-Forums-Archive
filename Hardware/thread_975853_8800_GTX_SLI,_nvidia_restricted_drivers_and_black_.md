---
title: "8800 GTX SLI, nvidia restricted drivers and black screen of death"
date: 2008-11-08
forum: Hardware
---

### Post by bumfluff on 2008-11-08
Hello,

Apologies for posting this as there seems to already be a number of posts already regarding this- although they appear to be solved - however I'm struggling.

I recently upgraded to 8.10 from 8.04 and I've got the dreaded black screen of death. Once I've installed the restricted nvidia drivers (177.80 and 173), the PC boots to a black screen. If I log in, I hear the familiar Ubuntu tune which makes me think the monitor is being incorrectly detected. 
If I switch the drivers to vesa (in xorg.conf) then it boots fine but I notice the monitor is still "Unknown" and I can't select other resolutions. 
I've made sure the correct headers are installed and no joy.  I've added BusID (PCI:04:00:0) to my xorg.conf as I've got 2 x 8800GTX's and this just allows me to get an output on the correct screen.
Lastly the monitor is a Samsung 225BW and is connected on DVI. 

Any help or suggestions would be greatly appreciated. Xorg.conf attached.

Many thanks

Joel

---

### Post by bumfluff on 2008-11-10
Hello,

In case it helps anyone else, I've managed to solve it. I did the following:

1. Remove any trace of nvidia drivers with apt-get remove --purge
2. Reinstalled nvidia-glx-177.80 with Synaptic
3. Ran sudo nvidia-xconfig.
4. Since I'm running SLI's, I needed to add in to the xorg.conf BusID "PCI:03:00:0" under Driver. I think this was the problem previously, as I'd been adding "PCI:04:00:0" which still produced a VESA output.
5. Reboot and Robert is your Dad's brother...

All good.


Joel

---


---
title: "Nvidia driver issues - Ubuntu 12.04"
date: 2014-03-10
forum: Hardware
---

### Post by theSEOmanian on 2014-03-10
Hello all, 

I have been struggling with this for a couple days now. Hopefully, I can find a driver guru that can shed some light. 

I have a BFGTech GTS250 pushing to two 25" monitors. I have another card (GeForce GT 520) pushing to a 60" TV. 

 
Out of the box ubuntu is doing quite well with both cards. Every now  and then the mouse will freeze and the computer become unresponsive. It  will suddenly catch up with all my mouse movement and I am ready to  rock. I assume this is because it has the wrong drivers.


  I have attempted the following:

  sudo apt-get --purge remove nvidia-current
  reboot.
  sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
  reboot.


  Now, my large TV is displaying a blank screen and the mouse is a large "X". 

  After removing the nvidia install and installing from nvidia-331 I get the same results. 

**Here is my xorg.conf**:[ http://pastebin.com/93JtX5Ge]("http://pastebin.com/93JtX5Ge")

Now, I have decided to start fresh and re-install ubuntu. I was told the bumblebee blocks the driver I need, and I should remove bumblebee. I am not sure how to go about doing this. Any advice? Thanks in advance for any help.

---

### Post by theSEOmanian on 2014-03-10
After my OS-reinstall I tried the following:[INDENT]
sudo add-apt-repository ppa:mad:org-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331
[/INDENT]
[INDENT]sudo apt-get --purge remove bumblebee
sudo reboot
[/INDENT]

After this, my two monitors (powered by the GTS 250) seem to working much better. I was unable to see my TV (powered by the GT 520) in my displays. I opened X server and the monitor was disabled. After I enabled the monitor and performed a restart I see a blank screen and the mouse icon is an "X". I did not see any warnings that I was running low-graphics mode. 

...back in the same boat.

**xorg config:** [http://pastebin.com/b5kye4zz](http://pastebin.com/b5kye4zz)
**Xorg.0.log:** [http://pastebin.com/cntxtYdw](http://pastebin.com/cntxtYdw)

**sudo lshw -C display; lsb_release -a; uname -a; dpkg -l | grep nvidia**     -----

[SIZE=1][FONT=lucida console]  *-display               
       description: VGA compatible controller
       product: G92 [GeForce GTS 250]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:56 memory:f8000000-f8ffffff memory:c0000000-cfffffff memory:f6000000-f7ffffff ioport:e000(size=128) memory:f9000000-f901ffff
  *-display
       description: VGA compatible controller
       product: GF119 [GeForce GT 520]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:57 memory:fa000000-faffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff ioport:d000(size=128) memory:fb000000-fb07ffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
Linux alex-ubuntu 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
ii  nvidia-331                                331.49-0ubuntu1~xedgers13.10.3          amd64        NVIDIA binary driver - version 331.49
ii  nvidia-libopencl1-331                     331.49-0ubuntu1~xedgers13.10.3          amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                     331.49-0ubuntu1~xedgers13.10.3          amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                           331.38-0ubuntu1~xedgers~saucy1          amd64        Tool for configuring the NVIDIA graphics driver[/FONT][/SIZE]

---

### Post by theSEOmanian on 2014-03-13
162 Views and not one suggestion. No answers posted on askubuntu. No one able to completely solve the issue on ubuntu's IRC (#ubuntu and #ubuntu-x). 8 bugs submitted. 

Have I actually stumped Ubuntu?

---


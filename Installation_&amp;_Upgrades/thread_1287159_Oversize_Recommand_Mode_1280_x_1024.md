---
title: "Oversize Recommand Mode 1280 x 1024"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by meanswing on 2009-10-09
Im very new to Ubuntu. Installed it a week ago. Every time i boot up Ubuntu my monitor gives me "Oversize Recommand Mode 1280 x 1024" error . I have to go into the Ubuntu recovery console and use" Try to fix graphics errors" thing to be able to boot up ubuntu. I am using an Asus A7N-266 motherboard and a Geforce FX 5900 XT. anyone know how to fix this. I think the Nvidia Accelerated Graphics Drivers is giving me trouble. Any help would be appreciated.

---

### Post by meanswing on 2009-10-10
Ok i was able too boot up ubuntu on desktop. Now when i try to Activate the NVDIA Accelerated Graphics version 173 or 96 and reboot i get an error. Here is what im getting

Ubuntu is running in low graphics mode. The following error was encountered. You may need to update you configuration to solve this.
(EE) NVIDIA (0): Failed to load module "freetype" (module does not exist, 0)
(EE) NVIDIA (0): Failed to load module "type1" (module does not exit, 0)
(EE) NVIDIA (0): Failed to initialize the NVIDIA Kernel module! Please ensure
(EE) NVIDIA (0) that there is a supported NVIDIA GPU in thiS sYstem, and 
(EE) NVIDIA (0) that the NVIDIA device files have been created properly.
(EE) NVIDIA (0): Please consult the NVIDIA REAM ME for details. 
(EE) NVIDIA (0): ***Aborting***
(EE) Screen(s) found, but none have a useable configuration.


I also ran "sudo lshw -c video" and here is what came up
 sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: NV35 [GeForce FX 5900XT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: driver=nvidia latency=32 maxlatency=1 mingnt=5 module=nvid

---

### Post by jfulfer on 2012-06-20
I am having the same problem with Ubuntu 12.04. I installed on one computer than when i put the hard drive into my desktop monitor came up with "over size error recommended 1280 x 1024". Is there anything I can do to solve this?

---


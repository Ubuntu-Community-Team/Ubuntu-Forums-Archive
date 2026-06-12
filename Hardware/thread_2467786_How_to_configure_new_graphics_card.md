---
title: "How to configure new graphics card"
date: 2021-10-07
forum: Hardware
---

### Post by Only1KW on 2021-10-07
I'm running Ubuntu 18.04.  I recently installed a new graphics card.  I can only get a single output to work on it.  What do I need to do to reconfigure Ubuntu to detect my new adapter and start using it?

 ~/Downloads/amdgpu-pro-19.30-909144-ubuntu-18.04 $ sudo lshw -C display
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Turks GL [FirePro V4900]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:41:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:80000000-8fffffff memory:9f620000-9f63ffff ioport:3000(size=256) memory:c0000-dffff

---

### Post by Only1KW on 2021-10-07
To be clear, I've tried installing open source radeon, open source amdgpu, and amdgpu-pro from AMD's website.  Everything seems to install correctly, but none of them will actually bind to the card.

---

### Post by QIII on 2021-10-08
First thing:  remove anything amdgpu.  Your very old hardware (technologically speaking) is beyond end-of-life and was discontinued before amdgpu came along. Its physical architecture is not compatible with amdgpu.

Your card is supported by the open-source radeon driver module.  If you were able to see anything on your monitor when you installed the card, then the module was loaded and driving your GPU.  There would have been nothing else required on your part.

---

### Post by Only1KW on 2021-10-08
I've already tried removing everything amdgpu by calling /usr/bin/amdgpu-uninstall and /usrbin/amdgpu-pro-uninstall (depending on what existed there at the time) and it doesn't seem to help.  I do have something on my monitor after installing the card.  The problem is all monitors have the same thing.  When I pull up arandr, I see one "default" screen.  I keep reading that because the output of lshw -C display says the display is UNCLAIMED  and the "configuration" line doesn't show "driver=", that means no driver is loaded for the card.  Is that not correct?

---

### Post by QIII on 2021-10-08
No, that is not necessarily correct.  If you see anything at all with a card with that physical architecture, the radeon module is loaded and driving the GPU.  There are only two drivers for AMD graphics devices in a modern Linux distribution:  radeon and amdgpu (AMDGPU-PRO if you add the proprietary overlay to amdgpu).  Both are present in the Linux kernel as is and no further action is required.  The module that will be loaded and used depends on which supports the hardware.  In your case, that is radeon.

Please issue the following command in the terminal and post the results

```
lsmod | grep radeon
```

---

### Post by Only1KW on 2021-10-08
I tried that command and got nothing back.  I then loaded that module and long story short, after fixing some other things I broke while trying to debug, everything is working as I desire.  With some more digging, I found that "radeon" was in /etc/modprobe.d/blacklist.conf, probably due to my previous card installed.  Removing that seems to be a permanent fix.  Thanks!

Edit: lshw -C display output looks correct too.

 ~ $ lshw -C display
WARNING: you should run this program as super-user.
  *-display                 
       description: VGA compatible controller
       product: Turks GL [FirePro V4900]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:41:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:134 memory:80000000-8fffffff memory:9f620000-9f63ffff ioport:3000(size=256) memory:c0000-dffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---


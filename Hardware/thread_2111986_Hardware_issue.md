---
title: "Hardware issue"
date: 2013-02-03
forum: Hardware
---

### Post by sizaradam on 2013-02-03
dear all
im new to ubuntu , facing a problem with my graphic card 
my laptop is Asus K53E and ubuntu doesn't recognize my graphic card says unknown.

please advice

---

### Post by ajgreeny on 2013-02-03
What is the output of command ```
lspci
```and/or ```
sudo lshw -c display
```

---

### Post by Yellow Pasque on 2013-02-03
If you're referring to sysinfo program, that's a common bug. Nothing to worry about as long as glxinfo program outputs correct information:
```
sudo apt-get install mesa-utils
glxinfo
```

---

### Post by sizaradam on 2013-02-03
this is the output mr.ajgreeny

 *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:51 memory:dd000000-dd3fffff memory:c0000000-cfffffff ioport:e000(size=64)

---

### Post by ajgreeny on 2013-02-04
> **sizaradam said:**
> this is the output mr.ajgreeny

 *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:51 memory:dd000000-dd3fffff memory:c0000000-cfffffff ioport:e000(size=64)
So it looks as if your system does detect the graphic card, and presumably you are getting to a desktop so not only is it detected, but it also works as it should.

Most Intel graphics work "out of the box" in Linux these days.

---

### Post by sizaradam on 2013-02-05
> **ajgreeny said:**
> So it looks as if your system does detect the graphic card, and presumably you are getting to a desktop so not only is it detected, but it also works as it should.

Most Intel graphics work "out of the box" in Linux these days.

Dear Mr. Ajgreeny 

thank you for your concern and for helping me out , 
i was able to find this command , which when i used it it change the graphic card status from unknown to this :
Intel® Sandybridge Mobile x86/MMX/SSE2 



the command was this 
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

---

### Post by sizaradam on 2013-02-06
oh by the way i found these commands too i hope it will help any one who face the same problem

thank you all for your help 


sudo apt-get install mesa-utils

If you want the latest driver:

sudo add-get-repository ppa:glasen/intel-driver
sudo apt-get update
sudo apt-get install xserver-xorg-video-intel&#65279;

---


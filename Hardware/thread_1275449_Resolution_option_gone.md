---
title: "Resolution option gone"
date: 2009-09-25
forum: Hardware
---

### Post by evo9 on 2009-09-25
I'm having a problem on my Toshiba Satelite Laptop running Ubuntu 9.04.

When I used my tv as a second monitor to watch movies on I had to change my resolution from 1280x800 to 1024x768. Now I no longer have the option to set it back to 1280x800.

I've been searching the forums and I have found some similar problems but nothing with my graphics card. 

When I enter the command "sudo lshw -C display" in the terminal this is what shows up.             

  *-display UNCLAIMED
       description: VGA compatible controller
       product: Mobility Radeon HD 2400
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0


Any help would be greatly appreciated, my system has been like this for about 2 weeks now and I really would rather solve this problem than reinstall.

---

### Post by mikewhatever on 2009-09-25
I'd boot into recovery mode and select the option to reconfigure xserver. If 1280x800 was the default resolution, chances are, it'd get restored. There is definitely no need to reinstall.

---

### Post by evo9 on 2009-09-27
You are a scholar and a gentlemen, thank you sir.

With that problem solved, any ideas if the same thing will happen if I use my tv for a second monitor again? Is there anything possible to prevent it?

---

### Post by abdusamed on 2009-10-12
in my ... i just have the option of 1024 x764 RESOLUTION! disappeared RANDOMLY! i will try xserver boot trick toom on my xubuntu.. hope it helps.. any other suggestion WILL help GREATLY~ :(

---


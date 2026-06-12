---
title: "No video output after system starts"
date: 2015-04-23
forum: Hardware
---

### Post by nelsonhoover on 2015-04-23
I'm not having any luck getting video output after my Ubuntu Server 14.04 finishes booting. Grub works, I can see the system starting to boot, but when it should give me the login prompt, the graphics output turns off; the monitor simply says "no signal".

I have tried all manner of grub options, such as NOMODESET, VGA=0, etc, with no luck.

Here is the graphics controller the PC has (got this via SSH):
```
user@pc# lshw -C display  
    *-display
       description: VGA compatible controller
       product: Atom Processor D2xxx/N2xxx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=gma500 latency=0
       resources: irq:50 memory:80200000-802fffff ioport:30d0(size=8)



```

I'll be using it as a little server and don't care what kind of quality the display is (I'm not running X11), I just want to have some way of editing a few configs directly from the console instead of SSH being my only access, for when I mess up some network config and can't get back in.

Can I somehow just force VGA mode? Or make the system use the same settings it is before it hits init? The display does work till that point in the boot process.

Thanks in advance for any advice,
Nelson

---

### Post by nelsonhoover on 2015-04-24
OK, I finally got this working by blacklisting the gma500_gfx kernel module to keep the kernel from loading the graphics driver.

To do this, open (on anything after 12.04) */etc/modprobe.d/blacklist.conf* and, at the bottom, add *blacklist gma500_gfx *and save it. Reboot and voila, a command prompt.

---


---
title: "Low resolution after updating xubuntu packages"
date: 2014-10-02
forum: Hardware
---

### Post by dave0109 on 2014-10-02
I recently performed an upgrade of all packages, amongst which appears to have been an upgrade from nvidia-337 to nvidia-340 (both from the xorg-edgers PPA).  Prior to the upgrade I was able to run my monitor at its native 2560x1440.  Now, I only get 800x600.  My card is a GeForce GTX 750 Ti.

I purged all the packages from xorg-edgers (actually I purged the PPA) and went back to default. Rebooted, then re-added the PPA and installed nvidia-340 again with all upgrades, to no avail.

Frustratingly, nvidia-337 has been deleted from the PPA, so I can't go back to that.  The standard drivers in Xubuntu won't work (beyond 800x600) either.  So now I appear to be stuck.

I've tried my old 1920x1200 monitor, just in case the new driver couldn't cope with the higher res monitor, but that hasn't done anything different.

Output from xrandr isn't very inspiring...
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        75.0* 

```

Not sure where to go from here.

---

### Post by Vladlenin5000 on 2014-10-03
Why don't you use just what's offered in additional drivers? This assumes you somehow need the proprietary driver. Having that in mind the first choice should always be the version tested for your OS version. I really don't understand why you insist in a version that doesn't work for you...

---

### Post by dave0109 on 2014-10-03
I don't insist on anything.  Perhaps it wasn't clear when I wrote "The standard drivers in Xubuntu won't work (beyond 800x600) either.", so to clarify: I have now purged the xorg-edgers PPA and rebooted.  I'm back (still) in an 800x600 screen.  If I go to the Additional Drivers settings, nothing extra is found.

If I run the command "sudo ubuntu-drivers devices", there's is a short delay and nothing else is returned.  I end up back at the shell prompt.

So perhaps the issue is now that ubuntu isn't detecting the graphics card?

To clarify further, everything was working fine when I booted up a couple of days ago - I then installed the latest updates when prompted, rebooted (due to new kernel) and since then haven't got anything better than 800x600.

Thanks for looking.

---

### Post by dave0109 on 2014-10-03
Additional information:-
```

$ sudo lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2)
01:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev a1)
$ sudo lshw -class display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fb000000-fb07ffff

```

---

### Post by MartyBuntu on 2014-10-03
You followed the **explicit** instructions for upgrading with xorg-edgers, right?

It's a fairly experimental PPA. Stuff breaks. Expect stuff to break occasionally.

**IMPORTANT NOTICE* - If you are upgrading from one release to another and are using this PPA, be sure to install ppa-purge and use it to downgrade all of this PPA's packages before the upgrade or you will have a broken system.*

---

### Post by dave0109 on 2014-10-03
I was on 14.04 already and simply updated the packages that I was notified about.  It wasn't an upgrade from any previous Ubuntu version.  I was using the xorg-edgers nvidia-337 because the nvidia-331 shipped with Ubuntu didn't work with the graphics card (in fact I ended up with no display on tty7 at all), hence the use of xorg-edgers.

Following the update, which took me to nvidia-340, I've been stuck with this low resolution.

So now I'm back to vanilla Xubuntu, with nothing from xorg-edgers, and still at 800x600 with no Additional Drivers being flagged as available.

---

### Post by dave0109 on 2014-10-04
I haven't had any luck at all with this.

Looking on the nvidia web-site, I can see that the driver offered by Ubuntu 14.04 (nvidia-331) doesn't support the GeForce GTX 750Ti.

So I've tried both offerings from xorg-edgers > 331 and haven't had any change in screen resolution.  However, there are changes in the output from certain commands that indicate the driver is loaded (I believe), but not sure what the missing link is.

I can see the driver is being used...
```

$ lspci -vnn | grep -i VGA -A 12
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] [10de:1380] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: ZOTAC International (MCO) Ltd. Device [19da:1352]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	Expansion ROM at fb000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia

```

I can check that the kernel module is loaded...
```

$ lsmod | grep nvidia
nvidia              11070267  1 
drm                   303102  2 nvidia

```

I can get info about the module...
```

$ modinfo nvidia_343
filename:       /lib/modules/3.13.0-35-generic/updates/dkms/nvidia_343.ko
alias:          char-major-195-*
version:        343.22
supported:      external
license:        NVIDIA
...
$ sudo dkms status
nvidia-343, 343.22, 3.13.0-35-generic, x86_64: installed
nvidia-343-uvm, 343.22, 3.13.0-35-generic, x86_64: installed

```

The display is no longer UNCLAIMED...
```

$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fb000000-fb07ffff

```

But still, xrandr isn't detecting anything useful...
```

$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        75.0* 

```

---

### Post by dave0109 on 2014-10-06
Fixed it.

I used a spare partition on the disc to install Xubuntu afresh, which initially gave me a 1600x1200 desktop.  I then went and changed to the nvidia-340 drivers and got a full 2560x1440.  All worked well, so I then knew that the binaries worked with my system.

Thanks to information [on this blog entry]("http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/") I was able to go through and detect which modules were loaded, and although the nvidia-340 could be found, when I did a 'modprobe -R nvidia' I got an error stating that it wasn't found.

This led me to comparing the contents of /etc/modprobe.d where I found that 2 files were missing (nvidia-340_hybrid.conf and nvidia-graphics-drivers.conf), which I copied over.  I also noticed that I had a bumblebee.conf, despite not having that installed.  It wasn't listed as an installed package in synaptic, but I deleted the package anyway.

One reboot later and the full resolution re-appeared.  The only mystery now is why it broke in the first place.

---


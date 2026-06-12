---
title: "Missing graphics and ATI proprietary driver issues"
date: 2012-04-21
forum: Hardware
---

### Post by 23senick on 2012-04-21
I was trying to reduce the temperature for my HP DM1 4020. Psesnor was tracking 3 pieces of hardware (doesn't give any labels) all running around 67-70 degrees (plus the battery)

After various tweaks (Jupiter etc) I followed a suggestion and tried both propitiatory graphics drivers (original and post-release). the first worked but no temperature change and displayed "non-compatible hardware" all the time. The post-release one install failed.  

So back to neither being enabled (using Additional Drivers), or so I thought.  However Psensor is now only tracking 2 devices.  Graphics hardware is beyond my skill level but I guess something has been disabled. Plus the output of *lshw -C display* is as follows:
 
  *-display               
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
      resources: irq:43 memory:e0000000-efffffff ioport:4000(size=256) memory:f0300000-f033ffff

Firstly, how can I re-enable the missing hardware?

Secondly the driver is fglrx, I thought this was proprietary, or is this open source? If proprietary, why is it showing as disabled in Additional Drivers, and how can I revert to open source?

Grateful for any suggestions!

---

### Post by jocko on 2012-04-21
> **23senick said:**
> Secondly the driver is fglrx, I thought this was proprietary, or is this open source? If proprietary, why is it showing as disabled in Additional Drivers, and how can I revert to open source?
Flgrx is amd's proprietary driver. The "disabled" message in jockey-gtk is just a faulty message. It will show "disabled" even when the driver is installed and working.
The proprietary driver is probably the best driver (at least it should perform better and is likely to have better support for the powersaving features) for you if:

[LIST]
[*]your laptop is reasonably new (which I guess it is, since it uses a pcie bus).
[*]it is not too new (if the card is newer than the driver, it is probably not supported. But amd may have a newer driver on their website).
[*]your laptop does not have hybrid graphics (some variants work, others don't)
[/LIST]
Note that with the proprietary driver the temperature and power features of the card is handled by the driver and the catalyst control center, which may very well be the reason psensor lost one of your sensors.

To revert to the open source driver, first uninstall the proprietary driver. Type this in a terminal:
```
sudo apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates
```
Then remove the /etc/X11/xorg.conf file:
```
sudo rm /etc/X11/xorg.conf 
```

---

### Post by jocko on 2012-04-21
> **23senick said:**
> Secondly the driver is fglrx, I thought this was proprietary, or is this open source? If proprietary, why is it showing as disabled in Additional Drivers, and how can I revert to open source?
Flgrx is amd's proprietary driver. The "disabled" message in jockey-gtk can be just a faulty message. It sometimes show "disabled" even when the driver is installed and working.
The proprietary driver is probably the best driver (at least it should perform better and is likely to have better support for the powersaving features) for you if:

[LIST]
[*]your laptop is reasonably new (which I guess it is, since it uses a pcie bus).
[*]it is not too new (if the card is newer than the driver, it is probably not supported. But amd may have a newer driver on their website).
[*]your laptop does not have hybrid graphics (some variants work, others don't)
[/LIST]
Note that with the proprietary driver the temperature and power features of the card is handled by the driver and the catalyst control center, which may very well be the reason psensor lost one of your sensors.

To revert to the open source driver, first uninstall the proprietary driver. Type this in a terminal:
```
sudo apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates
```
Then remove the /etc/X11/xorg.conf file:
```
sudo rm /etc/X11/xorg.conf 
```

---

### Post by 23senick on 2012-04-21
Thanks, Ill give that a go. Can always revert to proprietary driver if necessary - though I've heard 12.04 may have better temperature performance anyway, so other option is to wait a few days for release...

---

### Post by 23senick on 2012-04-21
yep, everything back to normal - unfortunately including running a bit hot again. There were one or two graphics things with the proprietary driver which didn't look right (nothing serious).and these also are resolved  

Will wait and see if 12.04 improves things - thanks again!

---

### Post by 23senick on 2012-05-12
No better with 12.04...back with proprietary driver and CPU etc hovering around 57-58 degrees (windows seemed to be 56-57, so comparable)

---


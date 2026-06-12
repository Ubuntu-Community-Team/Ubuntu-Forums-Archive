---
title: "Nvidia GTX 750 + Intel HD. Dual card / dual monitors"
date: 2014-10-16
forum: Hardware
---

### Post by James_Hughes on 2014-10-16
Hi all! Long time since I posted here (had to make a new account because I could not get my curuxz one to work) but am stuck with my new computer. Recently got one of these: [http://www.ebuyer.com/634853-zoostorm-gaming-desktop-pc-7260-5000](http://www.ebuyer.com/634853-zoostorm-gaming-desktop-pc-7260-5000) and am dual booting it with windows. Because I have windows I can confirm all hardware is working fine and the setup is ok. 

I want to have two screens (one LG 22" and one Acer 22") both on VGA. Since both the nvidia and the intel HD onboard graphics each have one VGA port (the DVI's do not support VGA) I am using one montior on each card. In windows this is fine, left screen is on the Nvidia and right screen is on the Intel with no problems. However in ubuntu 14.04 it just wont work!! :(

What I get is the right screen (the on-board intel) works fine but the left one will just not come on not matter what I do. Have followed numours guides and currently have the 340 nvidia driver installed but just can't get it to work. The nvidia settings thing says I can switch it on, lists it as performance mode, but when I try to do so it gives me a blank error and does nothing.

I am banging my head against a wall. Anyone have any ideas please?

---

### Post by QIII on 2014-10-16
Before you do anything else, make a request in the resolution center to get help re-associating with your old account.  I'm going to close this thread for the time being.  If you get your old name back, start a new thread because this one will not be associated with your old account.  That might be confusing.

If you don't want your old account name, use the Report Post button, explain why this was closed and ask for it to be reopened.

Cheers!

---

### Post by Irihapeti on 2014-10-16
Thread re-opened at OP's request.

---

### Post by James_Hughes on 2014-10-20
Since I have tried Mint with the same effect thought I would post the details I put in their forum. No one seems to be able to help yet :(

I have a GA-B85-HD3 motherboard which has an onboard intel HD graphics card, in additon I have an Nvidia GTX 750. I currently have two 22" 1680 x 1050 monitors, one in each card. In windows both work perfectly at the same time, but when I reboot to mint I can only get the one that used the onboard intel graphics to work.

I have tried many, many, methods of installing the nvidia drivers from the edgers PPA through to using the 340 driver downloads from the offical site but in each case the only thing I can achive is for the intel to stop working properly. Never have I managed to get the nvidia card to switch on or for both monitors to be on at the same time. 

My lshw -C video output shows both cards: ```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)

```

But my Xrandr output only shows the ports for the intel HD:
```
Screen 0: minimum 8 x 8, current 1680 x 1050, maximum 32767 x 32767
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VGA1 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0*+
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

Have been banging my head against a wall for days now with this and still can not get it to use both cards. Have reinstalled several times but still no joy. Every time I install, either via apt or manually it says the drivers for nvidia are not in use. Can anyone lend me a hand please?

---

### Post by James_Hughes on 2014-10-22
No one can help?

---

### Post by Les_Green on 2014-10-24
I have same card and am using the DVI and the HDMI (with adapter cable) to drive two moniotrs in windows, but can not seem to make it work in Ubuntu

---

### Post by Vladlenin5000 on 2014-10-24
You can't have monitors in different cards. Go to BIOS and make sure only the PCIe one (Nvidia) is selected, not "onboard" or even "AUTO". Then, connect both to the Nvidia card only and install the recommended drivers.

---

### Post by James_Hughes on 2014-10-25
> **Vladlenin5000 said:**
> You can't have monitors in different cards. Go to BIOS and make sure only the PCIe one (Nvidia) is selected, not "onboard" or even "AUTO". Then, connect both to the Nvidia card only and install the recommended drivers.

I'm sorry but this is simply untrue. I have used dual cards in linux before on other systems and others have reported this same configuration being possible.

My monitors are both VGA, as such without a signal coverter (which are unreliable at best) it is impossible to plug both monitors into the Nvidia (it only has a single analog output)

---

### Post by oldfred on 2014-10-25
If nVidia cannot see EDID it cannot set correct parameters for your monitor.

[http://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor](http://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor)

 Dual nVidia cards - 2013
[http://ubuntuforums.org/showthread.php?t=2129190](http://ubuntuforums.org/showthread.php?t=2129190)

You may have to revert to the old way or manually setting it up?

 With xorg.conf - older 
[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)

[http://christian.amsuess.com/tools/arandr/](http://christian.amsuess.com/tools/arandr/)

      
 Maxwell 750 
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)

---

### Post by markohrastovec on 2014-12-17
Take a lookt at [http://ubuntuforums.org/showthread.php?t=2229746&p=13188982#post13188982](http://ubuntuforums.org/showthread.php?t=2229746&p=13188982#post13188982)

---


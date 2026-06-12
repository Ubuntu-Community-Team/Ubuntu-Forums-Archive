---
title: "External monitor randomly stops working"
date: 2017-02-21
forum: Hardware
---

### Post by Only1KW on 2017-02-21
I have a laptop (Dell Latitude E7440) with a dock and an external monitor connected to the VGA port on the dock.  Initially when using the system, I am able to use the monitor as a secondary display with no issues.  However, every so often, after docking up my laptop and going to the "Display" utility to enable the display, I can no longer find my monitor listed there.  The only way I can find to get the monitor to show up again is to reboot the laptop, which is kind of a heavy handed solution.  Putting the laptop to sleep doesn't fix the problem, and (from my experience) is potentially the trigger I am performing that is causing the external monitor from no longer showing up.

I have a VGA and DVI connector on the docking station, and neither of those work when I hit this issue.  I have a HDMI and mini-DVI connector built in to the laptop and they continue to both work just fine.  I also have a USB keyboard and mouse and Ethernet cable attached to the dock and those also continue to work just fine.  I also have a Display Port on the docking station, but I don't have the necessary hardware to test it.  

Here is what I believe to be some relevant output from " grep -i intel /var/log/Xorg.0.log"
```
[1264140.582] (II) intel(0): Enabled output DP1-1
[1264140.583] (II) intel(0): Enabled output DP1-2
[1264140.583] (II) intel(0): Enabled output DP1-3
[1329817.495] (II) intel(0): resizing framebuffer to 3200x1080
[1329817.585] (II) intel(0): switch to mode 1280x1024@60.0 on DP1-3 using pipe 1, position (1920, 0), rotation normal, reflection none
[1329848.452] (EE) intel(0): Failed to prepare CRTC for page flipping, disabling TearFree
[1329848.452] (EE) intel(0): sna_mode_redisplay: page flipping failed, disabling CRTC:30 (pipe=1)
[1329848.452] (II) intel(0): Disabled output DP1-1
[1329848.452] (II) intel(0): Disabled output DP1-2
[1329848.452] (II) intel(0): Disabled output DP1-3
[1329848.506] (II) intel(0): resizing framebuffer to 1920x1080
[1331321.840] (II) intel(0): Enabled output DP1-1
[1331321.841] (II) intel(0): Enabled output DP1-2
[1331321.841] (II) intel(0): Enabled output DP1-3
[1333676.964] (II) intel(0): Disabled output DP1-1
[1333676.964] (II) intel(0): Disabled output DP1-2
[1333676.964] (II) intel(0): Disabled output DP1-3
[1337474.481] (II) intel(0): Enabled output DP1-1
[1337474.484] (II) intel(0): Enabled output DP1-2
[1337474.485] (II) intel(0): Enabled output DP1-3
[1340003.576] (II) intel(0): resizing framebuffer to 3200x1080
[1340003.604] (II) intel(0): switch to mode 1280x1024@60.0 on DP1-3 using pipe 1, position (1920, 0), rotation normal, reflection none
[1359576.769] (II) intel(0): Disabled output DP1-1
[1359576.773] (II) intel(0): Disabled output DP1-2
[1359576.773] (II) intel(0): Disabled output DP1-3
[1359577.018] (II) intel(0): resizing framebuffer to 1920x1080

```

You can see the three external ports become enabled and disabled, and I believe this corresponds to me docking and undocking my laptop.  You can also see when I connect my 1280x1024 external monitor to the VGA port.  For some reason, the enabling of the DP1 ports seems to stop happening when I hit this issue when I dock again.  Any idea how I manually trigger the outputs to get rescanned?

Some other relevant output (while the laptop is in the failing state):
```

username@host:~$ xrandr --listproviders
Providers: number : 1
Provider 0: id: 0x48 cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 8 associated providers: 0 name:Intel

username@host:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 309mm x 173mm
   1920x1080     60.05*+  59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1368x768      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1280x720      60.00  
   1024x768      60.00  
   1024x576      60.00  
   960x540       60.00  
   800x600       60.32    56.25  
   864x486       60.00  
   640x480       59.94  
   720x405       60.00  
   640x360       60.00  
DP1 disconnected (normal left inverted right x axis y axis)
DP1-1 disconnected (normal left inverted right x axis y axis)
DP1-2 disconnected (normal left inverted right x axis y axis)
DP1-3 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)


username@host:~$ lspci | grep -i intel
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I218-LM (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)


username@host:~$ uname -a
Linux host 4.6.0-040600-generic #201606100558 SMP Fri Jun 10 10:01:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux



```

---

### Post by Only1KW on 2017-02-21
Update: I found [http://askubuntu.com/questions/150879/can-i-force-vga-signal-output-even-when-xrandr-shows-disconnected](http://askubuntu.com/questions/150879/can-i-force-vga-signal-output-even-when-xrandr-shows-disconnected) and tried following the example in the accepted answer, but if fails for me:

```

username@host:~$ xrandr --addmode DP1-3 1280x1024
username@host:~$ xrandr --output DP1-3 --mode 1280x1024 --right-of eDP1
xrandr: Configure crtc 1 failed

```

Following other suggestions on the web, I ran "xrandr --verbose" to see which CRTCs are listed for DP1-3, and saw "0 1 2".  However, explicitly calling "xrandr --output DP1-3 --crtc" for all three options all fail in the same manner.  So still looking for help.

---


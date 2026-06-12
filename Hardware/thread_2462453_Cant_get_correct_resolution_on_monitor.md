---
title: "Cant get correct resolution on monitor"
date: 2021-05-21
forum: Hardware
---

### Post by prismrivers on 2021-05-21
I have a Tuxedo XP-1610, running ubuntu 20.04, used as a development machine with 3 external monitors.
I recently got tricked into updating nvidia drivers (thank you, apt...). Before I was using 440, which was working perfectly. Now I am on 465, but I also tried 460 and 450, it makes no difference.
440 just seems to have been erradicated from existance, the driver tool (software-properties-gtk --open-tab=4) does not offer it anymore. I tried to install it from some nvidia-ppa as well, which also just got me a broken 460. I could not find a run file from nvidia for it,
though I am not sure how they can even be installed, I tried a 430 file but that just broke the driver completely.
If there were some way to go back to 440 all my problems would be solved, but after search for hours I cant see any.

The current 465 is installed via the driver tool, after apt upgrade just broke the driver.

One of my monitors runs in 1920x1080, but it should be 2560x1440.
I have two of these monitors, identical model. Definitely support that resolution. One works fine, the other gets the low resolution.
The correct resolution is completely hidden from xrandr and arandr, it just cannot be selected at all.
I tried to add the resolution by hand via xrandr like this: [https://unix.stackexchange.com/a/227894](https://unix.stackexchange.com/a/227894) but that just gives some error message that google tells me is because xrandr and nvidia dont like each other very much anymore.

This likely has something to do with the way it is connected to the laptop. The working one is connected hdmi-hdmi, the broken one mini-displayport (laptop) to hdmi (monitor).
I have a 3rd monitor connected via usb3 (laptop) to hdmi (monitor), which works fine. If I swap the connections, so the problem monitor is connected via usb3 it does offer the desired resolution but when it is selected the monitor just says "bad preset mode" and just stays black.

I am out of ideas how I could fix this, somehow the one working driver is not available anymore and I have no other options to connect this monitor to the laptop, the laptop does not have more ports to try.
Is there nothing that can be done? :(

EDIT:
So I tried to swap the cables again and somehow now the beaviour is a bit different. When I use the usb3-hdmi cable on the problem-monitor it works, but now the monitor that was on usb3 has the issue of only showing 1920x1080.
Seems the issue is somehow relating to mini-displayport, the adapter cable or something like that.

---

### Post by TheFu on 2021-05-21
> **prismrivers said:**
>   somehow relating to mini-displayport, the adapter cable or something like that.

I have a DisplayPort --> VGA adapter. It was bought specifically to get 1920x1200 resolution, but it only advertises 1920x1080 over the EDID.  I had to manually get the EDID information and tell the nvidia drivers to use that instead.  I placed the raw EDID data into a file:  /etc/X11/xorg-monitor.dell-2412m.edid.raw
The exact name isn't important, just that it can be pointed at in an xorg conf file later.

I don't recall all the commands, but probably posted them in these forums about 2 yrs ago.  edidtool?  Maybe that's the command to get the EDID data for a monitor.  Then I had to manually create a file in /etc/X11/xorg.conf.d/  I called it 20-nvidia.conf, but that isn't important.
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName "GeForce GT 1030"
    # Option "UseEDID" "False"
    Option "UseDisplayDevice" "DFP-0"
**    Option "CustomEDID" "DFP-0:/etc/X11/xorg-monitor.dell-2412m.edid.raw"**
    # Option      "ModeDebug"
EndSection
```
Other sections are necessary and I manually added plenty of modelines with timings to make a number of resolutions available.

I'm not running 20.04. Still on 18.04 here and I don't use Wayland.
If you do some research and ask specific questions, I may be able to help, but I didn't take great notes at the time and once it was working, it has always worked.  The sad thing was that older GPUs never had any issue driving the monitor correctly through VGA connections. It was just after nvidia dropped all support for my old GPU and Nouveu refused to support the 1200p resolution that I spent the $70 on a new card (which I really didn't want).

---

### Post by prismrivers on 2021-05-25
Sorry for the late reply, this is my work laptop and there was a long weekend.
Thanks, I will try that.

I've ordered a new cable over the weekend, mini displayport to displayport. When I use that on the problem monitor that one works and instead one of the other monitors does this vertical image shift.

I'll try around more with different combinations and your EDID idea. Sigh.

[IMG]https://i.imgur.com/6D0pkRb.jpg[/IMG]

EDIT:

With the new adapter I found a combination of monitor-connections that appears to work. I'll go with that...

---


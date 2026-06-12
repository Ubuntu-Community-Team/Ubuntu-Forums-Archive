---
title: "External display resolution wrong after 8.04 upgrade"
date: 2008-06-27
forum: Hardware
---

### Post by atthecoast on 2008-06-27
I have a T60p Thinkpad with the ATI card. I have been running 7.10 and previous Ubuntu with an external 1280x1024 display and the native 1600x1200 display. All was fine.

Yesterday I upgraded to 8.04 yesterday and now in the external monitor will only display 1024x768. I've spent several hours with google and fussing with xorg.conf but no luck

I would really appreciate some help getting this working as it did before. It appears there is a new version of xorg stuff installed in 8.04. My old xorg.conf file does not work to give higher resolution on external display.

I am using the proprietary ATI accelerated graphics driver as recommended during the install. (Note: This was a scratch install of 8.04 just preserving my /home directory.)

lspci shows:
```
01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5200]
```
Here is tail of my xorg.conf file. I added the "option mode2" line based on information found on the web to try and force resolution of external display but this did not work. Other than that this was working with past two Ubuntu releases on the same hardware.

```
Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal,reverse"
        Option      "ForceMonitors" "lvds,crt1"
        Option      "EnableMonitor" "auto"
        Option      "Mode2" "1280x1024"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth     24
        SubSection      "Display"
                Modes   "1600x1200"
        EndSubsection
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection
```

---

### Post by atthecoast on 2008-07-07
I have continued to experiment with getting the second display to run at full resolution (1280 x 1024) and still no luck on that. I did try removing the ATI accelerated graphics driver. What I found then is that when trying to set screen resolution I could detect the displays and the system recognized the make of the external displays and would show me both the laptop display and external display. I was then able to run the external display at higher resolution as I desire. But this would now only work in a "clone display" mode, and I believe the built in laptop display also dropped resolution lower. I don't recall for sure if that was the case, but as I was not able to run other than cloned display mode this was of no use. I went back to the ATI proprietary driver and can now use the secondary display such that the desktop is one large surface, but cannot drive the secondary display at high resolution. When setting resolution (System -> Preferences -> Screen Resolution) this also shows the monitor as "Unknown".

---

### Post by Odrodzona-Sarmacja on 2008-07-09
I had similiar experiences with nvidia binary driver. Installing nvidia-settings solved my issues with display. As I noticed this tool edited xorg.conf file and added entire entries for my nvidia card. My advice would be to look for a similiar ati tool to change the card settings for xorg.conf. Good luck!

---

### Post by atthecoast on 2008-07-14
Regarding running a utility to modify the xorg.conf file, this is exactly what I did with the previous two versions of Ubuntu before 8.04. With the identical hardware, after a clean install of either of those versions I executed the following two commands and I had dual monitors working with high resolution on both, and different resolutions on both displays.
```
aticonfig --dtop=horizontal,reverse --force-monitor=lvds,crt1 --enable-monitor=lvds,crt1

aticonfig --enable-monitor=auto
```
So some of my confusion is why something so simple stopped working with the 8.04 release. I had the foresight to save my old xorg.conf file and dropping that in also doesn't work.

---


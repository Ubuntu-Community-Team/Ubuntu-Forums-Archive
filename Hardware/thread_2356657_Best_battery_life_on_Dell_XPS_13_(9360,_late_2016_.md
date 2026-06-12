---
title: "Best battery life on Dell XPS 13 (9360, late 2016 model)"
date: 2017-03-25
forum: Hardware
---

### Post by sola on 2017-03-25
I have the XSP 13 9360, FHD, 8GB, 256GB running on Ubuntu 16.04.2.

 I get about 6-10 hours with light web browsing and watching youtube videos + videos from my NAS (about ~5-10W power draw with Chromium and light web browsing).

At a recent measurement, I got 9 hours with ~3hrs of light web browsing and ~6hrs of video watching with Kodi from a remote SMB drive accessed via wifi (most of the videos are high-profile, 1080p H264, ~50min 720p DivX) . Screen backlight usually near to minimum because this was in the afternoon and night + I prefer lower screen brightness in general.

This is mostly acceptable but I would like to tune the battery life to the maximum.


[SIZE=5]**I have done these already**[/SIZE]


[SIZE=3]**Installed TLP**
[/SIZE]
for generally optimize power usage on battery. I updated it to v0.9 from its own PPA.

I also set these in /etc/default/tlp:

 CPU_SCALING_GOVERNOR_ON_BAT=powersave
SOUND_POWER_SAVE_ON_BAT=1


[SIZE=3][B]Installed the 4.11 rc1 kernel
[/B][/SIZE]
Install it with Ukuu (easiest way and you also get Ubuntu patches)
This should take care of the NVMe power drain since pre-4.11 kernels don't have NVMe power management at all


[B][SIZE=3]Installed the latest Intel video driver
[/SIZE][/B]
I used the &#8220;Intel Graphics Installer for Linux&#8221;. This should take care of the necessary firmware items as well (huc, guc...etc)
[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)


[B][SIZE=3]Added kernel parameters for the Intel video driver
[/SIZE][/B]
[https://wiki.archlinux.org/index.php/Dell_XPS_13_(9360)](https://wiki.archlinux.org/index.php/Dell_XPS_13_(9360))

Notes here:
- don't forget update-initramfs after you added the config values
- the "enable_huc" parameter seems to be invalid, you will see a boot message about it if you check it with dmesg

**[SIZE=3]Installed Kodi for watching videos[/SIZE]**

For watching videos in hw-accelerated way. Kodi uses vaapi by default whenever possible so much lower power drain.

Note: This seems to be the best way to play from SMB shares on Linux since it is practically stutter free on my home network (wifi), while 1080p H264 was stuttering with the Ubuntu built-in Videos app.

[B][SIZE=3]Switched to Chromium for browsing
[/SIZE][/B]
Seems like it draws much less power on the Javascript-heavy web pages I view regularly (less than the default installed Firefox).

I will play with Firefox multi-process later, I hope I can bring down power draw there as well.


[SIZE=3]**Deactivated Bluetooth**[/SIZE]

I don't use it most of time. Can be enabled/disabled simply by using the panel applet, next to the wifi icon.


[SIZE=3][B]Deactivated keyboard backlight when not needed
[/B][/SIZE]
I don't need this most of the time but it seems to be quite a power hog. At least a 0.5W gain from average brightness to zero.



[B][SIZE=4][SIZE=5]I also intend to try to configure these[/SIZE]
[/SIZE][/B]

[B][SIZE=3]Configure hw-accelerated video for Chrome, Firefox, VLC
[/SIZE][/B]
VAAPI and VDPAU usage in the browser for hw-accelerated Youtube watching in the browser
[https://oded.ninja/2016/10/30/optimizing-your-linux-distro-ninja-level/](https://oded.ninja/2016/10/30/optimizing-your-linux-distro-ninja-level/)

With this, Youtube videos would consume much less battery. Currently, if battery life is important, I watch Youtube videos via the Kodi Youtube plugin (which plays hw-accelerated)

[SIZE=3][B]Move /tmp to a tmpfs drive 
[/B][/SIZE]
So that the temporary files of the web browsers stay on a memory drive, hopefully further lowering power draw while browsing.

[https://oded.ninja/2016/10/30/optimizing-your-linux-distro-ninja-level/](https://oded.ninja/2016/10/30/optimizing-your-linux-distro-ninja-level/)

I am not sure this will result in a lot of savings.

[SIZE=3][B]Investigate wifi power-draw
[/B][/SIZE]
Seems like the Killer/Atheros wifi consumes 1.5W even if there is no network traffic (according to PowerTop). Maybe the power management is not activated at all on the driver.

Let me know if you know how to investigate and improve this.


[SIZE=3]**Others**[/SIZE] 

Let me know if you know any further Ubuntu / Linux power optimizations I could use on this machine.

Would be nice to get it closer to thw battery life under Windows.

---

### Post by TheFu on 2017-03-25
Turn down the display brightness!!!   On my FHD system that is the difference between 6 hrs and 11 hrs.
Don't use Kodi.  Use mpv.  Kodi is a CPU hog when it isn't playing videos.

I don't really try to get more than about 6 hrs from my setup. It is only an i3, so I do most things remote and only use this laptop as a remote display. That way, I don't have to settle for laptop performance or need an expensive laptop upgrade after a few years.  Upgrading a desktop is 5x more cost effective, IMHO.  But my work required connectivity to other systems, so doing it all on a laptop isn't required or expected.  Without networking, my job cannot happen.

If you want a lighter browser, use dillo.  Chromium is a hog too. Dillo isn't good for everything, but for general use, non-video, non-HTTPS stuff, it works great.

---


---
title: "At wits end - Kodi and AMD Radeon"
date: 2015-10-16
forum: Hardware
---

### Post by Metallinut on 2015-10-16
I've almost had it, and am throwing this post out as a last ditch effort.

BLUF: I cannot get anything more than very poor performance for mpeg2 decoding in Kodi.

Background:
System: Shuttle XS35V3 ([http://global.shuttle.com/news/productsDetail?productId=1586](http://global.shuttle.com/news/productsDetail?productId=1586))
Graphics: Radeon HD 6430M
OS: XUbuntu 14.04.03
Kodi: 15.1 Git:d496682
AMD driver: Downloaded and installed from the website, following this guide: wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide

I have a MythTV backend that I connect to with the MythTV PVR plugin. Everything works from other front ends.

H.264 videos play fine, no problem. And the menu system is smooth as silk. But when watching LiveTV or recordings from Myth (MPEG2), I get unwatchable stuttered video. The codec OSD in Kodi shows dc:ff-mpeg2video - does this mean it's not using hardware acceleration? But within seconds of playing video, the drop and skip counts of the video are in the several hundreds.

The driver appears to have been installed properly:
```
$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6430M
OpenGL version string: 4.5.13399 Compatibility Profile Context 15.20.1013
```

Now I don't know much about VAAPI vs. VDPAU, but I saw something somewhere that looked like AMD had better support with VAAPI. In Kodi, I have vaapi hardware acceleration enabled for all available video formats. And it would appear that VAAPI is functioning properly as well:
```
$ vainfo
libva info: VA-API version 0.35.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_x64-linux-gnu/dri/fglrx_drv_video.so
libva info: Found init function __vaDriverInit_0_33
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.35 (libva 1.3.0)
vainfo: Driver version: AMD MMD 1.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileMPEG4Simple            : VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    : VAEntrypointVLD
      VAProfileMPEG4Main              : VAEntrypointVLD
      VAProfileH264Baseline           : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Simple              : VAEntrypointVLD
      VAProfileVC1Main                : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD 
```

Is there a separate va driver I need to install?

Does anyone have mythTV mpeg2 working on a system like this? I think I'm really close except for this last piece!!!

---

### Post by TheFu on 2015-10-16
I always used VDPAU on my E350 APU. The CPU couldn't handle 720p or higher resolutions without it.  That machine has been repurposed for network routing, so it doesn't have any Linux on it anymore. A raspberry-pi v2 took over the Kodi job.

I don't know anything about MythTV, but have been using Kodi and xbmc before that for 2+ yrs as a playback device.

Don't recall which PPA I used, sorry, but I **never** install GPU drivers with a direct download under Linux. fglrx was the package name and there were some specific settings to make it work with the onboard RADEON thru aticonfig. The trick is that aticonfig cannot be run when X/Windows is running. Use fglrxinfo to see driver info.

Hope this info isn't outdated.  It could be, so use at your own risk.

If you are new to Linux, learn that newer isn't always better.  Staying with the stable released software will make your  life happier.  Using alpha code, like a nightly wuold be is asking for issues.

---


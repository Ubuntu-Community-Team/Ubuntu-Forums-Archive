---
title: "DVI Madness"
date: 2009-11-01
forum: Hardware
---

### Post by j2fraser on 2009-11-01
I recently purchased a Dell 2408wfp, which is a great display, except that I am having incredible problems getting the power management to work appropriately.

I have connected the display with the DVI-D Single Link cable that came with the monitor to my ATI Radeon RV380 (X600) DVI-I port, and am running it at 1900x1200, 60Hz with restricted drivers (fglrx 8.47.3) in Hardy. Whenever the monitor is powered off, or goes into sleep mode, it will not "wake," or recognize that the system is sending it a display signal, on being powered up, or by keyboard or mouse input -- in either Ubuntu or Windows XP. After doing a bit of reading, I have found that this is a common problem amongst many monitors, and it seems to be related to some "older" video cards (some people with Nvidia cards also report similar problems, although my impression is that it is more common amongst people using ATI cards).

Ubuntu/Linux Workaround: I have discovered that if I change consoles (Ctrl-Alt-Fn, where Fn is one of the function keys -- say 1-6, as 7 seems to be where my current X session always lives -- and then back to Ctrl-Alt-F7) I can restore the display from "sleep." Restarting X (Ctrl-Alt-Backspace) also works, although then you lose whatever you were working on...

Windows XP Workaround: Some people have success with the latest version of ATI Catalyst Control Centre / Drivers (didn't work for me). Some people also indicate that there is a third party application you can use to set hotkeys which will wake the display by (I think) restarting the driver. The only "solution" I have found is a hard reboot -- not great for retaining whatever you might have been working on.

I wonder if the problem is related to the physical connection between the monitor and the video card. The DVI port on my X600 appears to be DVI-I Dual Link (see [http://www.datapro.net/techinfo/dvi_info.html]("http://http://www.datapro.net/techinfo/dvi_info.html")), while the DVI port on the monitor is actually DVI-D Single Link (it looks like a DVI-D Dual Link port, but I believe it is internally crippled). Anybody have any sense if changing my DVI cable will help?

---

### Post by j2fraser on 2009-11-02
Bump?

---


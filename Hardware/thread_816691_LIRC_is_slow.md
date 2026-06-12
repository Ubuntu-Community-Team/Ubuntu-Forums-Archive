---
title: "LIRC is slow"
date: 2008-06-02
forum: Hardware
---

### Post by spiderworm on 2008-06-02
I finally got a remote for my MythTV box the bluetooth keyboard i was using. Everything works perfectly, but LIRC seems sloooow. I've tested the speed with irw and it's slow, but responds more quickly than the mythfrontend. Mythfrontend takes maybe half a second to respond to the remote button presses. I hooked the bluetooth keyboard back up to test mythfrontend, and it responds instantly with the keyboard.

Somebody mentioned that they've noticed slowness with lirc and more recent kernels. Does anyone have this problem and/or a resolution?

distro: Ubuntu Hardy Heron

kernel: 2.6.24-17-generic

lircd --version: lircd 0.8.3pre1

mythfrontend --version:

MythTV Version : 16838
MythTV Branch : branches/release-0-21-fixes
Library API : 0.21.20080304-1
Network Protocol : 40
Options compiled in:
linux profile using_oss using_alsa using_arts using_jack using_backend using_dbox2 using_dvb using_firewire using_frontend using_hdhomerun using_iptv using_ivtv using_joystick_menu using_libfftw3 using_lirc using_opengl_vsync using_opengl_video using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmcw using_xvmc_vld using_glx_proc_addr_arb using_bindings_perl using_bindings_python using_opengl using_ffmpeg_threads using_libavc_5_3 using_live

---

### Post by jobowyer on 2008-10-08
Having this same issue. Using a plane jane microsoft usb wireless (not bluetooth) keyboard and the buttons are quick. My usb remote is the streamzap. Did you get a solution to this?

---


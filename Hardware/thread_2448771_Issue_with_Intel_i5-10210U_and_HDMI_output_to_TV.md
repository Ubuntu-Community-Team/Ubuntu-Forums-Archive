---
title: "Issue with Intel i5-10210U and HDMI output to TV"
date: 2020-08-13
forum: Hardware
---

### Post by jwilkicki on 2020-08-13
I'm having a problem getting my Zotac C-box barebones build to  display on a Vizio 4K TV.  I have already confirmed that the HDMI output  works by doing the initial setup with a traditional Dell monitor over  HDMI and it displays fine with the shipping 5.4 kerne;.  I also see the  BIOS splash (not Plymouth) when the TV is on and I reboot the machine,  so I'm confident the hardware is okay and connected to the right inputs.
 When the machine boots, I see the BIOS splash on the TV, then a quick flash of  white text that I can't read and then the TV claims it doesn't have a  signal.  I checked the output as best as I can and I think EDID  information is coming from the TV.  I've tried switching between Wayland  and plain Xorg and, at least with Xorg, if the TV is on at the time the  box boots, I see EDID data from the monitor.  One puzzle is it seems to  come in on DP-1 instead of something that seems like HDMI, but I've  confirmed I'm not using the Displayport.

 As far as I can tell from dmesg and lsmod, it looks like the modules  are loading and something is detected.  Somewhat related, ALSA seems to  have mixers for the HDMI port (PulseAudio can't seem to find it, but  that's another post).  Curiously, it also looks like gdm3 hasn't  crashed; it appears to be running.  There's just no signal to the TV.
 As mentioned above, I've tried switching between Wayland and Xorg.  I  tried forcing Xorg to use the Intel device over vesa or anything else.   I've tried to boot the i915 driver with nomodeset.  I've upgraded the  kernel to 5.8 from the kernel mainline builds to see if there might be a  new driver or bugfix. I'm used to debugging xorg errors but Wayland in  combination with systemd is a new beast for me.
 Here's some output from the usual diagnostics I've tried:
 $ lspci # Including the whole output in case the chipset information is important
00:00.0 Host bridge: Intel Corporation Device 9b61 (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics (rev 02)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6                                                                                                   th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Comet Lake Thermal Subsy                                                                                                   tem
00:14.0 USB controller: Intel Corporation Device 02ed
00:14.2 RAM memory: Intel Corporation Device 02ef
00:14.3 Network controller: Intel Corporation Wireless-AC 9462
00:16.0 Communication controller: Intel Corporation Comet Lake Management Engine                                                                                                    Interface
00:17.0 SATA controller: Intel Corporation Comet Lake SATA AHCI Controller
00:1d.0 PCI bridge: Intel Corporation Device 02b1 (rev f0)
00:1d.3 PCI bridge: Intel Corporation Device 02b3 (rev f0)
00:1d.4 PCI bridge: Intel Corporation Device 02b4 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 0284
00:1f.3 Audio device: Intel Corporation Device 02c8
00:1f.4 SMBus: Intel Corporation Device 02a3
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake SPI (flash) C                                                                                                   ontroller
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 P                                                                                                   CI Express Gigabit Ethernet Controller (rev 15)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 P                                                                                                   CI Express Gigabit Ethernet Controller (rev 15)
03:00.0 USB controller: ASMedia Technology Inc. ASM2142 USB 3.1 Host Controller
 The VGA controller is listed as Intel Corporation UHD Graphics (rev 02)
 Here's the output of lsmod, focused on i915:
 $ lsmod | grep i915
i915                 2273280  7
drm_kms_helper        225280  1 i915
cec                    53248  2 drm_kms_helper,i915
i2c_algo_bit           16384  1 i915
drm                   561152  7 drm_kms_helper,i915
video                  49152  1 i915
 I don't seem to get much from the system when Wayland is enabled.  Here's some output when I just had plain Xorg enabled:
 Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): EDID vendor "VIZ", prod id 4149
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Using EDID range info for horizontal sync
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Using EDID range info for vertical refresh
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Printing DDC gathered Modelines:
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "3840x2160"x0.0  297.00  3840 4016 4104 4400  2160 2168 2178 2250 +hsync +vsync (67.5 kHz eP)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "1920x1080"x0.0  297.00  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (135.0 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "1920x1080"x0.0  297.00  1920 2448 2492 2640  1080 1084 1094 1125 +hsync +vsync (112.5 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (II) modeset(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
Aug 11 02:07:09 eitri /usr/lib/gdm3/gdm-x-session[2105]: (--) modeset(0): HDMI max TMDS frequency 300000KHz
 That's just partial output, but seems to indicate the driver knows  something is attached.  I also have debug output turned on in gdm. I  don't entirely know what I'm looking for with Wayland, but I found this  in journalctl:
 Aug 11 02:08:54 eitri gdm3[2474]: GdmSessionWorkerJob: : SessionWorkerJob on pid 2478
Aug 11 02:08:54 eitri gdm3[2474]: GdmSession: setting session to type 'wayland'
Aug 11 02:08:54 eitri gdm3[2474]: GdmLocalDisplayFactory: display status changed: 1
Aug 11 02:08:54 eitri gdm3[2474]: GdmLocalDisplayFactory: received VT change event
Aug 11 02:08:54 eitri gdm3[2474]: GdmLocalDisplayFactory: VT is 1 at startup
Aug 11 02:08:54 eitri gdm-launch-environment][2478]: Enabling debugging
Aug 11 02:08:54 eitri gdm-launch-environment][2478]: GdmSessionWorker: connecting to address: unix:abstract=/tmp/dbus-gGBtsVXe
Aug 11 02:08:54 eitri gdm3[2474]: GdmDBusServer: new connection 0x55b409a21680
Aug 11 02:08:54 eitri gdm3[2474]: GdmSession: Handling new connection from worker
Aug 11 02:08:54 eitri gdm3[2474]: GdmSession: Authenticating new connection
Aug 11 02:08:54 eitri gdm-launch-environment][2478]: accountsservice: Finding a graphical session for user 0
Aug 11 02:08:54 eitri gdm-launch-environment][2478]: accountsservice: Failed to identify the current session
Aug 11 02:08:54 eitri gdm-launch-environment][2478]: accountsservice: ActUserManager: seat unloaded, so trying to set loaded property
Aug 11 02:08:54 eitri gdm-launch-environment][2478]: accountsservice: ActUserManager: Seat wouldn't load, so giving up on it and setting loaded property
Aug 11 02:08:54 eitri gdm-launch-environment][2478]: accountsservice: ActUserManager: already loaded, so not setting loaded property
Aug 11 02:08:54 eitri gdm3[2474]: GdmSession: worker connection is 0x55b409a21680
 I also saw this:
 Aug 11 02:08:54 eitri /usr/lib/gdm3/gdm-wayland-session[2486]: gnome-session-binary[2486]: DEBUG(+): Enabling debugging
Aug 11 02:08:54 eitri gnome-session-binary[2486]: DEBUG(+): Enabling debugging
Aug 11 02:08:54 eitri /usr/lib/gdm3/gdm-wayland-session[2486]: gnome-session-binary[2486]: GLib-GIO-DEBUG(+): _g_io_module_get_default: Found default implementation dconf (DConfSettingsBac>
Aug 11 02:08:54 eitri gnome-session-binary[2486]: GLib-GIO-DEBUG(+): _g_io_module_get_default: Found default implementation dconf (DConfSettingsBackend) for ‘gsettings-backend’
Aug 11 02:08:54 eitri systemd[879]: gnome-session.target: Requested dependency OnFailure=gnome-session-failed.target ignored (target units cannot fail).
Aug 11 02:08:54 eitri systemd[879]: [EMAIL="gnome-session@gnome-initial-setup.target"]gnome-session@gnome-initial-setup.target[/EMAIL]: Requested dependency OnFailure=gnome-session-failed.target ignored (target units cannot fail).
Aug 11 02:08:54 eitri systemd[879]: gnome-session-pre.target: Requested dependency OnFailure=gnome-session-shutdown.target ignored (target units cannot fail).
Aug 11 02:08:54 eitri systemd[879]: gnome-session-initialized.target: Requested dependency OnFailure=gnome-session-shutdown.target ignored (target units cannot fail).
Aug 11 02:08:54 eitri systemd[879]: gnome-session-failed.target: Requested dependency OnFailure=gnome-session-shutdown.target ignored (target units cannot fail).
Aug 11 02:08:54 eitri systemd[879]: gnome-session-wayland.target: Requested dependency OnFailure=gnome-session-shutdown.target ignored (target units cannot fail).
Aug 11 02:08:54 eitri systemd[879]: [EMAIL="gnome-session@gnome-login.target"]gnome-session@gnome-login.target[/EMAIL]: Requested dependency OnFailure=gnome-session-failed.target ignored (target units cannot fail).
 I'm not really sure where else to go for output or what configuration  I might need to change.  It seems like this is close to working and I  know kernel 5.4 worked fine with a 'regular' monitor, but I'm not sure  what to do next to troubleshoot or configure something.
 Thanks in advance for any insights.  I'm happy to respond with more debug output or output from a command that might be useful.

---


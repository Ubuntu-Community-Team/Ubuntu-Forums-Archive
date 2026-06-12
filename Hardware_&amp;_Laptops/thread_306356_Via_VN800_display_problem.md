---
title: "Via VN800 display problem"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by karlh on 2006-11-24
I have an Everex nc1500 laptop with a via VN800 northbridge (Unichrome Pro IGP, 1280x800 WXGA LCD) The installer seems to have set up X to use the vesa driver, which makes sense because xserver-xorg-video-via doesn't support the VN800.

Kubuntu works fine, except that I get display garbage that comes up for a couple seconds just as X starts. It shows a band across the upper third of the screen with the Kubuntu logo/progress bar showing up double. All of it in bright pink and other colors.

I can get rid of it by setting X to use the fbdev driver, but that requires me to start vesafb at boot. I did that by adding vga=791 in /boot/grub/menu.lst, but that seems to lock me into 1024x768. That makes some text look pretty bad on my LCD, since it's meant to run at 1280x800 and not 1024x768. There aren't any modes with the right aspect ratio, and that's the highest I can go and still have the output fit on my screen.

I think it would solve my problem if someone could clue me in on how to get fbdev to run at 1280x800.

(or how to get rid of the screen garbage with the vesa driver, for that matter)

I've tried other things, too:

I've built and installed the openchrome driver as per this HOWTO: [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

That driver seems to shut down the display altogether, including the backlight. The output is here:

----------------------------

(II) Open ACPI successful (/var/run/acpid.socket)
(II) APM registered successfully
(II) VIA(0): VIAScreenInit
(II) VIA(0): VIAMapFB
(--) VIA(0): mapping framebuffer @ 0xf0000000 with size 0x4000000
(==) VIA(0): Removed MMIO write-combining range (0xf0000000,0x4000000)
(==) VIA(0): Write-combining range (0xf0000000,0x4000000)
(--) VIA(0): Frame buffer start: 0xaf8f9000, free start: 0xea600 end: 0x4000000
(II) VIA(0): VIAMapMMIO
(--) VIA(0): mapping MMIO @ 0xd1000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xd1200000 with size 0x10000
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VIA(0): VIASave
(II) VIA(0): Primary
(II) VIA(0): TVSave...
(II) VIA(0): VIAWriteMode
(II) VIA(0): ViaModePrimary
(II) VIA(0): ViaModePrimaryVGA
(II) VIA(0): ViaModePrimaryVGA: Setting up 800x600
(II) VIA(0): CrtcHTotal: 0x420
(II) VIA(0): CrtcHDisplay: 0x320
(II) VIA(0): CrtcHBlankStart: 0x320
(II) VIA(0): CrtcHBlankEnd: 0x420
(II) VIA(0): CrtcHSyncStart: 0x348
(II) VIA(0): CrtcHSyncEnd: 0x3C8
(II) VIA(0): CrtcVTotal: 0x274
(II) VIA(0): CrtcVDisplay: 0x258
(II) VIA(0): CrtcVSyncStart: 0x259
(II) VIA(0): CrtcVSyncEnd: 0x25D
(II) VIA(0): CrtcVBlankStart: 0x258
(II) VIA(0): CrtcVBlankEnd: 0x274
(II) VIA(0): Offset: 0x0C8
(II) VIA(0): Fetch Count: 0x0C8
(II) VIA(0): ViaTVPower: Off.
(II) VIA(0): ViaSetPrimaryFIFO
(II) VIA(0): ViaSetPrimaryDotclock to 0x848c04
(II) VIA(0): ViaSetUseExternalClock
(II) VIA(0): VIAAdjustFrame
(II) VIA(0): VIAAdjustFrame
(II) VIA(0): - Blanked
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
(II) VIA(0): [drm] drmOpen failed
(EE) VIA(0): [dri] DRIScreenInit failed.  Disabling DRI.
(II) VIA(0): - Visuals set up
(II) VIA(0): VIAInternalScreenInit
(II) VIA(0): - B & W
(II) VIA(0): Using 1800 lines for offscreen memory.
(II) VIA(0): - Backing store set up
(II) VIA(0): - SW cursor set up
(II) VIA(0): VIAHWCursorInit
(II) VIA(0): - Def Color map set up
(II) VIA(0): VIALoadPalette
(II) VIA(0): - Palette loaded
(**) VIA(0): DPMS enabled
(II) VIA(0): - DPMS set up
(II) VIA(0): - Color maps etc. set up
(II) VIA(0): direct rendering disabled
(WW) VIA(0): [XvMC] Cannot use XvMC without DRI!
(II) VIA(0): - Done
(==) RandR enabled
(EE) AIGLX: Screen 0 is not DRI capable
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
Synaptics DeviceOff called
(II) VIA(0): VIALeaveVT
(II) VIA(0): ViaCursorStore
(EE) VIA(0): ViaCursorStore: stale image left.
(II) VIA(0): VIARestore
(II) VIA(0): ViaDisablePrimaryFIFO
Synaptics DeviceOff called
(II) VIA(0): VIACloseScreen
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

-----------------------

I tried loading the via and drm modules, but the output was the same.

I'd be happy to post any more info if it would help.

Any ideas?

---

### Post by [S2] on 2006-11-28
I had the same problem. I think you have to install the drm module too. See [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) (I just updated it).

---


---
title: "No touchpad with custom kernel (original crashes)"
date: 2010-02-16
forum: Hardware
---

### Post by KGyST on 2010-02-16
I have an Acer 5310 notebook. In this computer, kernels freeze over 2.6.27.4. The problem started with Debian packaged kernels, then continued to exist my over-2.6.27 kernels (but didn't exist in my own 2.6.27.4 kernel), and didn't disappear after installing Karmic Koala. 

After a day or so of usage, the computer feezes, no mouse pointer, no _Caps Lock, etc. /var/messages is usually empty, once the bug came out when a line was being written, and the log file went on with the reboot's first line being written continuig that line.

I decided to compile a kernel from my proved old 2.6.27. Most thing seem to be OK, but no Synaptics touchpad.

Here is a xorg.log logfile with the new kernel (no tuochpad):

[I]..
	(==) intel(0): Silken mouse enabled
	..
	(--) AlpsPS/2 ALPS GlidePoint: no supported touchpad found
	(EE) AlpsPS/2 ALPS GlidePoint Unable to query/initialize Synaptics  hardware.
	(EE) PreInit failed for input device "AlpsPS/2 ALPS GlidePoint"
	(II) UnloadModule: "synaptics"
	(EE) config/hal: NewInputDeviceRequest failed (8)
	(II) config/hal: Adding input device PS/2 Mouse
	(**) PS/2 Mouse: always reports core events
	(**) PS/2 Mouse: Device: "/dev/event6"
	(II) PS/2 Mouse: Found 3 mouse buttons
	(II) PS/2 Mouse: Found x and y relative axes
	(II) PS/2 Mouse: Configuring as mouse
	(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
	(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10,  EmulateWheelTimeout: 200
	(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
	(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
	(**) PS/2 Mouse: (accel) filter chain progression: 2.00
	(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
	(**) PS/2 Mouse: (accel) set acceleration profile 0
	(II) PS/2 Mouse: initialized for relative axes.[/I]

And with a package-based with working touchpad:

[I]..
	(==) intel(0): Silken mouse enabled
	..
	(II) intel(0): Setting screen physical size to 331 x 207
	(II) config/hal: Adding input device PS/2 Mouse
	(II) LoadModule: "evdev"
	(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
	(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
	(**) PS/2 Mouse: always reports core events
	(**) PS/2 Mouse: Device: "/dev/input/event8"
	(II) PS/2 Mouse: Found 3 mouse buttons
	(II) PS/2 Mouse: Found x and y relative axes
	(II) PS/2 Mouse: Configuring as mouse
	(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
	(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10,  EmulateWheelTimeout: 200
	(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
	(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
	(**) PS/2 Mouse: (accel) filter chain progression: 2.00
	(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
	(**) PS/2 Mouse: (accel) set acceleration profile 0
	(II) PS/2 Mouse: initialized for relative axes.
	(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
	(II) LoadModule: "synaptics"
	(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
	(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
	(II) Synaptics touchpad driver version 1.1.2
	(**) Option "Device" "/dev/input/event9"
	(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
	..[/I]

the kernel config file has an 
CONFIG_MOUSE_PS2_SYNAPTICS=y

row, but when making xconfig, i cannot access it (not showing this option).

What can I do?

---


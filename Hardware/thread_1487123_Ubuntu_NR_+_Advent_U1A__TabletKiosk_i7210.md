---
title: "Ubuntu NR + Advent U1A / TabletKiosk i7210?"
date: 2010-05-18
forum: Hardware
---

### Post by Asenath83 on 2010-05-18
Hi guys,

since I cannot find any reasonably current topics regarding this hardware/software combination I thought I'd start a new one. Has anyone recently tried getting Ubuntu (especially Netbook Remix) running on the Advent U1A, which is a rebranded version of the TabletKiosk i7209?

Here be specs:
[http://www.tabletkiosk.com/tkstore/pc/viewPrd.asp?idcategory=35&idproduct=153]("http://www.tabletkiosk.com/tkstore/pc/viewPrd.asp?idcategory=35&idproduct=153")

I know back then when it was released there were issues both with the touch screen and the wireless module but that was 2007ish so does anyone know what the current status is?

EDIT: Of course I mean the i7209!

---

### Post by Asenath83 on 2010-05-20
UPDATE:
I am in the process of installing Ubuntu 10.4 Desktop i386 on my U1A from USB drive, the tablet arrived today.
Basic installation is done, all updates have been pulled as well.

WORKING:
- Mouse buttons on the left
- Touchpad on the right
- Up and Down buttons on the right
- Bluetooth
- USB (error message but it works. The error message is "Error mounting '4.1 GB Filesystem': DBus Error org.gtk.PrivateVolumeMonitor.Failed: An operation is already pending)
- Wired Networking (when booted in docking station - doesn't work when you boot it out of the docking station and then put it in there)
- Headphone Socket

NOT WORKING:
- Touch screen (when I touch it the cursor jumps to the upper left corner and opens the menu - might need tinkering with the Wacom driver?)
- Wireless
- Inbuilt camera
- Inbuilt microphone
- Inbuilt speaker
- SD card slot
- Removing tablet from docking station while running - this causes it to freeze. I guess this has something to do with the CPU throttling you can't switch off in the BIOS.

---

### Post by Asenath83 on 2010-05-20
Okay, I managed to pull some stuff that might help figuring out the touchscreen. I have a USB keyboard with touchpad connected to this right now so you might see those in the list.

xinput --list
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Touchkit HID-USB Touc&#274;&#272;               	id=9	[slave  pointer  (2)]
&#9116;   &#8627; USB keyboard                            	id=11	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB keyboard                            	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
```

dmesg | grep [Ww]acom
doesn't have anything to tell me.

Now checking the Xorg.0.log in /var/log/
I think this is all just the touchpad with the mouse buttons, though I am not sure about the last lines:
```
(II) config/udev: Adding input device Touchkit HID-USB Touc&#274;&#272; (/dev/input/event5)
(**) Touchkit HID-USB Touc&#274;&#272;: Applying InputClass "evdev tablet catchall"
(**) Touchkit HID-USB Touc&#274;&#272;: always reports core events
(**) Touchkit HID-USB Touc&#274;&#272;: Device: "/dev/input/event5"
(II) Touchkit HID-USB Touc&#274;&#272;: Found 3 mouse buttons
(II) Touchkit HID-USB Touc&#274;&#272;: Found absolute axes
(II) Touchkit HID-USB Touc&#274;&#272;: Found x and y absolute axes
(II) Touchkit HID-USB Touc&#274;&#272;: Found absolute tablet.
(II) Touchkit HID-USB Touc&#274;&#272;: Configuring as tablet
(**) Touchkit HID-USB Touc&#274;&#272;: YAxisMapping: buttons 4 and 5
(**) Touchkit HID-USB Touc&#274;&#272;: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Touchkit HID-USB Touc&#274;&#272;" (type: TABLET)
(II) Touchkit HID-USB Touc&#274;&#272;: initialized for absolute axes.
(II) config/udev: Adding input device Touchkit HID-USB Touc&#274;&#272; (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
```

---


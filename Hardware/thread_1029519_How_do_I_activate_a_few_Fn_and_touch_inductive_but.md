---
title: "How do I activate a few Fn and touch inductive buttons with Ubuntu?"
date: 2009-01-03
forum: Hardware
---

### Post by arashiko28 on 2009-01-03
I know it's a long title, but I don't want to make believe I have the answer.
I have a Lenovo Ideapad Y530 and it has a pretty cool touch inductive panel that in Ubuntu is pretty useless :(. Out of 14 buttons, I only have one that is operational. This is the mute button. From left to right there is mute, quick access, dolby surround activation button, play/pause, stop, prev track, next track. When toggled with the switch button, there are equalizer options, jazz, pop, dance, classic and normal, none of them actually works, they are lighted and brighter when touched, but no effect done... The other 2 buttons are volume and the switch, these do work and are regular, no touch sensitive.

Beside that, there a are a few buttons with Fn that doesn't work neither and that used to work on my old laptop. These are:
fn+F5 on/off wireless/bluetooth 
fn+F9 play/pause
fn+F10 stop
fn+F11 prev
fn+F12 next

Is there any workaround for this or perhaps someone experienced can create some sort of file... I don't know, I just want it to be fully functional to get rid of vista with no remorse. 
I tweaked the sound and is a lot better but it's still not getting the juice out of it.

Please, help!!!:D

---

### Post by utnubuuser on 2009-01-03
Have you tried the ThinkWiki? They seem to be up to speed on anything Thinkpad related.

---

### Post by arashiko28 on 2009-01-03
This is not Thinkpad, it's Ideapad and Thinkpads don't have touch sensitive panels. Though from the same manufacturer they offer very different things and are as total stranger one to another. But thanks, I haven't stopped looking I just want an extra help.:D

---

### Post by teaker1s on 2009-01-03
have you tried** xev** to see if touching buttons produces kernel output. if it does it would be possible to set key codes with xmodmap just like a multimedia keyboard with irregular keycodes.

---

### Post by arashiko28 on 2009-01-03
This is what I got with the play/pause button:
> FocusIn event, serial 31, synthetic NO, window 0x4600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x4600001,
    mode NotifyNormal, detail NotifyNonlinear


And this is from the only working button, the mute:
> FocusIn event, serial 31, synthetic NO, window 0x4600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  86  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x4600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x4600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 

I actually don't have a clue of what this may mean, except that all the other keys gave the same data as the play/pause key and the mute button, changes the first two digits every time when activating.

---

### Post by teaker1s on 2009-01-03
I would have expected unknown keycode, I can only suggest that possibly key touch editor 
[https://help.ubuntu.com/community/MultimediaKeys]("https://help.ubuntu.com/community/MultimediaKeys")

or looking at usb and pci hardware and seeing if it's identified as a component.

```
lspci -v
```

```
lsusb
```

---

### Post by arashiko28 on 2009-01-03
> :~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Lenovo Device 3a00
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Lenovo Device 3a02
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d3c00000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at d120 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Lenovo Device 3a02
	Flags: bus master, fast devsel, latency 0
	Memory at d4100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Lenovo Device 3a0a
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at d0c0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Lenovo Device 3a0b
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at d0a0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Lenovo Device 3a09
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d080 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Lenovo Device 3a0c
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at d4204c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo Device 3a0d
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: d2800000-d3bfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 3a0e
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: d1400000-d27fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 3a0f
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=05, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: d0000000-d13fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 3a10
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Lenovo Device 3a14
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at d060 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Lenovo Device 3a15
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d040 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Lenovo Device 3a16
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d020 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Lenovo Device 3a17
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d4204800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
	Memory behind bridge: d4000000-d40fffff
	Capabilities: [50] Subsystem: Lenovo Device 383f

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Lenovo Device 3a19
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Lenovo Device 3a1b
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 220
	I/O ports at d110 [size=8]
	I/O ports at d100 [size=4]
	I/O ports at d0f0 [size=8]
	I/O ports at d0e0 [size=4]
	I/O ports at d000 [size=32]
	Memory at d4204000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Capabilities: [b0] PCIe advanced features <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
	Subsystem: Lenovo Device 3d7e
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at d2800000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 7a-2d-34-fe-ff-54-23-00
	Kernel driver in use: tg3
	Kernel modules: tg3

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
	Subsystem: Intel Corporation Device 1211
	Flags: bus master, fast devsel, latency 0, IRQ 218
	Memory at d1400000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number a2-c6-d8-ff-ff-ea-16-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

06:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Lenovo Device 3d94
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at d4000000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

06:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Lenovo Device 3d90
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at d4000a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

06:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Lenovo Device 3d92
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at d4000900 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

06:03.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: Lenovo Device 3d91
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at d4000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2


I understand very little about all this :s 
For lsusb I got:
> :~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 005: ID 04f2:b105 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Understand so much less:confused: hope you can help me.

---

### Post by teaker1s on 2009-01-04
okay looking at pci I can't see anything touch button related and all I can see on usb is your built in webcam.

I'll have a think about it as it would look to me as if the touch buttons are connected directly to keyboard and in windows use a driver.
have a look on google, then bump thread with a reply and I'll see what I can find

---

### Post by arashiko28 on 2009-01-04
I have checked a few places, and I could "program" one of them though it does nothing anyway. I went to system> preferences> keyboard shortcut and "changed" the play/pause button, but couldn't choose it again for pause. It disabled one for the other.

---

### Post by teaker1s on 2009-01-04
[http://www.linlap.com/wiki/Lenovo+IdeaPad]("http://www.linlap.com/wiki/Lenovo+IdeaPad")
poster states same model with linux mint buttons work, now linux mint used to be ubuntu based,if it still is you may be able to find and install package

---

### Post by arashiko28 on 2009-01-04
> **teaker1s said:**
> [http://www.linlap.com/wiki/Lenovo+IdeaPad]("http://www.linlap.com/wiki/Lenovo+IdeaPad")
poster states same model with linux mint buttons work, now linux mint used to be ubuntu based,if it still is you may be able to find and install package

Where?? It says that the topic doesn't exist anymore...:confused:

I was thinking too about mint, but the last time I tried it, looked so much like windows that was immediately out of my list, though that was when I first tired Linux (7.04) and wanted anything not windows.

---

### Post by starcannon on 2009-01-04
You already found the Keyboard Shortcut menu, so I assumed you mapped all mappable keys using that utility; so the next thing you can do, and indeed how I managed a Touchpad on/off switch for my Asus Eee, is to using gconf-editor to point at applications or scripts that do what you want. I did use Keyboard Shortcuts to get button names to work with, but as suggested there are other methods that may work better.
```
gconf-editor
```
Then go to /apps/metacity/keybinding_commands and put the path to the application or script that you'll be assigning to a key. Then go to /apps/metacity/global_keybindings and assign a key to the same command{number} that you assigned an application or script to in the keybinding_commands area.

Okay now test your key; note that if you use a key or key combo for multiple purposes you may get unexpected results, no results, or sporadic expected resuslts; so make sure each key/combo is used only once :)

GL and have fun.

---

### Post by arashiko28 on 2009-01-04
> **starcannon said:**
> You already found the Keyboard Shortcut menu, so I assumed you mapped all mappable keys using that utility; so the next thing you can do, and indeed how I managed a Touchpad on/off switch for my Asus Eee, is to using gconf-editor to point at applications or scripts that do what you want. I did use Keyboard Shortcuts to get button names to work with, but as suggested there are other methods that may work better.
```
gconf-editor
```
Then go to /apps/metacity/keybinding_commands and put the path to the application or script that you'll be assigning to a key. Then go to /apps/metacity/global_keybindings and assign a key to the same command{number} that you assigned an application or script to in the keybinding_commands area.

Okay now test your key; note that if you use a key or key combo for multiple purposes you may get unexpected results, no results, or sporadic expected resuslts; so make sure each key/combo is used only once :)

GL and have fun.

Jajaja, I did not, as I saw that it wasn't working I stopped messing with it.  For all the rest...
SLOW and calmed english... I'm not an IT, so pretty much of what you said looks like chinese for me...

---

### Post by starcannon on 2009-01-04
heh :) sorry; mmm-kay lemme try a different approach:

I was able to find my key names using the Keyboard Shortcuts application (other methods were described earlier in this thread, and they may be required for your situation); I chose something that was currently disabled and then tried keyboard combinations on it and wrote down the results:
[IMG]http://img513.imageshack.us/img513/6907/keyboardshortcutsbx7.png[/IMG]

Press Alt+F2
Type or copy paste:
```
gconf-editor
```Press the Enter key, or click the Run button.
[IMG]http://img510.imageshack.us/img510/1125/runapplicationgh1.png[/IMG]

The gconf-editor window should now be up.
[IMG]http://www.freeimagehosting.net/uploads/8d92c0015d.png[/IMG]

Then open apps
[IMG]http://img511.imageshack.us/img511/6223/appsyx3.png[/IMG]

Then open metacity
[IMG]http://img206.imageshack.us/img206/4976/metacityrv9.png[/IMG]

Then under keybinding_commands bind an application:
[IMG]http://img175.imageshack.us/img175/8692/enterkeybindingcommandsuj5.png[/IMG]

Then under global_keybindings set your key:
[IMG]http://img136.imageshack.us/img136/125/bindkeyglobalkeybindingcn6.png[/IMG]

Now test your key, for me results were immediate; I did not have to restart the computer, nor did I have to restart the x-server, the changes were on the fly and it made trying different combinations and running down typo's or other mistakes a breeze.

GL and have fun.

---

### Post by arashiko28 on 2009-01-04
Ok, now I know what you mean, the thing is that I don't have any response from these keys when pressed, so I can't tell the command, they're all the same, XF86Audio(Play, Stop)... that changes, but not that it actually works...

---

### Post by starcannon on 2009-01-04
I've done a bit of digging around on google and came up with this thread here in our forums:
[http://ubuntuforums.org/showthread.php?t=870681](http://ubuntuforums.org/showthread.php?t=870681)

[Post #3 ]("http://ubuntuforums.org/showpost.php?p=5460971&postcount=3")claims the buttons to work ootb with Ubuntu, but I've read a bunch of posts where they do not, so anyway, I'll keep looking for awhile, and post back anything I find. All in all that looks like a really sweet laptop, and it will be worth the effort when your done, it even appears that a solution to get the subwoofer working has been found.

Hmm post #10 has this to say about the fn and touch keys:
> **Miscellaneous :**
All the Fn keys seem to work, but the "sensitive" keys don't. It may be a hardware problem because it was malfunctioning under Win***.

Saw your post at [http://lnv.lithium.com/](http://lnv.lithium.com/) while looking for more info on your key mapping, that looks like a great place to request help; I'll look around a bit more.

GL and have fun

---

### Post by arashiko28 on 2009-01-04
> **starcannon said:**
> I've done a bit of digging around on google and came up with this thread here in our forums:
[http://ubuntuforums.org/showthread.php?t=870681](http://ubuntuforums.org/showthread.php?t=870681)

[Post #3 ]("http://ubuntuforums.org/showpost.php?p=5460971&postcount=3")claims the buttons to work ootb with Ubuntu, but I've read a bunch of posts where they do not, so anyway, I'll keep looking for awhile, and post back anything I find. All in all that looks like a really sweet laptop, and it will be worth the effort when your done, it even appears that a solution to get the subwoofer working has been found.

Hmm post #10 has this to say about the fn and touch keys:


Saw your post at [http://lnv.lithium.com/](http://lnv.lithium.com/) while looking for more info on your key mapping, that looks like a great place to request help; I'll look around a bit more.

GL and have fun

Oh yes, it works, acually after installing 8.10, everything goes like a charm, I solved the sound issue a month ago. and I have the subwoofer and can record with my front mics.
the only missing part for getting it fully working under ubuntu is this panel :D

It's not a hardware problem because I don't have that problem. They work pretty well.

---

### Post by arashiko28 on 2009-01-04
I'll try to get a clean output from **xev** so that I think might give some clue.

....................

Edit: update
Here it is, only the dolby and the quick access buttons didn't showed any kind of activity.

> Play/Pause
FocusIn event, serial 34, synthetic NO, window 0x4a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 34, synthetic NO, window 0x4a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x4a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

Stop
FocusIn event, serial 34, synthetic NO, window 0x4a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967239 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


Previous
KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  4294967176 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

Next
KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


Dolby
no change

Quick accces
no change

Mute (sample, this does work)
FocusIn event, serial 34, synthetic NO, window 0x4a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 34, synthetic NO, window 0x4a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x4a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


---

### Post by arashiko28 on 2009-01-05
I'm on the live cd of Linux Mint 6, the buttons does works here, at least the multimedia buttons does, stop does as pause only. For the equalizer buttons they have no function at all.

Is there something useful here that might be taken to be applied in Ubuntu?

---

### Post by teaker1s on 2009-01-05
only thing i can think of is 
```
lsmod
``` may give a clue if there is a module loading for touch buttons.

Otherwise maybe the kernel has been compiled with a driver-asking on linux mint forum may help.

---

### Post by arashiko28 on 2009-02-03
So... after the last few update have come to realize that the touch inductive buttons from the multimedia does works, but only with totem, which makes it a bit difficult since I have problem with that player and the sound. On windows didn't worked with VLC and only with wmp and itunes, but now that windows gone :p, can't compare anymore.
Thanks to all of you that tried to help and contributed, now I know a lot more about linux because of you, so not everything was in vain.

I'm still hoping that this laptop becomes popular enough (though it has caused a few head turns) so that the next version comes with more compatibility features.

"Computers are made to last... Computers without Windows lasts longer!!!:p"
                                                               -Me...

---


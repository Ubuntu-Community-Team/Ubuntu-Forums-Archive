---
title: "Toshiba Portege R700 / R705 Linux Hardware Compatibility Thread"
date: 2010-08-10
forum: Hardware
---

### Post by connect404 on 2010-08-10
Ive recently purchased a number of newly released [Toshiba portege R700-15U]("http://ie.computers.toshiba-europe.com/innovation/series/Port%C3%A9g%C3%A9-R700-Series/1087011/") business laptops. There was (and still is) very little linux related support information available due to it being a very new model so I have started to document the hardware compatibility under ubunutu 10.04. This is not intended to be a review or discussion of the laptop features, but a collation of compatibility info and fixes for this laptop under linux for owners or those looking to to buy one. 

The R705 shares almost all the same components as the R700. It just lacks a number of features (bluetooth? fingerprint reader, express slot?, 5400rpm drive?) present on the R700 so there is no reason why it cant be tracked here also.

Feel free to post updates and I will keep this chart fresh.

[COLOR=Black]Test OS:  Ubuntu 10.04 Lucid Lynx amd64. Alternate installer, for encrypted LVM setup. Apart from that it was a standard install.[/COLOR]
Test Firmware: Initial Release firmware

[COLOR=DarkOrange]
[/COLOR]Legend:[COLOR=DarkOrange]
[COLOR=Green]Works (maybe with a patch or fix)[/COLOR]
A number of small bugs are present,[/COLOR]
[COLOR=Red]Could be a potential deal breaker for someone moving from windows to ubuntu[/COLOR]



[SIZE=2][COLOR=Green]Webcam[/COLOR][/SIZE][SIZE=2]
[/SIZE]
[LIST]
[*]Hardware is detected
[*]Works in Chesse & Skype.
[*]Can adjust the resolution/brightness/settings correctly.
[/LIST]

[SIZE=2][COLOR=Green]Suspend to RAM / Suspend to Disk[/COLOR][/SIZE][SIZE=2]
[/SIZE]
[LIST]
[*]The laptop goes in and out of sleep/hibernate cleanly.
[*]Wifi/LAN comes up automatically on resume.
[*]**Fixed in 2.6.35**[B] [s]If you have an SD card mounted in the slot the laptop WILL NOT suspend to disk or RAM.. the screen blanks out with the fan running and requires a hard reset to get it back.[/s]
[/B]
[*][B]FIXED enough (see acpi script in thread) [s]Brightness is locked after resume. Brightness indicator moves up and down when changed, but doesn't affect the display levels. [/s]
[/B]
[*][B][FIXED:]("http://ubuntuforums.org/showthread.php?p=7661521#post7661521") [s]Even when set to suspend to ram on idle the R700 is hibernating[/s]
[/B]
[/LIST]
[SIZE=2][COLOR=Indigo]
[COLOR=Green]Multi Card Reader[/COLOR][/COLOR][/SIZE][SIZE=2]
[/SIZE]
[LIST]
[*]Tested OK with an SD & SDHC card.
[*]Not an ubuntu specific issue, but I cant boot from the SD card
[/LIST]
[COLOR=Green]
[/COLOR][SIZE=2][COLOR=Green]Express Slot[/COLOR][/SIZE][SIZE=2][COLOR=Green]
[/COLOR][/SIZE]
[LIST]
[*]Shows up in an lspci and is supported under linux
[*]Untested at the moment
[/LIST]
[SIZE=2][COLOR=DarkOrange]
[/COLOR][/SIZE][SIZE=2][COLOR=Red]Fingerprint reader[/COLOR][/SIZE]

[LIST]
[*]**Shows up in lspci, but isn't detected by pam_fprint_enroll or fprint_demo.**
[*][B]No OS drivers exist for the device
[/B]
[/LIST]
  [SIZE=2][COLOR=Green]
[/COLOR][/SIZE][SIZE=2][COLOR=Green]Wifi / Bluetooth[/COLOR][/SIZE][SIZE=2][COLOR=Green]
[/COLOR][/SIZE]
[LIST]
[*]Intel wifi works 100%
[*]Full WEP/WPA/WPA2 support
[*]**Wifi wont turn off/on via keyboard hotkey**
[*]**Wifi status LED will not turn off even with card manually disabled**
[*]Bluetooth works, pairs, transfers files, connects to my bluteooth HID device
[*][B]Even when disabled, bluetooth seems to renable itself sometimes after a reboot or resume from suspend...  still chasing this up. I suspect its still drawing power even when disabled
[/B]
[/LIST]

[SIZE=2][COLOR=Green][COLOR=DarkOrange]Hard Drive[/COLOR][/COLOR][/SIZE]

[LIST]
[*] The hard drive accelerometer/impact sensor/protection system is not supported by hdapsd.
[/LIST]
 [SIZE=2][COLOR=Green]
Touchpad
[/COLOR][/SIZE]
[LIST]
[*]Generally works well.
[*]Two finger scrolling greyed out via the ubuntu mouse settings but can be turned on easily by running a few synclient settings on login to X (I run them automatically on startup)
[/LIST]
```
#!/bin/bash
sleep 10
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48
```
[LIST]
[*]**Touchpad disable button (both keyboard shortcut & dedicated button) do NOT function**
[*]Touchpad automatically disables itself when typing and required no setup
[/LIST]

[SIZE=2][COLOR=Green]Keyboard[/COLOR][/SIZE][SIZE=2][COLOR=Green]
[/COLOR][/SIZE]
[LIST]
[*]2 dedicated hardware buttons (email & web in windows i think) can be assigned to a function via keyboard shortcuts... but they both appear as the same button "Mod4+X"
[*]F1-F12 are the default action, with Fn being secondary
[*]Display switch hotkey works
[*]Most Fn modifiers work fine. Can vol+ & vol-, mute, suspend, numberpad etc
[*]**Touchpad & Display switch Fn modifiers dont function, and are not programmable. Triggering them does not register any type of keypress. Suspect these are hardware set and will never be accessible.**
[*][B]Wifi hotkey only turns Bluetooth module on and off. Could be fixed with some acpi scripting if needed
[/B]
[/LIST]
 [SIZE=2][COLOR=Green]
Sleep&Charge[/COLOR][/SIZE][SIZE=2][COLOR=Green]
[/COLOR][/SIZE]
[LIST]
[*]When enabled in the bois the esata/usb port will charge even when the laptop is not on. This works fine in Ubunutu and the laptop is not woken up.
[/LIST]

[SIZE=2][COLOR=Green]NIC[/COLOR][/SIZE]

[LIST]
[*]Throughput is in line with 1Gb port
[*]When using toshset tool to disable the NIC it cant be re-enabled without going into the bios
[/LIST]
[SIZE=2][COLOR=Green] 
[/COLOR][/SIZE][SIZE=2][COLOR=Green]Display[/COLOR][/SIZE][SIZE=2][COLOR=Green]
[/COLOR][/SIZE]
[LIST]
[*]**FIXED enough (see acpi script in thread) **[s]**Display brightness cannot be changed after the laptop has resumed from a suspend to disk or RAM.**[/s]
[/LIST]
[SIZE=2][COLOR=Green]Video
[/COLOR][/SIZE]
[LIST]
[*]Intel video card is fully supported.
[*]Compiz is on by default and all desktop effects work great
[*]Full SD (720p) playback works 100%
[*]VGA & HDMI outputs are recognized
[*]VGA & HDMI outputs can be configured as secondary or mirrored devices and detect/display correctly.
[*]Have had this plugged into both a TV and LCD monitor and everything works flawlessly.
[*]**After removing the HDMI cable the laptop display goes to full brightness and cant be lowered if you have resumed from a suspend!**
[/LIST]
[SIZE=2][COLOR=Green]
[/COLOR][/SIZE][SIZE=2][COLOR=Red] Battery[/COLOR][/SIZE][SIZE=2][COLOR=Green]
[/COLOR][/SIZE]
[LIST]
[*]**Ubuntu misreports  battery capacity and charge levels.**
[*][B]After a week of testing battery level predictions are still very poor, despite some error correction being performed
[/B]
[*][B]"Ubuntu Power Statistics" (accessible from the battery icon) gives an average of 25% prediction accuracy for both charge and discharge cycles. Less than ideal :)
[/B]
[*]**Full charge predicts a 3****½**[B] - 4hr battery life... but when the laptop gets to 5mins remaining it can still last up to another 1hr.
[/B]
[*][B]Battery reports that after a week of use that it is only capable of 90% original capacity. I suspect this is incorrect too.
[/B]
[*]Despite these issues, the battery still gives 3**½**-4**½** hours of use, its just difficult to predict when it will run out or when its fully charged.
[/LIST]
[SIZE=2][COLOR=Green] [COLOR=DarkOrange]
[COLOR=Green]Audio[/COLOR][/COLOR]
[/COLOR][/SIZE]
[LIST]
[*]Sound playback through speakers works with a clean install of lucid (works in Maverick atm)
[*]HDMI audio output works. This can be switched on and off via volume panel settings
[*]**Headphone & Mic jack do not function**
[*]**Inbuilt mic is muted by default, but works fine when unmuted via **
[*]Fixed in 10.10 (2.6.35 kernel) [s][I built alsa from source]("http://ubuntuforums.org/showthread.php?p=6589810") it fixed the headphone & mic jack issue, but after a kernel update it broke again. Running the script again fixed the issue again[/s]
[/LIST]

For those interested here are some specs:
```

connect404@pez:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device 0007
    Flags: bus master, fast devsel, latency 0, IRQ 35
    Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3050 [size=8]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCIe advanced features <?>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 94727000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:19.0 Ethernet controller: Intel Corporation 82577LC Gigabit Network Connection (rev 06)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at 94700000 (32-bit, non-prefetchable) [size=128K]
    Memory at 94725000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 3020 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [e0] PCIe advanced features <?>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 94726c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 37
    Memory at 94720000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 94600000-946fffff
    Prefetchable memory behind bridge: 000000007c100000-000000007c2fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device 0001
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 94500000-945fffff
    Prefetchable memory behind bridge: 000000007c300000-000000007c4fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device 0001
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 92500000-944fffff
    Prefetchable memory behind bridge: 0000000090400000-00000000923fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device 0001
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: 92400000-924fffff
    Prefetchable memory behind bridge: 000000007c500000-000000007c6fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device 0001
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at 94726800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
    Capabilities: [50] Subsystem: Toshiba America Info Systems Device 0001

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06) (prog-if 01)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 34
    I/O ports at 3048 [size=8]
    I/O ports at 305c [size=4]
    I/O ports at 3040 [size=8]
    I/O ports at 3058 [size=4]
    I/O ports at 3000 [size=32]
    Memory at 94726000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA <?>
    Capabilities: [b0] PCIe advanced features <?>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at 94724000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

01:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 94600000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [800] Advanced Error Reporting <?>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

02:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
    Subsystem: Intel Corporation Device 1301
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Memory at 94500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Device Serial Number c0-c1-01-ff-ff-10-27-00
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

```lsusb
```

 connect404@pez:~$ lsusb
Bus 002 Device 003: ID 0930:0c05 Toshiba Corp. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:58f5 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 08ff:168b AuthenTec, Inc. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```[SIZE=2][COLOR=Green]
[/COLOR][/SIZE]hdparm with the standard 320gb 7200rpm drive[SIZE=2][COLOR=Green]
[/COLOR][/SIZE]```

 connect404@pez:~$ hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   1746 MB in  2.00 seconds = 873.13 MB/sec
 Timing buffered disk reads:  320 MB in  3.01 seconds = 106.36 MB/sec

```[SIZE=2][COLOR=Green]
  [/COLOR][/SIZE][SIZE=2][COLOR=Green]


[/COLOR][/SIZE]

---

### Post by anydroid on 2010-08-11
I read your post on notebookreview.com, thanks for starting this thread.

I've been waiting to get my hands on the [R700-15Q]("http://uk.computers.toshiba-europe.com/innovation/product/Portege-R700-15Q/1089286/") for weeks but Toshiba are (understandably) feeding the market with higher spec'd models first.

Given the importance of Toshiba's "ECO mode" for regulating temp/fans/noise/power consumption in Windows, how does the R700 score on these points under Ubuntu?

Is the [Toshset]("http://www.schwieters.org/toshset/") project deprecated or still of use on the R700?

*Re BIOS: I can't find release notes for B1.30-EC1.30-WIN so it's impossible to know what's been tweaked. I'm a bit disappointed that BIOS updates are coming as Windows executables only.*

---

### Post by connect404 on 2010-08-12
> **anydroid said:**
> I read your post on notebookreview.com, thanks for starting this thread.

I've been waiting to get my hands on the [R700-15Q]("http://uk.computers.toshiba-europe.com/innovation/product/Portege-R700-15Q/1089286/") for weeks but Toshiba are (understandably) feeding the market with higher spec'd models first.

Given the importance of Toshiba's "ECO mode" for regulating temp/fans/noise/power consumption in Windows, how does the R700 score on these points under Ubuntu?

Is the [Toshset]("http://www.schwieters.org/toshset/") project deprecated or still of use on the R700?

*Re BIOS: I can't find release notes for B1.30-EC1.30-WIN so it's impossible to know what's been tweaked. I'm a bit disappointed that BIOS updates are coming as Windows executables only.*

Good luck getting your R700, mine were delayed a couple of times and the supplier ended up getting Toshiba to dispatch them direct to me.

I dont have much to comment on regarding the ECO mode. Though from reports from the notebookreviews thread my battery life seems to be on par with Windows7 users so i can see any major discrepancy without all the toshiba windows tools running.

Had a look in my bios last night and it seems I already have 1.30. Not sure what toshiba is up too here... 

[s]AFAIK toshset uses HAL. I tried both the omnibook module and toshet tools on the laptop but they didnt do anything. Couldn't access extra hotkeys, turn bluetooth on/off etc. Sure there is more investigating to be done, but on the surface they are just too old to support this laptop.[/s]

Toshset does still mostly work on this laptop, not all functions have the desired effect, but its enough to get by.

Im sure youll like your R700, and please update the thread as you get linux issues resolved!

---

### Post by samio chang on 2010-08-25
Thanks for the post! It has been very useful for some one as new to ubuntu as me :D I am using 10.04 on R700 S1330. Regarding the inbuilt microphone, it works for me! I got the mic sound after switched off the microphone mute.

---

### Post by ouilsen on 2010-08-27
Hi all!

What about the built-in UMTS Modem? Is anyone online using Ubuntu and 3G?

---

### Post by fataki on 2010-08-28
> **connect404 said:**
> I
**UPDATE: Toshiba have just release an updated firmware [B1.30-EC1.30-WIN]("http://uk.computers.toshiba-europe.com/innovation/download_bios.jsp?service=UK") . Its and exe so will require a non linux startup disk to install. Will update & test soon.**


1.40 has been released. Downloaded and installed it with Toshiba's update utility before wiping windows.

> 
[SIZE=2][COLOR=Green]Fingerprint reader[/COLOR][/SIZE][SIZE=2][COLOR=Green]
[/COLOR][/SIZE]
[LIST]
[*]Shows up in an lspci and is supported under linux
[*]Have not personally tested it, but can if someone really wants to know.
[*]Read unconfirmed reports that it can be configured.
[/LIST]
  [SIZE=2][COLOR=Green]
[/COLOR][/SIZE]


Shows up in lspci, but isn't detected by pam_fprint_enroll or fprint_demo.

> 
[SIZE=2][COLOR=Green]Keyboard[/COLOR][/SIZE][SIZE=2][COLOR=Green]
[/COLOR][/SIZE]
[LIST]
[*][B]Wifi, Touchpad & Display switch Fn modifiers dont function, and are not programmable. Triggering them does not register any type of keypress. Suspect these are hardware set and will never be accessible.
[/B]
[/LIST]


Can we use one of the dedicated hardware buttons for Display switch?

Scenario: Laptop is connected to external display and laptop display is off. External display is disconnected from laptop, but laptop screen doesn't turn on. Need to switch display back to just laptop before disconnecting external display. Pressing display switch-button should help?

---

### Post by JacquiOh on 2010-08-28
Thanks! This is such a useful post!

I have the 15U as well, and I love it -- apart from the headphones issue and I'm having battery life issues. Not sure what's up there, but I'm starting to think I have a dud battery. I'm only getting about 2.5 hours on Ubuntu and same on W7 even with Eco mode running. That's with nothing but tweetdeck, chrome and notepad/gedit open.

I'm going to try the bios update.

The script for the headphones/mic but I'm a bit worried. Not great with command line yet.

---

### Post by omerp on 2010-08-29
I've got an R705, and I think I've found a solution to the "Brightness is locked after resume" problem. It's a little kludgy, but it works.

I've added a script to /etc/pm/sleep.d directory called "99_dpms_post" (made it executable, since everything else in there is), with the following contents:

```
#!/bin/bash

if [[ ${1} =~ (thaw|resume) ]] ; then

    test -f /usr/share/acpi-support/state-funcs || exit 0

    . /usr/share/acpi-support/power-funcs
    . /usr/share/acpi-support/policy-funcs
    . /etc/default/acpi-support

    /usr/bin/toshset -bl on

    for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"
            chvt 1
            sleep .5
            /usr/sbin/vbetool post
            sleep .5
            chvt 7
            sleep .5
            . /usr/share/acpi-support/screenblank
            sleep .5
            su $user -c "xset dpms force on"
        fi
    done

fi

```Probably a few things in there that are not 100% necessary (for example, I didn't test whether all the "sleep" ones were, but I personally don't care at all about an extra few seconds on resuming... if anyone does, you're welcome to try removing them, I'd be interested to hear if it still works).

UPDATE: Better solution posted below. You should ignore this one; I'm leaving it here for the "historical record", and in case there is anything in it that might prove useful for solving some other problem now or in the future.

---

### Post by JacquiOh on 2010-08-30
The alsa upgrade worked great -- now I can use headphones. That was driving me nuts. 

Omerp --

How do I make that script for the resume bug executable? Or do I just create the file and save it?

---

### Post by omerp on 2010-08-30
JacquiOh: I've found a better, cleaner, and -- most importantly -- more reliable solution to the brightness-control-after-resume problem.

Here it is:

Create the files "tosh-brightness-down" and "tosh-brightness-up" in /etc/acpi/events/ (you can use, e.g., *sudo cp <some-file-already-in-that-folder> tosh-brightness-up* to copy an existing file from /etc/acpi/events/, that way all the permissions and so forth will be as they should be, and then replace the contents of the created files with the contents given below, using *sudo <your favorite editor>*).

*tosh-brightness-down*  :

```
event=hkey VALZ 00000001 00000140
action=/etc/acpi/tosh-brn-down.sh
```*tosh-brightness-up*:

```
event=hkey VALZ 00000001 00000141
action=/etc/acpi/tosh-brn-up.sh
```Then, in a similar fashion, add the following two files to /etc/acpi/ (the parent directory of the one where the previous two files were).

*tosh-brn-down.sh*:

```
#!/bin/sh
test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/key-constants

DeviceConfig

toshset -bl on
```*tosh-brn-up.sh*: (the file is identical to "tosh-brn-down.sh", but I think it's worth having them separate for good order, in case we find out their content should be differentiated somewhere down the line)

```
#!/bin/sh
test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/key-constants

DeviceConfig

toshset -bl on
```Note: This solution assumes you have the  *toshset* package installed on your system (*sudo apt-get install toshset* to install).

Reboot your system for the changes to take effect (or, you can just restart *acpid* and *acpi-support*).

This solution is non-ideal, in the sense that it only fixes **changing brightness via the Fn-keys**, not other ways of changing brightness (e.g., through gnome-power-manager). Ideally, there would be some way to hook onto *any* change in the brightness the system has established, and run *toshset -bl on* immediately (which is essentially what all this does, only just for Fn-key driven brightness events).

If anyone knows of any more general brightness-hook of this sort, please let me know.

---

### Post by fataki on 2010-09-01
The hard drive accelerometer/impact sensor/protection system is not supported by hdapsd.

---

### Post by Local.tosh on 2010-09-01
Low battery runtimes are at least partially related to the fact that the current kernel doesn't seem to support the i3 i5 i7 super low frequency mode (SuperLFM).

Made a thread about it here
[http://ubuntuforums.org/showthread.php?t=1565599](http://ubuntuforums.org/showthread.php?t=1565599)

i might try to upgrade the kernel once i figure how to do that:)

---

### Post by connect404 on 2010-09-02
Cheers for the feedback!

> **samio chang said:**
> Thanks for the post! It has been very useful for some one as new to ubuntu as me :D I am using 10.04 on R700 S1330. Regarding the inbuilt microphone, it works for me! I got the mic sound after switched off the microphone mute.

No probs, glad it helps... must have missed the mute for some reason, inbuilt mic works great now!


> **ouilsen said:**
> Hi all!

What about the built-in UMTS Modem? Is anyone online using Ubuntu and 3G?

Dont quote me, but I did some initial investigations before choosing the non 3g option and it appears the model Toshiba use's is supported in the ubuntu kernel.  Give us an lsusb dump with the module installed and we can investigate it for ya.

Fataki: Anything noticeable in the v1.4 release?  Thanks for the updates.. Ill change my master list

> **JacquiOh said:**
> 
The script for the headphones/mic but I'm a bit worried. Not great with command line yet.

Yeah its less than ideal, and sometimes after resuming from a suspend to ram indicator-sound-service goes nuts and needs a kill -9 to stop it running 100%. Maverick fixes the sound issues.. perhaps wait for the beta and just roll with that.

Oh, just saw you got it going... congrats

Omrep: Thanks for your efforts, trying it now. Brightness is my biggest issue with Ubuntu on this thing

---

### Post by connect404 on 2010-09-02
UPDATE:   V1.5 BIOS released on the 31/08

Cant seem to get bartpe to boot xp on this thing, so looks like I need to get XP setup on a spare drive to get this firmware updated.

---

### Post by Local.tosh on 2010-09-02
> **connect404 said:**
> UPDATE:   V1.5 BIOS released on the 31/08

Cant seem to get bartpe to boot xp on this thing, so looks like I need to get XP setup on a spare drive to get this firmware updated.

You could also burn the Bios to CD (and boot with it in the drive ofc ;)) that should work as well.

---

### Post by Kixtosh on 2010-09-02
Great thread everyone. I'm on my third Portégé: about to install Xubuntu & LXDE on a R205-S209 that's still running WinXP Pro, but the R700/705 will probably be my fourth.

Some of the Fn enabled Hotkey functions have been a troublespot since I first tried Knoppix 3.7 in 2004/5. I'm guessing the dedicated buttons for Toshiba Assist and Toshiba Presentation on the R205 won't work either.

Please carry on!   ):P

---

### Post by connect404 on 2010-09-03
> **fataki said:**
> 
Scenario: Laptop is connected to external display and laptop display is off. External display is disconnected from laptop, but laptop screen doesn't turn on. Need to switch display back to just laptop before disconnecting external display. Pressing display switch-button should help?



\should just need to write a small script that tells gnome to cycle thru the displays and then assign it to a hotkey. Actually, similar to the brightness fix should be possible to do it like that.

Either that or dont have only an external display on.



Oh... first post updated to reflect progress.

---

### Post by omerp on 2010-09-03
Regarding the headphones/mic jacks issue:

For me (on an R705), installing the backports alsa package (depending on which kernel you're running, it could be named *linux-backports-modules-alsa-lucid-generic*, or something similar to that; for me it was *linux-backports-modules-alsa-lucid-generic-tuxonice*, because I'm running a *tuxonice* kernel) fixed it. Needs reboot to take effect.

---

### Post by Local.tosh on 2010-09-04
> **omerp said:**
> Regarding the headphones/mic jacks issue:

For me (on an R705), installing the backports alsa package (depending on which kernel you're running, it could be named *linux-backports-modules-alsa-lucid-generic*, or something similar to that; for me it was *linux-backports-modules-alsa-lucid-generic-tuxonice*, because I'm running a *tuxonice* kernel) fixed it. Needs reboot to take effect.

Yeah as long as you get the alsa-driver-1.0.23 (the latest one) headphones et cetera should work.

You can also run the upgrade script:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

### Post by shiva_SVK on 2010-09-06
> **connect404 said:**
> [SIZE=2][COLOR=DarkOrange]
[/COLOR][/SIZE][SIZE=2][COLOR=DarkOrange]Fingerprint reader[/COLOR][/SIZE]

[LIST]
[*]**Shows up in lspci, but isn't detected by pam_fprint_enroll or fprint_demo.**
[/LIST]
  

Have anybody tried Fingerprint GUI? On VAIO SZ there was the same problem with the above fingerprint reading solutions under Ubuntu, however, Fingerprint GUI was working perfectly.

[http://www.n-view.net/Appliance/fingerprint/](http://www.n-view.net/Appliance/fingerprint/)

---

### Post by talmage on 2010-09-06
> **connect404 said:**
> 
[SIZE=2][COLOR=Green]
[/COLOR][/SIZE][SIZE=2][COLOR=Green]Wifi / Bluetooth[/COLOR][/SIZE][SIZE=2][COLOR=Green]
[/COLOR][/SIZE]
[LIST]
[*]Intel wifi works 100%
[*]Full WEP/WPA/WPA2 support
[*]**Wifi wont turn off/on via keyboard hotkey**
[*]**Wifi status LED will not turn off even with card manually disabled**
[*]Bluetooth works, pairs, transfers files, connects to my bluteooth HID device
[*][B]Even when disabled, bluetooth seems to renable itself sometimes after a reboot or resume from suspend...  still chasing this up. I suspect its still drawing power even when disabled
[/B]
[/LIST]


I'm having trouble with 802.11N on my R705.  Did you do anything special to make that work?  I can't get it to talk to my access point using WPA2-Personal with a pre-shared key.  It acts as if it doesn't even see the access point.  It connects with ease to my 802.11B/G access point.

---

### Post by longreach on 2010-09-21
Hi all,

Great thread. VERY helpful for me.

For the headphones, I had the same problem with my old laptop, so I just got some logitech headphones that had USB converter included. All worked fine. (slack but simple).

I have an issue that I haven't seen on here yet and I am wondering if it is just my laptop...

Sometimes when I leave the laptop in Suspend, when I come back to it (usually about 12 hrs later) the battery is dead as a doornail. It doesn't happen everytime, just when it wants to annoy me.

My first suspicion was the battery, especially because of the dodgy charge/status info in ubuntu, but I read here and found that was normal, I also tested the laptop after the battery was charged and found I got at least 3 hrs use (with no power saving tweaks) so I don't think it's the battery. Anyone else had this problem?

I have tested suspend in Win 7 and had no such problems, but the issue is random enough that it could be by complete chance that it hasn't happened... yet. I don't use Win7 very often so I have to do more testing of the issue.

---

### Post by georgek on 2010-09-24
I'm probably going to get an R700-15R soon (encouraged by the reports here) but I can't find anything useful anywhere about port replicators.

I presume that the usb ones really do need Windows drivers so I can ignore them but does anyone know about the Hi-Speed Port Replicator?  As long as the basics work then it will be good enough for me - I've lived with having to turn off my Thinkpad X41 to (un)dock it ...

---

### Post by hanaflower on 2010-09-29
I just got the r705 and I just installed 10.04 and can not get my wireless working.  Has anyone else had a similar problem or any suggestions to get me up and running?

Thanks

---

### Post by Kixtosh on 2010-09-30
> **hanaflower said:**
> I just got the r705 and I just installed 10.04 and can not get my wireless working.  Has anyone else had a similar problem or any suggestions to get me up and running?

ThanksWelcome to the forum! Is this your first Ubuntu/Linux install? You may need to start a new thread for this, but to get you going, try these troubleshooting suggestions, if you haven't found them already:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by garciagil on 2010-10-04
Hi everyone!
I've successfully installed Ubuntu 10.04.1 on my R700 and everything seems to go fine (excluding the known problems with function keys and other minor issues). However, today I've docked it to its port replicator for the first time and got not signal on neither the auxiliar 19 inches screen nor the laptop screen. Moreover, the fan was working at maximum regime whereas the upper left cornes was getting dangeroulsy hot.
Does anybody know about the nature of the problem and how to solve it?
Thanks in advance.

---

### Post by Kixtosh on 2010-10-04
> **garciagil said:**
> ... However, today I've docked it to its port replicator for the first time and got not signal on neither the auxiliar 19 inches screen nor the laptop screen. Moreover, the fan was working at maximum regime whereas the upper left cornes was getting dangeroulsy hot. ...Hello and welcome to the Ubuntu forums! Which model of port replicator are you using? If it is one of the dynadock models, as far as I know, they are software enabled (they have O.S. specific drivers to install), and therefore unlikely to work with Ubuntu.

[http://us.toshiba.com/computers/accessories/dynadock](http://us.toshiba.com/computers/accessories/dynadock)

If it's a more "traditional" dock, then I'm not sure why it would not work, since I've used these before (albeit rarely, and not with a R700 series Portégé) without any issues.

[http://www.toshibadirect.com/td/b2c/adet.to?poid=472413](http://www.toshibadirect.com/td/b2c/adet.to?poid=472413)

---

### Post by choylee on 2010-10-15
Hello,

I have installed the Ubuntu 10.10 on my toshiba R700 Core i5 
Sometimes , my laptop is freeze with hight CPU (hight fan). 
then I must rebooted (reboot = 10:22)

Any ideas ? 

LOGS : 

lpierre@r700:~$ dmesg | fgrep intel\ ips
[   10.122039] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   10.122065] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   10.183862] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   15.349952] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[   25.327189] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[  155.086569] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[  185.031072] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[  214.975543] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[  219.966342] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded

/var/log/message 
Oct 15 10:11:09 r700 kernel: [   15.363888] EXT4-fs (sda3): re-mounted. Opts: commit=600
Oct 15 10:11:11 r700 kernel: [   17.906394] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 10:11:13 r700 kernel: [   19.626730] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Oct 15 10:11:13 r700 kernel: [   19.629325] EXT4-fs (sda3): re-mounted. Opts: commit=600
Oct 15 10:11:42 r700 kernel: [   48.996001] padlock: VIA PadLock not detected.
Oct 15 10:17:36 r700 kernel: [  402.326815] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 10:17:41 r700 kernel: [  407.319251] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 10:17:51 r700 kernel: [  417.304198] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 10:24:18 r700 kernel: imklog 4.2.0, log source = /proc/kmsg started.


syslog
ct 15 10:12:47 r700 NetworkManager[1103]: <warn> Activation (eth1) failed.
Oct 15 10:12:47 r700 NetworkManager[1103]: <info> (eth1): device state change: 9 -> 3 (reason 0)
Oct 15 10:12:47 r700 NetworkManager[1103]: <info> (eth1): deactivating device (reason: 0).
Oct 15 10:12:47 r700 wpa_supplicant[1200]: Authentication with 00:00:00:00:00:00 timed out.
Oct 15 10:17:02 r700 CRON[1996]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 15 10:17:36 r700 kernel: [  402.326815] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 10:17:41 r700 kernel: [  407.319251] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 10:17:51 r700 kernel: [  417.304198] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 10:24:18 r700 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct 15 10:24:18 r700 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1043" x-info="http://www.rsyslog.com"] (re)start
Oct 15 10:24:18 r700 rsyslogd: rsyslogd's groupid changed to 103
Oct 15 10:24:18 r700 rsyslogd: rsyslogd's userid changed to 101

---------------------------------------
deamon.log
Oct 15 10:12:32 r700 NetworkManager[1103]: <info> (eth1): supplicant connection state:  scanning -> associating
Oct 15 10:12:32 r700 wpa_supplicant[1200]: Association request to the driver failed
Oct 15 10:12:37 r700 wpa_supplicant[1200]: Authentication with 00:0f:b5:36:0b:86 timed out.
Oct 15 10:12:37 r700 NetworkManager[1103]: <info> (eth1): supplicant connection state:  associating -> disconnected
Oct 15 10:12:37 r700 NetworkManager[1103]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Oct 15 10:12:42 r700 wpa_supplicant[1200]: Trying to associate with 00:0f:b5:36:0b:86 (SSID='viatelecom' freq=2462 MHz)
Oct 15 10:12:42 r700 NetworkManager[1103]: <info> (eth1): supplicant connection state:  scanning -> associating
Oct 15 10:12:42 r700 wpa_supplicant[1200]: Association request to the driver failed
Oct 15 10:12:47 r700 NetworkManager[1103]: <warn> Activation (eth1/wireless): association took too long, failing activation.
Oct 15 10:12:47 r700 NetworkManager[1103]: <info> (eth1): device state change: 5 -> 9 (reason 11)
Oct 15 10:12:47 r700 NetworkManager[1103]: <warn> Activation (eth1) failed for access point (viatelecom)
Oct 15 10:12:47 r700 NetworkManager[1103]: <info> Marking connection 'Auto viatelecom' invalid.
Oct 15 10:12:47 r700 NetworkManager[1103]: <warn> Activation (eth1) failed.
Oct 15 10:12:47 r700 NetworkManager[1103]: <info> (eth1): device state change: 9 -> 3 (reason 0)
Oct 15 10:12:47 r700 NetworkManager[1103]: <info> (eth1): deactivating device (reason: 0).
Oct 15 10:12:47 r700 wpa_supplicant[1200]: Authentication with 00:00:00:00:00:00 timed out.
Oct 15 10:24:18 r700 NetworkManager[1107]: <info> NetworkManager (version 0.8.1) is starting...
Oct 15 10:24:18 r700 NetworkManager[1107]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Oct 15 10:24:18 r700 avahi-daemon[1113]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Oct 15 10:24:18 r700 avahi-daemon[1113]: Successfully dropped root privileges.



Many thanks

---

### Post by connect404 on 2010-10-15
No ideas, but I can confirm the same behavior. I initially did an upgrade from 10.04 to 10.10 and my R700 would randomly hard crash, and the CPU fan would start to spin very very fast (faster than at full load). I wiped it, did a clean install and I still am having the same issue, though no where near as frequent. Logs don't show much.

The brightness fix details above does not work anymore. toshset is not working in Maverick...

```

connect404@pez:~$ sudo toshset 
required kernel toshiba support not enabled.

```On the bright side the headphone issue is resolved and my laptop can now suspend with an SD card installed.

> **choylee said:**
> Hello,

I have installed the Ubuntu 10.10 on my toshiba R700 Core i5 
Sometimes , my laptop is freeze with hight CPU (hight fan). 
then I must rebooted (reboot = 10:22)

Any ideas ? 


---

### Post by connect404 on 2010-10-15
Just checked and a new firmware for the R700 is out:

**Version 1.60 - 2010-09-28**
[LIST]
[*]Changed the Thermal Control Parameter(s).
[/LIST]
Looks suspiciously related.... too bad toshiba doesnt give any useful info for these updates. I will try it out on Monday and report back.


> **choylee said:**
>  intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   10.122065] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   10.183862] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   15.349952] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[   25.327189] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[  155.086569] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[  185.031072] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[  214.975543] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[  219.966342] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded


---

### Post by choylee on 2010-10-15
I have a 1.5 Bios version .

Do you advice me to update in 1.6 ? 

Many Thanks.

---

### Post by connect404 on 2010-10-15
Dont know the answer, going to do an update now. Mine just crashed again with the same apci errors:

These are some new errors when bringing the laptop up:
```
Oct 15 12:52:18 pez kernel: [    2.212797] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 15 12:52:18 pez kernel: [    2.213805] ACPI Error (psargs-0359): [GTF0] Namespace lookup failure, AE_NOT_FOUND
Oct 15 12:52:18 pez kernel: [    2.213811] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT0.PRT0._SDD] (Node ffff8800709427e0), AE_NOT_FOUND
Oct 15 12:52:18 pez kernel: [    2.213937] ACPI Error (psargs-0359): [GTF0] Namespace lookup failure, AE_NOT_FOUND
Oct 15 12:52:18 pez kernel: [    2.213942] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT0.PRT0._GTF] (Node ffff880070942800), AE_NOT_FOUND
Oct 15 12:52:18 pez kernel: [    2.214488] ata1.00: ATA-8: Hitachi HTS725032A9A360, PC3OC71E, max UDMA/133
Oct 15 12:52:18 pez kernel: [    2.214510] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Oct 15 12:52:18 pez kernel: [    2.215704] ACPI Error (psargs-0359): [GTF0] Namespace lookup failure, AE_NOT_FOUND
Oct 15 12:52:18 pez kernel: [    2.215709] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT0.PRT0._SDD] (Node ffff8800709427e0), AE_NOT_FOUND
Oct 15 12:52:18 pez kernel: [    2.215809] ACPI Error (psargs-0359): [GTF0] Namespace lookup failure, AE_NOT_FOUND
Oct 15 12:52:18 pez kernel: [    2.215829] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT0.PRT0._GTF] (Node ffff880070942800), AE_NOT_FOUND

```

and when its just idling var/log/messages is filling up with this:

```
Oct 15 13:03:04 pez kernel: [  975.880540] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:03:09 pez kernel: [  980.875789] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:04:54 pez kernel: [ 1085.776650] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:07:29 pez kernel: [ 1240.645532] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:07:59 pez kernel: [ 1270.632053] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:08:29 pez kernel: [ 1300.618543] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:08:54 pez kernel: [ 1325.607321] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:10:24 pez kernel: [ 1415.568035] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:10:59 pez kernel: [ 1450.552562] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:11:29 pez kernel: [ 1480.538681] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:11:49 pez kernel: [ 1500.528504] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:12:24 pez kernel: [ 1535.513560] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:12:59 pez kernel: [ 1570.496939] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Oct 15 13:13:39 pez kernel: [ 1610.478892] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded

```


> **choylee said:**
> I have a 1.5 Bios version .

Do you advice me to update in 1.6 ? 

Many Thanks.

---

### Post by connect404 on 2010-10-15
Bios update complete, errors still spamming in the logs. Havent seen a crash .... yet

---

### Post by choylee on 2010-10-15
I going to see the BIOS parameters in order to disable something 


LOGS
9.634420] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[    9.634447] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    9.682117] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   14.856928] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[   24.835781] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[   84.709055] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[  119.628788] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
...etc..........;
[13646.387447] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[1266874884.011836] intel ips 0000:00:1f.6: restoring config space at offset 0xf (was 0x300, writing 0x30a)
[1266874884.011854] intel ips 0000:00:1f.6: restoring config space at offset 0x4 (was 0x4, writing 0xd4724004)
[1266874884.011862] intel ips 0000:00:1f.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[   10.713992] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[   60.630078] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[  220.361372] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded

---

### Post by omerp on 2010-10-15
I can confirm that kernel 2.6.35 (the one distributed under Maverick) breaks toshset. Turns out a bug has already been submitted about this;

[https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/644898](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/644898)

For now I know of no workaround except downgrading to a 2.6.32 kernel. Not much of a solution.

---

### Post by fataki on 2010-10-16
Also experiencing the freeze with high cpu/fan usage, but not often.

Can't install the 1.60 Bios update, toshiba service center (and the .zip file I downloaded from the site) claim it is not suitable for my device (R700-11P).

---

### Post by TNT1 on 2010-10-16
Dunno if this is the right place to ask, but how do I install Toshiba Utils on a Portege m400? I'm told if I install this, the hardware buttons will work.

---

### Post by longreach on 2010-10-17
> **TNT1 said:**
> Dunno if this is the right place to ask, but how do I install Toshiba Utils on a Portege m400? I'm told if I install this, the hardware buttons will work.

Well, it's a thread on the R700, so not really the right place no :-P

You may find something useful here:
[http://linuxappfinder.com/package/toshutils](http://linuxappfinder.com/package/toshutils)

I have never used these but I might give them a go myself.

---

### Post by longreach on 2010-10-17
.... ok I tried the toshutils but does not appear to work on the R700, the website mentions it probably won't for the newer models coz of BIOS stuff. (I know, I'm very technical with my descriptions)

---

### Post by omerp on 2010-10-17
> **longreach said:**
> .... ok I tried the toshutils but does not appear to work on the R700, the website mentions it probably won't for the newer models coz of BIOS stuff. (I know, I'm very technical with my descriptions)
Yes, to the best of my understanding, toshutils was designed to work with the old power-management interface, APM -- whereas toshset can talk to the newer interface, ACPI.

---

### Post by grantingram on 2010-10-17
Ladies/Gents,

Thanks for all the hints and tips on this thread.  

I've recently got an R700 15W from work and installed Ubuntu 10.04 on it.  

The headphone jack initially didn't work but I followed the suggestion of omerp and installed *linux-backports-modules-alsa-lucid-generic* and after a reboot I a wired up for sound!  So thanks very much.  

I have a Toshiba Hi Speed Port Replicator in the office.  [Looks just like this: [http://www.toshibadirect.com/td/b2c/adet.to?poid=472413]](http://www.toshibadirect.com/td/b2c/adet.to?poid=472413])  It works just fine for me.

I also have the display at maximum brightness problem when you come back from a suspend but haven't yet tried the suggestions.  

Overall it seems like a pretty slick machine....

EDIT: It appears that the backports-modules and the docking station don't go very well together.  With the backports installed the machine quite often fails to start or if it does putting it in a docking station causes a complete lock-up with no mouse movement.  So you might have to pick one or the other.

---

### Post by choylee on 2010-10-21
> **connect404 said:**
> Bios update complete, errors still spamming in the logs. Havent seen a crash .... yet

I have updated to BIOS 1.16. 
I have the same errors in /var/log/message 
intel ips 0000:00:1f.6: MCP power or thermal limit exceeded

But I have not seen a crash (cpu/fan hight speed )   :P


Do you know if this CPU temperature is too hight ? :confused:
r700-131:/var/log$ **sensors**
acpitz-virtual-0
Adapter: Virtual device
temp1:       +56.0°C  (crit = +107.0°C)

 Thanks

---

### Post by fataki on 2010-10-22
Battery life and its estimation seem better with 10.10 Maverick. Still having the crashes though, twice in 15 min. this morning, but not after that.

---

### Post by jmtd on 2010-10-25
> **omerp said:**
> JacquiOh: I've found a better, cleaner, and -- most importantly -- more reliable solution to the brightness-control-after-resume problem.

Does this really work?

I normally use Debian.  "toshset" on Debian would not work without a specially patched toshiba_acpi driver.  I ported the patch in the /usr/share/doc/toshset directory to 2.6.35 and rebuilt it.  However, having done that, running "toshset -bl on" post reboot didn't cure the problem (but it did vary the backlight brightness fractionally).

I assumed that Ubuntu must have this stuff compiled into their toshiba_acpi driver by default and perhaps some other magic.  So, I installed 10.10, but I have the exact same findings there.

Who has got this to work?

---

### Post by omerp on 2010-10-26
> **jmtd said:**
> Does this really work?

I normally use Debian.  "toshset" on Debian would not work without a specially patched toshiba_acpi driver.  I ported the patch in the /usr/share/doc/toshset directory to 2.6.35 and rebuilt it.  However, having done that, running "toshset -bl on" post reboot didn't cure the problem (but it did vary the backlight brightness fractionally).

I assumed that Ubuntu must have this stuff compiled into their toshiba_acpi driver by default and perhaps some other magic.  So, I installed 10.10, but I have the exact same findings there.

Who has got this to work?

The "fix" using toshset amounts to calling 'toshset -bl on' after every time you alter brightness (i.e., right after the brightness function-keys are pressed). For reasons that are not 100% clear to me, this makes the hardware actually reflect the change that was issued.

Now, as far as kernel versions are concerned: everything I said here pertains to 2.6.32; as other posts in this thread mention, this does not work on 2.6.35 (the version that Ubuntu 10.10/Maverick shipped with), and judging from the bug-report on launchpad (see previous post), it's not a matter of toshiba_acpi not being compiled into the kernel, but rather something more subtle...

---

### Post by crompie on 2010-10-28
> **jmtd said:**
> Does this really work?

I normally use Debian.  "toshset" on Debian would not work without a specially patched toshiba_acpi driver.  I ported the patch in the /usr/share/doc/toshset directory to 2.6.35 and rebuilt it.  However, having done that, running "toshset -bl on" post reboot didn't cure the problem (but it did vary the backlight brightness fractionally).

I assumed that Ubuntu must have this stuff compiled into their toshiba_acpi driver by default and perhaps some other magic.  So, I installed 10.10, but I have the exact same findings there.

Who has got this to work?

Sorry if this post is slightly off-topic, but the post by jmtd (above) is very interesting, since it seems you got toshset to work. Can you please go into a little more detail on exactly how you did this, i.e. "I ported the patch in the /usr/share/doc/toshset directory to 2.6.35 and rebuilt it". Kindly elaborate? Where did you find the patch?

I am running Ubuntu 10.10 with kernel 2.6.35-22-generic, on a Toshiba Portege R600. I need toshset in order to enable the on-board 3g Mobile Broadband modem, but running toshset gives "required kernel toshiba support not eanbled". The module toshiba_acpi is successfully loaded on my system, but toshset still does not run.

If you got it to work with kernel 2.6.35 I'm very interested to know how. Thanks.

---

### Post by solnyshok on 2010-10-28
hi,can somebody help me to run synaptics 2 finger scroll script on resume? simply adding it to startup apps results in loosing this ability after resume

btw, brightness fix also fails after resume

headphone jack works out-of-the-box and sleep works with sd card in the reader too.

---

### Post by solnyshok on 2010-10-28
hi, please help me to fix hibernation issue. this my syslog during hibernation attempt

I think there are at least 2 problems in this log
1- bluetooth failed to hibernate
2- why is it spending 100seconds to preallocate space on my ssd with average speed of 25MB/s. I have intel ssd x25-m, sequential write speed around 100MB/s. Why even pre-allocate anything? Can it be because my swap isn't on the swap partition but a swap file in the /mnt?

EDIT: ok I fixed hibernation by going from swap file to swap partition, editing uswsusp.conf for new swap device and reconfiguring uswsusp. A bonus is that after hibernation - brightness regulation keeps working.

---

### Post by solnyshok on 2010-10-29
Hello, people, is bluetooth working for you on 10.10? I cannot activate bluetooth in Ubuntu, however, in W7 everything works.

---

### Post by solnyshok on 2010-11-01
ok, found easy fix to 2 finger scroll issue
desktop->gnome->peripherals->touchpad->scroll_method =2 in gconf-editor
while there, you can also enable horizontal scroll. it survives hibernate cycle this way

---

### Post by stevekerrison on 2010-11-02
This problem also exists on the Satellite R630 (Portege R700 sans some of the business features). My R630-13F freezes up shortly after boot, but usually once it's "warm" (one or two boots) it's OK.

There's also an apparent (but not completely confirmed, to my mind) correlation between running on battery and/or using the wifi instead of wired ethernet, and the lockups.

Safe to say it's something ACPI related, however.

There's a bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/667405](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/667405) is there a similar report for the R700?

---

### Post by longreach on 2010-11-02
> **solnyshok said:**
> 

headphone jack works out-of-the-box and sleep works with sd card in the reader too.

I have also got the headphone & mic jack working out of the box (since upgrading) might be worth editing first post to say it is in 10.10.

---

### Post by crompie on 2010-11-02
Many of the hardware issues discussed here (and others) can be resolved  using the "toshset" command. This allows you to control a host of functions such as screen brightness, the fan, Fn keys, bluetooth, the on-board 3g modem, etc.

For example, the 3g mobile broadband modem in Toshiba laptops does not work out the box in Ubuntu. In order to enable it, you have to issue the command "sudo toshset -3g on" in a Terminal. Then you can use Network Manager to set up your mobile broadband connection (assuming toshset works!)

Problem is, toshset does not work with the latest kernel version 2.6.35 used in Ubuntu 10.10. Using the command shown above gives the error "required toshiba kernel support not enabled". However, it DOES work with previous releases of Ubuntu, which used older kernel versions. 

Apparently the problem is with the driver module tochiba_acpi. In order for toshset to run, it requires a modified version of toshiba_acpi. It seems that the modified driver is included with the older kernel 2.6.32 (compiled for Ubuntu), but for some reason it has been left out of the latest kernel.

Note that the module toshiba_acpi IS present in Ubuntu 10.10, but it is not the modified version that is required for toshset.

The modified module toshiba_acpi is available as a patch here:
[http://memebeam.org/free-software/toshiba_acpi/](http://memebeam.org/free-software/toshiba_acpi/)
Note that this site says that the driver is already included in "modern" kernals (2.4 and 2.6). However, it appears that what is included in these kernels is the old, unmodified driver. So you DO need to patch the driver. 

EDIT:
For instructions on applying the patch, see post #13 on the following page:
[https://bugs.launchpad.net/bugs/644898](https://bugs.launchpad.net/bugs/644898)

Alternatively:
Another solution is a work-around. All you need to do is use an older kernel. The kernel used by the previous version of Ubuntu (10.04 - Lucid Lynx) is kernel 2.6.32-25-generic and this kernel includes the modified driver, which allows toshset to run.

The easiest way to install the 2.6.32 kernel is via the Synaptic package manager. If you have multiple operating systems installed, when you reboot Grub will give you the option of starting Ubuntu 10.10 with kernel 2.6.32. Even though you are using an older kernel, everything still works as normal - including toshset.

Once you have the 2.6.32 kernel, type "toshset" in a Terminal, and you will see all the hardware functions it can do.

Hopefully at some stage the modified driver will be built into the latest kernel.

---

### Post by choylee on 2010-11-03
Hello,

I don't find the Ubuntu (10.01)  but so : 

Ubuntu 9.04 (Jaunty Jackalope)
Ubuntu 9.10 (Karmic Koala)
Ubuntu 10.04.1 LTS (Lucid Lynx)
Ubuntu 10.10 (Maverick Meerkat)

Do you mean *[I]10.04.1 *[/I] ?

Thanks you

---

### Post by crompie on 2010-11-03
Choylee,

You are quite correct - the previous version of Ubuntu was 10.04 (Lucid Lynx) with kernel 2.6.32-25-generic.

My apologies for the error.

---

### Post by solnyshok on 2010-11-06
what I found from information on new Linux kernel (2.6.36) it is going to be first kernel that has support for Core i3/i5 turbo mode for graphics. Also, current kernel does not see that our CPUs can work at 25% of nominal frequency, so in windows, my 2.4GHz cpu idles at 665MHz, in Ubuntu at 1.2GHz. And lack of bluetooth, lack of brightness regulation after sleep, periodical freezes while running on battery. Lots of small niggles that I strongly dislike. But loading speed is amazing. It now boots in around 5 seconds from SSD.

I am writing this on 2.36 Kernel. It seems faster. All problems with Toshset still present though. No Bluetooth, no brightness regulation after sleep. No reduced MHz.

---

### Post by choylee on 2010-11-07
> **crompie said:**
> Choylee,
You are quite correct - the previous version of Ubuntu was 10.04 (Lucid Lynx) with kernel 2.6.32-25-generic.
My apologies for the error.

I have installed the 10.04 in order to downgrad to a 2.6.32 kernel
And now It works.

I didn't have this errors in /var/log/message and I haven't got the freeze with high cpu/fan usage :)
[  119.628788] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded

root@r700:/# aptitude show toshset
Package: toshset
State: installed
Automatically installed: no
Version: 1.75-2
Priority: optionnel
Section: utils
Maintainer: Ubuntu Developers <[EMAIL="ubuntu-devel-discuss@lists.ubuntu.com"]ubuntu-devel-discuss@lists.ubuntu.com[/EMAIL]>
Uncompressed Size: 250k
Depends: libc6 (>= 2.7), libgcc1 (>= 1:4.1.1), libpci3, libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4)
Description: Access much of the Toshiba laptop hardware interface Toshset is a command-line tool to allow access to much of the Toshiba laptop hardware interface developed by Jonathan Buzzard. It can do things like set the hard drive spin-down time, turn off the display and set the fan speed without the help of the kernel. Toshset requires an experimental version of the toshiba_acpi kernel module with an ACPI-enabled kernel. Otherwise it works only if the laptop supports the old APM BIOS. (The last of these was produced something like 5 years ago) 
Please read README.Debian how to install the experimental version of the toshiba_acpi kernel module. (Ubuntu users don't need it)

---

### Post by ksanger on 2010-11-07
I've read the thread, what do you guys recommend?  

I've just purchased a Toshiba Portege R705 and am interested in dual booting to linux.  Should I even attempt it?  And if so do I go back to a previous version 10.04.1 so that the toshset still works?

Lastly is it really safe?  If the OS controls the cooling then how do I know that the fan will keep the i3 processor cool?  I would have thought that the bios controlled the fan not the OS.

---

### Post by omerp on 2010-11-07
ksanger,

I have an R705 as well, and so long as you install 10.04.1 (or alternatively, install 10.10 and downgrade to the 2.6.32 kernel), the OS works *great* on this machine. As far as the heat/fan-related comments on this thread, I suspect that they pertain to the R700, not to the R705 -- as I have never encountered them on my R705.

---

### Post by crompie on 2010-11-08
For those wishing to use toshset with kernel 2.6.35 in Ubuntu 10.10, see post #13 on the following page:

[https://bugs.launchpad.net/bugs/644898](https://bugs.launchpad.net/bugs/644898)

There are instructions there to patch the kernel, enabling toshset to run. 

:P

---

### Post by solnyshok on 2010-11-08
> **omerp said:**
>  ...as far as the heat/fan-related comments on this thread, I suspect that they pertain to the R700, not to the R705 -- as I have never encountered them on my R705.
actually, I think it is a matter of toshiba-acpi functionality. Happens regularly on my r630 with kernel 2.6.35 on Ubuntu 10.10 and yesterday happened on Fedora 14 (also 2.6.35-something kernel)

---

### Post by omerp on 2010-11-08
> **solnyshok said:**
> actually, I think it is a matter of toshiba-acpi functionality. Happens regularly on my r630 with kernel 2.6.35 on Ubuntu 10.10 and yesterday happened on Fedora 14 (also 2.6.35-something kernel)

That's my point, though -- I was running Ubuntu 10.10 with 2.6.35 on my R705 for quite a while and never encountered this particular issue. Perhaps, then, I should have written "I suspect they pertain to models other than the R705"...

---

### Post by solnyshok on 2010-11-08
> **omerp said:**
> That's my point, though -- I was running Ubuntu 10.10 with 2.6.35 on my R705 for quite a while and never encountered this particular issue. Perhaps, then, I should have written "I suspect they pertain to models other than the R705"...

it occurs only on cold start WITHOUT AC, i/e cold start on battery. So, if you use it mostly connected to AC, you could have missed it. Anyway, now compiling updated tacpi, hopefully will forget about this bug forever. //EDIT: Happened again this morning on resume from cold, 2.6.35 with patched ACPI

---

### Post by ksanger on 2010-11-09
I'm running a Toshiba Portege R705-P35 with ubuntu kernel 2.6.32-25.  The wireless port will not enable.

Based on these recommendations I tried installing Ubuntu 10.04 LTS through WUBI.  It installs.  But my wireless port is disabled.  It sees the wireless device as an Intel WiMAX/WFi Link 6050 Series.  There is a bug report [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451) #39 stating that the driver for this hardware did not work. 

The fix appears to be installing the driver and sys file from Windows using ndiswrapper.  Also the last post suggests that the new driver does exist.  However I can't find instructions on how to use either method.  Can someone please post what they have done to enable the wireless Ethernet connection?

---

### Post by ksanger on 2010-11-10
Hello again.  Still have no idea how to enable the wireless on this toshiba r705 laptop with ubuntu 10.04 LTS.  However there is a difference between Win 7 which lists the wireless as 6250 and ubuntu which calls is 6050.  Is this part of my problem?  Please help.

---

### Post by solnyshok on 2010-11-11
Hi,I want to share another solution to brightness regulation after suspend. I went into "keyboard shortcuts" and added new ones for 
Fn+F6 = sudo toshset -bl on
Fn+F7 = sudo toshest -bl on
it works for me, maybe because I am in sudoers file. 

What is interesting in this approach, is that now brightness is being regulated in smaller steps. Previously, you could regulate it in steps of 2 from 0 to 8. now it is in steps of 1. OSD do not show up anymore. I like this better than previous situation though.

=====================================

also, bluetooth is sometimes off on startup, and always off after suspend. in order to re-activate it, I use following commands
sudo toshset -bluetooth off
sudo toshset -bluetooth on
sudo bluetoothd
I also installed blueman-applet cause it is more functional than the default one.

---

### Post by solnyshok on 2010-11-12
re: cold freezes.
Today, I had more time to study this issue. It happens only in Linux, Windows is ok. This morning I used laptop outside, it is quite cold there, so machine was getting colder instead of warmer and it kept crashing. Seems that there is a problem, that if processor is not hot enough (or thermal sensors are not warm enough) it would lockup. And, as this doesn't affect Windows, I think it is a bug in Toshiba ACPI that we use.

---

### Post by ksanger on 2010-11-13
Well I take this back.  Wireless on the Toshiba R705 with Ubuntu 10.04.01 LTS finally works.  The last thing I did was delete the connections I made by hand.  Then tried to connect again.  So in short, download the latest driver (6050 driver from [http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads)), untar it (tar xvf iwlwifi-6050-ucode-9.201.4.1.tgz), then copy it into /lib/firmware (cp iwlwifi-6050-ucode-9.201.4.1 /lib/firmware/) .  Then delete any wireless connection you tried to edit by hand.  Then reboot.  Your connections should show up, enter your security information.  And you'll be where I am :)  



_Ignore my rant below..._
[I]Wireless for 10.04.01 LTS does not work.  Installed latest driver /lib/firmware/iwlwifi-6050-4.ucode.  Now I can see my home network, but it won't connect.

10.04.01 LTS is not compatible with wireless networks at least out of the box.  Either everyone is online using the wired link or their doing something else.  If I ever get this working I'll post back, but I'm about to GIVE UP.  A laptop, especially a light weight laptop, requires a wireless connection.  Period.  Software that doesn't provide that as a minimum isn't compatible.  Sorry ubuntu it was a good try.[/I]

---

### Post by connect404 on 2010-11-13
> **ksanger said:**
> 10.04.01 LTS is not compatible with wireless networks at least out of the box.  Either everyone is online using the wired link or their doing something else.

No issues for wifi on 10.04 at all for me on a standard R700. I dont seem to get wifi-N performance, but its not a real biggie.

a 'sudo lspci -v' shows the following for wifi:

```
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 36
	Memory at 94500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

```

---

### Post by omerp on 2010-11-13
> **ksanger said:**
> Either everyone is online using the wired link or their doing something else.

I think I saw in one of your previous posts, ksanger, that you're on an R705-P35, right? I'm on an R705-P25 (i.e., an older model), which uses an Intel 6200, which I guess is better supported :-/

I'm really sorry you've had this bad luck -- I guess Toshiba rolled out a model with newer wifi hardware, but unfortunately the support is not there yet from Ubuntu (?)

---

### Post by connect404 on 2010-11-13
> **omerp said:**
> I think I saw in one of your previous posts, ksanger, that you're on an R705-P35, right? 

Oh, missed that... what wifi card do you have installed ksanger? run lspci and post back the results.

---

### Post by ksanger on 2010-11-13
> **connect404 said:**
> Oh, missed that... what wifi card do you have installed ksanger? run lspci and post back the results.

toshiba r705-p35 with ubuntu 10.04.01 LTS shows the wireless network controller 02:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 5f).  Note Win 7 shows it as an Intel WiMAX/Wifi 6250.

Here is lspci output so you may see the rest of the hardware on the p35 version.

$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LC Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
02:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 5f)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by GediminasB on 2010-11-22
Have anyone found a workaround for "cold start" bug? This is the only thing which delays me of switching from Windows to Ubuntu. ;)

---

### Post by garciagil on 2010-11-25
> **solnyshok said:**
> Hello, people, is bluetooth working for you on 10.10? I cannot activate bluetooth in Ubuntu, however, in W7 everything works.

Install Blueman ;)

---

### Post by solnyshok on 2010-11-26
as much as I love ubuntu, I went away to Win7 until this cold start bug is sorted out. I cannot afford to loose my work everytime I wakeup my laptop without AC.

---

### Post by JacquiOh on 2010-11-26
Huh. I think this is what is going wrong with my R700. While the upgrade to 10.10 fixed a ton of stuff: headphones/video playback/audio playback/brightness, it has seriously killed my ability to work on the laptop without it plugged in. It just randomly stops working and then, within seconds, the fan goes haywire. First time it happened (I'm usually plugged in) I didn't know a colleague had unplugged me. Took me a while to discover the connection. 

Is that what's happening with all of yours?

---

### Post by GediminasB on 2010-11-27
> **JacquiOh said:**
> Huh. I think this is what is going wrong with my R700. While the upgrade to 10.10 fixed a ton of stuff: headphones/video playback/audio playback/brightness, it has seriously killed my ability to work on the laptop without it plugged in. It just randomly stops working and then, within seconds, the fan goes haywire. First time it happened (I'm usually plugged in) I didn't know a colleague had unplugged me. Took me a while to discover the connection. 

Is that what's happening with all of yours?

Yes, it is what's happening with my laptop. I assume it is somehow connected with WiFi, because it don't happen if I'm offline or on eth.

---

### Post by JacquiOh on 2010-11-27
Can't say with mine. I'm never offline or eth, really.

But for me, it's only when the power is unplugged. Once I'm plugged in, it's all good.

---

### Post by GediminasB on 2010-11-27
> **JacquiOh said:**
> Can't say with mine. I'm never offline or eth, really.

But for me, it's only when the power is unplugged. Once I'm plugged in, it's all good.

Yes, it doesn't happen when the power is plugged in. From my experience it is Unplugged + WiFi

---

### Post by NFec on 2010-11-27
Hi,

Toshiba released on the 25th of November a new version of the BIOS for the Portege R700/705 and Satellite R630:
B1.70-WIN-EC1.40

Does anyone has any experience with the update? Is it improving the Linux support?

---

### Post by GediminasB on 2010-11-28
> **NFec said:**
> Hi,

Toshiba released on the 25th of November a new version of the BIOS for the Portege R700/705 and Satellite R630:
B1.70-WIN-EC1.40

Does anyone has any experience with the update? Is it improving the Linux support?

It didn't affected "cold start" bug

---

### Post by daviemoston on 2010-11-29
it looks like the freezing problem doesn't just affect ubuntu.
see here [http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=56073&tstart=0](http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=56073&tstart=0)
and [http://forum.notebookreview.com/toshiba/512036-portege-r700-freezing-full-speed-fan-no-keyboard-4.html](http://forum.notebookreview.com/toshiba/512036-portege-r700-freezing-full-speed-fan-no-keyboard-4.html)
for details of people with the same problem on windows.
The suspicion on windows seems to be the fingerprint reader
On windows people are recomending either taking an updated driver ([http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/download.jsp?ct=DL&soid=2823594&ref=EV](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/download.jsp?ct=DL&soid=2823594&ref=EV)) or disabling the power management on the device
Go into Device Manager
Expand the Biometric section and select the Fingerprint Device.
Right click the Fingerprint Device and click "Properties"
Go into the Power Management Tab
Untick "Allow this computer to turn of the device to save power"

---

### Post by Jorge Alban on 2010-11-30
Thanks for all the info in this thread, I found it incredibly useful, so here is my feedback and R705 success story. Hope I can help and inspire someone as you people did with me:

Got a R705 for my web-centric 15-year old daughter. For 890$, during a weekend sale, I snapped an R705-01R01C with bluetooth and Expresscard Slot (no longer listed at toshibadirect.com). Came with version 1.6 Bios. Windows C:/ shrinking worked great using the factory restore partition inside the HDD. Just hold the CERO button and press the laptop POWER button to activate it. A feature in the Toshiba Recovery Wizard lets one shrink MSWindows to 60GB without conflicting with supposedly "immovable" system files (as did any other geeky method I tried).

Gparted in Ubuntu 10.04.1 LTS Live-CD let me turn that new empty disk space into an extenden partition, and inside it three small logical partitions: 30GB for ROOT, 360GB for HOME and 4 GB for SWAP (important for suspend-to-ram). During installation one must be careful to manually assign the mount points for the above-mentioned partitions and format them as EXT3. Also remember to assign the larger NTFS partition to WINDOWS.

After Ubuntu Lucid installation and more than 200 MB of updates through ethernet, the wireless was already functional and toshset already installed. Only THREE tweaks required were:

1) The simplified "brightness control after suspend to RAM" fix proposed by OMERP in post No. 10 of this thread. NEWBIE NOTES: For the copy command (cp) to work I first had to change directory (cd) to /etc/acpi/events/ in the Terminal. To copy a line of code into the terminal just highlight it on the webpage, click back in the terminal and press both mouse buttons simultaneously (or middle mouse button). 

I then opened the "Keyboard Shorcuts" tool and added new keyboards shortcuts to get eight steps of brightness, as suggested by SOLNYSHOK in post No. 66. No fix was required for Bluetooth as it works well, stays off after return from suspension and can easily be activated/deactivated with the menu under the bluetooth icon. 

2) In Synaptic Package Manager I looked for and installed "linux-backports-modules-alsa-lucid-generic" and both the headphones/mic jack got working.

My only remaining issue is getting just  over 3 hours of fast-and-furious wifi browsing with webcam on (bluetooth OFF, brightness three notches UP, BIOS settings dont make a difference), while MSWindows users claim about 4.5 hours. Since the original poster reported about one hour of battery left when the Gnome Power Manager claimed 5 minutes, I tested changing threshold values in gnome-power-manager:

Open a terminal and type "sudo gconf-editor" In the window that opens I selected APPS, then GNOME-POWER-MANAGER, then THRESHOLDS. I tried different TIME values, but finally settled for TIME-LOW: 50, TIME-CRITICAL: 40, and TIME-ACTION: 30. The idea is to let the battery deplete itself almost fully, so as not to develop "memory" issues and shorten battery capacity, but not to deplete it to the point where the system cant go into hibernation (default values were 1200, 300 and 120). 

And thats it ! Love the fact that the touchpad automatically disables itself when the keyboard is being used. Mute, Brightness, Volume, Suspend to RAM hardware buttons all work they way they are supposed to. Unless you are a 3D cutting-edge gamer, you cant go wrong with this little-laptop-that-could: As light and thin as a netbook (so much better built), yet as powerful and comfortable keyboard-and-screen-wise as a full sized laptop.

---

### Post by rinseaid on 2010-12-07
For anyone having issues connecting to 802.11n networks:

[http://ubuntuforums.org/showthread.php?t=1592846](http://ubuntuforums.org/showthread.php?t=1592846)

This solution fixed the problem for me.

---

### Post by njreid on 2010-12-09
> **NFec said:**
> Hi,

Toshiba released on the 25th of November a new version of the BIOS for the Portege R700/705 and Satellite R630:
B1.70-WIN-EC1.40

Does anyone has any experience with the update? Is it improving the Linux support?

No - I've upgraded the BIOS and it doesn't seem to prevent 10.10 64bit stock kernel from freezing for me. Nor does the latest 2.6.37rc2 kernel .deb seem to help either. The power management really does seem pretty broken with these machines on Linux - I really don't like having to rely on Windows 7.

---

### Post by stevekerrison on 2010-12-11
I'm running kernel 2.6.32-25-generic in 10.10 and have no freezes.

I guess we need a developer to take ownership of this issue and find out what changed between that and more recent kernels to make the freeze happen.

I suspect it's not that simple though - there may be a chunk of ACPI that wasn't supported on this laptop in 2.6.32 that was enabled in .35, and somewhere therein lies the problem.

But that's just conjecture...

---

### Post by moimael on 2010-12-12
Hi,

Does anyone know how to update the bios from a linux install only ? 
Is there some way to extract the bios from the exe or something like this ?

Thanks you :D

---

### Post by CIement on 2010-12-13
Hi, I am looking for a new laptop and while browsing at Best Buy I saw the R705 and thought it was fantastic. I really want to get it, but the only thing that's stopping me from getting one is the fact that there are some problems with Ubuntu working on it, and I would much prefer to use Ubuntu as opposed to Windows because it just makes life easier for me as a comp sci major. 

Would those of you who own this laptop still recommend it despite the problems it has? I'm not going to be doing much with it, just programming at home, bringing it to class on occasion or to a restaurant maybe. Could anyone please explain whatever problems I might be subject to experiencing if I do end up buying this laptop? Thanks for all the help!

---

### Post by omerp on 2010-12-13
Hi CIement,

I think if you stick to the 2.6.32 kernel (i.e., Ubuntu 10.04, or 10.10-and-then-downgrading-the-kernel), most of the problems identified in this thread would go away, or at least the solutions posted here would work for them.

The one glaring exception to this seems to be the wifi issues experienced by ksanger. It looks like somewhere in between the R705-P25 and the R705-P35, Toshiba changed the builtin wifi adapter from the Intel 6200 to, well, something else (Intel WiMAX/Wifi 6250?), and the latter has caused some problems. I don't know if ksanger ever figured those out.

I would check what the specific wifi hardware that the Portege you're looking at comes with. I have the R705-P25, and I must say -- having run Ubuntu before on two other laptops (a Dell and a Sony VAIO) -- that the Portege is easily the best Ubuntu machine I've had.

---

### Post by omerp on 2010-12-13
To ksanger and CIement:

It just so happened that today, Intel released new microcode images for both their 6250AGN and 6005AGN adapters on Linux.

I must say that I don't know what the propagation path of these into Ubuntu releases is -- in other words, how long you will have to wait to have these new microcode images bundled with a plain-vanilla Ubuntu distribution. On the other hand, installing them manually is a relatively painless affair. The microcode images, as well as installation instructions, can be found here:

[http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads)

(scroll down to the microcode image matching your hardware; the "R" link to the right leads you to the README, with installation instructions)

Ideally, this would clear up the problems you folks have been having with the newer Intel wifi adapters (though I'm only guessing; I can't test it myself, since I have the older 6200 model).

---

### Post by CIement on 2010-12-14
Alright thanks for the info! I'm just curious but how does the keyboard compare to the Macbook Pro one? I think the MBP keyboard is pretty good because it's really easy to type on but after a while it strains your fingers and wrist because there's such a short throw on the keys.

I'm going to be using this to write programs for school work, so I really need a good keyboard. 

Also, could you explain exactly what problems I'll encounter even after downgrading the kernel? I think in this thread some people were complaining about being able to control brightness, or having their laptop freeze up? Or maybe it won't start from cold? It would be nice if I could know what to expect if I do end up buying one.

---

### Post by solnyshok on 2010-12-18
Ola! I just might have good news. After applying new BIOS (from 2010-12-15), ver.1.8 cold freezes are gone. At least in my setup - latest Maverick kernel with all updates and backports applied. Tested it couple of times today on a cold machine, and not a single freeze.

BIOS changelog included specific mention of stability improvements for chipset and core-i processors, so I hope that's the much needed cure.

ACPI Flash BIOS version 1.80 for Portege R700/R705 (PT310U/PT311U/PT314U)(v1.80; 12-14-2010; 5.22M)

--------------------------------------
CHANGE HISTORY for Portege R700/R705
--------------------------------------

Version 1.80 2010-12-14
o Improved DeployCenter 5.5 recovery speed.
o Added support for the McAfee Endpoint Encryption eToken.
o Added support for 2011 non-Windows models.
o Implemented the INTEL specification for the Intel 5 Series Chipset to
improve stability.
o Implemented the INTEL specification for the Intel Core i7/i5/i3 Mobile
Processor Series to improve stability.
o Improved docker feature behavior - addresses missing undock Start Menu
option in Windows 7.
o Added support for the Paragon Backup & Recovery Suite.
o Improved USB device recognition.

[http://cdgenp01.csd.toshiba.com/content/support/downloads/t310v180.exe](http://cdgenp01.csd.toshiba.com/content/support/downloads/t310v180.exe)

(this link is from notebook review forums, for R630 I went to Toshiba site and downloaded BIOS from there, also v.1.8 )

---

### Post by fataki on 2010-12-19
No freezes after the 1.80 BIOS update. I have rebooted, suspended, hibernated and resumed multiple times during few hours.

---

### Post by GediminasB on 2010-12-19
Finally! I can fully move to Ubuntu :popcorn:

---

### Post by bakinsoda on 2010-12-19
@solnyshok does the new bios fix the system hang and shutdown issue that happens when we have the laptop unplugged?

---

### Post by solnyshok on 2010-12-19
> **bakinsoda said:**
> @solnyshok does the new bios fix the system hang and shutdown issue that happens when we have the laptop unplugged?seems to have solved  this problem for me.

---

### Post by bakinsoda on 2010-12-20
Sorry if this seems naive, but how are you guys updating the bios on an ubuntu system with a Win32 application?

---

### Post by popeye sweden on 2010-12-20
I too have bought the Toshiba portege R700 and want to install Ubuntu on it.
I understand that I should install the new version 10.10 but which one?
Should I install the 64bit, the 32 bit or the netbook version?

Thanks for the help.
Regards
popeye sweden

---

### Post by solnyshok on 2010-12-20
> Sorry if this seems naive, but how are you guys updating the bios on an ubuntu system with a Win32 application? 
I have kept Win7 dualbooting alongside Linux. Which was very necessary until this cold freeze problem was solved.
Did you already wipe out Windows? Other manufacturers like Asus, usually have bootable usb images for BIOS updates, but I am not sure if Toshiba has it.

---

### Post by bakinsoda on 2010-12-20
If anyone that is interested, I updated the BIOS by booting into FreeDOS.  Instructions can be found [here]("http://blog.nguyenvq.com/2010/12/20/update-system-bios-on-a-linux-machine-with-a-windowsdos-updater/").

---

### Post by fataki on 2010-12-22
> **connect404 said:**
> 
[SIZE=2][COLOR=Green]Keyboard[/COLOR][/SIZE][SIZE=2][COLOR=Green]
[/COLOR][/SIZE]
[LIST]
[*]2 dedicated hardware buttons (email & web in windows i think) can be assigned to a function via keyboard shortcuts... but they both appear as the same button "Mod4+X"
[*]F1-F12 are the default action, with Fn being secondary
[*]Most Fn modifiers work fine. Can vol+ & vol-, mute, suspend, numberpad etc
[*]**Touchpad & Display switch Fn modifiers dont function, and are not programmable. Triggering them does not register any type of keypress. Suspect these are hardware set and will never be accessible.**
[*]Wifi hotkey only turns Bluetooth module on and off. Could be fixed with some acpi scripting if needed
[/LIST]
[/COLOR][/SIZE]

Display switch (Fn+F5) is now working, don't know what fixed it and when.

---

### Post by anydroid on 2010-12-23
> **bakinsoda said:**
> @solnyshok does the new bios fix the system hang and shutdown issue that happens when we have the laptop unplugged?

BIOS update did _not_ fix cold-boot-on-battery lockups for me

---

### Post by sumwon on 2010-12-24
I am using Mint X [with the Ubuntu kernel] on my R705. I just want to add here that I initially encountered no problems with any hardware, aside from the inaccessibility of Toshiba-specific keys. I don't use Bluetooth so I can't vouch for that, but i have yet to engage in any real troubleshooting on this machine.

I finally got to checking the logs and notice i'm  getting an MCP error message that has been previously posted on, in addition to acpi errors at boot:

intel ips 0000:00:1f.6: MCP power or thermal limit exceeded

the error is regular but less common than it seems to have been for other users, but i'm still noticing a high idling frequency even when the error isn't being reported, with the chassis hot to the touch. The temp hasn't execeed 60C, but apparently this is still too hot. i encounter the error booting from both battery and AC, and it seems to occur mostly when the machine is idle. to summarize what i've read on this thread and elsewhere, this problem appears to be the result of the current 2.6.35 kernel being unable to run the i3/i5/i7 series processors in low power mode. the forthcoming .36 kernel does not appear to address this issue either. i've had no issues with crashing, freezing or fan operation, but i'm definitely concerned since the hardware wasn't designed to run with an inefficient CPU, and running the CPU beyond its thermal limit can reduce its lifespan or kill it.

Someone said they hadn't seen this MCP error on a 705, but I can assure you I'm seeing it. I have an i3, so i'm not sure if this makes a difference. 

Just curious to know if anyone else on this thread is still having this problem, or if i possibly overlooked a solution. The only solutions I am seeing are:

1) disabling ips logs
2) rolling back the kernel

While the following solutions i have personally ruled out:

-bios update
-intel microcode update

From what i have read, ips alerts only disappear with a rollback to 2.6.32 because such errors weren't logged in the previous kernel, so basically both are only ignoring the issue, thus none of these offers any solution.

Looking into running toshset, but I'm not seeing any indication it will be effective at addressing this issue. Also wondering if manually setting the thermal limit might be an option. Either way, without a solution this issue is a border-line deal breaker for me, so perhaps it could be noted on the first post under a Power Management or CPU header. Either way, its too late for me, so I'll be searching tirelessly for a solution...

---

### Post by moimael on 2010-12-25
> **bakinsoda said:**
> If anyone that is interested, I updated the BIOS by booting into FreeDOS.  Instructions can be found [here]("http://blog.nguyenvq.com/2010/12/20/update-system-bios-on-a-linux-machine-with-a-windowsdos-updater/").

Hi, i tried to make a freedos usb key with unetbootin and flash from it but everytime i launch chgbiosf.exe, it launches but nothing appends.

Is there something special to do ?

---

### Post by bakinsoda on 2010-12-25
> **moimael said:**
> Hi, i tried to make a freedos usb key with unetbootin and flash from it but everytime i launch chgbiosf.exe, it launches but nothing appends.

Is there something special to do ?

I did not use unetbootin.  Try following the instructions on the above post (or the linked post on that blog for further details).

---

### Post by bakinsoda on 2010-12-30
> **anydroid said:**
> BIOS update did _not_ fix cold-boot-on-battery lockups for me

Same for me, although I think it happens LESS frequently.

---

### Post by anydroid on 2011-01-08
I tried patching my kernel (2.6.35-24-generic i686) with a toshset patch, as recommended by [this]("https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/644898/comments/13") bug post on launchpad.

Build fine, installation fine, but I still get:
```
anydroid@tosh:~$ toshset
required kernel toshiba support not enabled.

```

---

### Post by god_at_hell on 2011-01-10
I just looked at the gnome-power-monitor while recharging my r630. It seems there is something wrong with the acpi-module, since the rate you get while recharging isn't the energy which goes into the battery, but the energy the system consumes. Since gnome-power-manager estimates the time to recharge by this rate, this has to be an error.
For example:
system idles with backlight low: rate = ~9W; time to recharge = ~7.5h
system idles with backlight full: rate = ~11W; time to recharge = ~5.5h

When I calculate the rate by looking at the battery charge i get in one hour, I get an average rate of 26W/h which looks quite correct.

---

### Post by omerp on 2011-01-10
> **anydroid said:**
> I tried patching my kernel (2.6.35-24-generic i686) with a toshset patch, as recommended by [this]("https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/644898/comments/13") bug post on launchpad.

Build fine, installation fine, but I still get:
```
anydroid@tosh:~$ toshset
required kernel toshiba support not enabled.

```

You should check to see if you have another [FONT="Courier New"]toshiba_acpi.ko[/FONT] somewhere, superseding the [FONT="Courier New"]toshiba_acpi.ko[/FONT] you compiled. On my system, I had a [FONT="Courier New"]/lib/modules/2.6.35-24-generic/kernel/drivers/platform/x86/toshiba_acpi.ko[/FONT] that was preventing the compiled one, which was placed in [FONT="Courier New"]/lib/modules/2.6.35-24-generic/extra/toshiba_acpi.ko[/FONT], from being loaded.

---

### Post by rob61280 on 2011-01-12
> **omerp said:**
> You should check to see if you have another [FONT="Courier New"]toshiba_acpi.ko[/FONT] somewhere, superseding the [FONT="Courier New"]toshiba_acpi.ko[/FONT] you compiled. On my system, I had a [FONT="Courier New"]/lib/modules/2.6.35-24-generic/kernel/drivers/platform/x86/toshiba_acpi.ko[/FONT] that was preventing the compiled one, which was placed in [FONT="Courier New"]/lib/modules/2.6.35-24-generic/extra/toshiba_acpi.ko[/FONT], from being loaded.

Has anyone had success in patching the kernel as described with regard to stopping the r700 overheating? 

Regards
Rob

---

### Post by anydroid on 2011-01-17
> **omerp said:**
> You should check to see if you have another [FONT="Courier New"]toshiba_acpi.ko[/FONT] somewhere, superseding the [FONT="Courier New"]toshiba_acpi.ko[/FONT] you compiled. On my system, I had a [FONT="Courier New"]/lib/modules/2.6.35-24-generic/kernel/drivers/platform/x86/toshiba_acpi.ko[/FONT] that was preventing the compiled one, which was placed in [FONT="Courier New"]/lib/modules/2.6.35-24-generic/extra/toshiba_acpi.ko[/FONT].

Thanks for the tip; I replaced the module at [FONT="Courier New"]/lib/modules/2.6.35-24-generic/kernel/drivers/platform/x86/toshiba_acpi.ko[/FONT] with the one newly built one from [FONT="Courier New"]/lib/modules/2.6.35-24-generic/extra/toshiba_acpi.ko[/FONT].

The toshset module is now loading, but its options don't seem to do anything -- admittedly I haven't tested this a lot. From memory, toggling [FONT="Courier New"]--cpu low|high[/FONT] always returns "CPU High" and [FONT="Courier New"]--fan low|high[/FONT] always returns "fan high".

---

### Post by omerp on 2011-01-17
> **anydroid said:**
> The toshset module is now loading, but its options don't seem to do anything -- admittedly I haven't tested this a lot. From memory, toggling [FONT="Courier New"]--cpu low|high[/FONT] always returns "CPU High" and [FONT="Courier New"]--fan low|high[/FONT] always returns "fan high".

I'm not 100% sure of this, but I don't think those options used to have an effect (back in 2.6.32), either. The reason I needed toshset, and why I went through the process of building it on 2.6.35, is for the "toshset -bl on" kludge that enabled changing brightness after resume from suspend.

---

### Post by connect404 on 2011-01-17
So, a few weeks on whats the verdict on 1.80? Is the Maverick kernel stable now?

---

### Post by god_at_hell on 2011-01-17
At work I'm always on battery and there were no freezes with Maverick and BIOS version 1.8 for me.

The only remaining problems for me are:
- poor battery status ... the power-manager reports the overall capacity fell to ~87% in one week O_o .. this can not be right
- wlan I can not be disabled ... I have to evaluate i unloading the module switches off the broadcom chip
- sometimes the laptop doesn't shutdown like it should, but it just hangs after unmounting the harddrive and killing all the services
- brightness locks after suspend to ram (fixable ... see page one of this thread) or while using an external display
- there are some errors at boot (ACPI and intel graphic related)
- two finger scrolling doesn't work for me ... even if I enable it with gconf-editor :-( 

and something I that should not be hardware related :D
- sometimes gnome doesn't start with the set theme, but in some ugly mode. 

This wraps it up.

---

### Post by omerp on 2011-01-17
> **god_at_hell said:**
> - two finger scrolling doesn't work for me ... even if I enable it with gconf-editor :-( 

Take a look at the code that connect404 has in the original post. Worked for me! (You have to make it run on every login, via Startup Applications or something.)

> **god_at_hell said:**
> - sometimes gnome doesn't start with the set theme, but in some ugly mode. 

I've occasionally encountered that; if it happens, do the following:
[LIST]
[*]open the Appearance app from Gnome Menu-->System-->Preferences
[*]wait a moment
[*]it should then fix everything except the icons on the desktop; to do that, type "nautilus -q" from a terminal -- it will restart nautilus and refresh the desktop icons to match the correct theme
[/LIST]

---

### Post by god_at_hell on 2011-01-18
> **omerp said:**
> Take a look at the code that connect404 has in the original post. Worked for me! (You have to make it run on every login, via Startup Applications or something.)

Ah ... I think i overlooked this ... thanks. It's now working :D

A new thing regarding the carge level of the battery. I think we can delete this sections, 'cause it doesn't seem to be OS related. Windows users report the same behaviour (look [here]("http://forum.notebookreview.com/toshiba/493524-portege-r700-thin-light-13-3-a-56.html")) and I checked it myself.
In both OS (linux and windows)...
[LIST]
[*]the battery reports an incidental wear level of 8.5% (for me it's now 13% :( )
[*]the displayed charge rate wile recharging is the actual energy consumption of the system and NOT the charge rate. The later is around 24W.
[/LIST]
Also I don't think the reported charge levels reported are wrong ... for me they seem to be right. 
Furthermore the accuracy displayed by the gnome power manager is 100% after 5 dis-/recharge cycles. I think the developers of the statistic function just implemented the tool this way. The incident poor accuracy is just a formality. On the other hand, it's a little bit missleading, since 100% accuracy in reality is unreachable.

---

### Post by god_at_hell on 2011-01-19
After some fiddling around i can now kill my wireless lan connection by using the wireless fn-key. This works for all r70x/r630 versions which use the wlan chip BCM4313 from Broadcom.
The big difference between lucid and maverick was for me, that maverick supported most of the fn-keys out of the box as normal keypress events and disabled most of the acpi-events from this keys. Lucid on the other hand provides acpi-events, but you have to bind there yourself.
In maverick you send a rfkill signal when you press the wireless key, but the old broadcom-sta module (5.60.48.36-2) doesn't support rfkill for the appropriate chip.

To fix this:
[LIST]
[*]download the newest broadcom sta driver sources [[here]("http://www.broadcom.com/support/802.11/linux_sta.php")]
[/LIST]
I choose the 64bit driver.
Create a new folder, extract sources and build module:
```

mkdir broadcom_wl
cd broadcom_wl
tar -xzf <path to tar-file>/hybrid-portsrc_x86-64_v5.100.82.38.tar.gz
make clean
make
ls

```
After this, you'll see a file called wl.ko in the folder.

For the next step unload the wl module with:
```
sudo rmmod wl
```
Now remove any remaining traces of the ubuntu version of the wl module (remove the package "bcmwl-kernel-source" and/or "broadcom-sta-*" with synaptic) and check if there is no wl.ko in "/lib/module/<kernel-version>/updates/dkms/".
Now copy the new wl.ko into a module subfolder (e.g. "/lib/module/<kernel version>/extra/") and reload the module:
```

sudo cp wl.ko /lib/module/<kernel version>/extra/wl.ko
sudo depmod
sudo modprobe wl

```

The wireless fn-key should now work like it should. You can check if rfkill finds the new driver with:
```
rfkill list all
```
You should see something like this:
```

4: brcmwl-0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no

```
The wireless fn-key toggles the soft blocked status.

You could also use DKMS for managing the module. If you want do do this ... look [here]("https://help.ubuntu.com/community/DKMS").

---

### Post by auvie on 2011-02-08
Hi there,

I noticed that the Toshiba Tecra R700 has the status of "certified" for Ubuntu 64-bit PC (x86_64), yet this thread suggests it probably shouldn't have such status.  I've installed 64-bit 10.10, and the first issue I've run into involves the power status.  I can look up the information in /proc/acpi, yet I do not get an icon appearing on the panel, even when I select "always display an icon" in the power management options.  Also, suspend and hibernate are not working properly, all they do is turn off the screen... as soon as the mouse is moved, it comes back on.

My BIOS is already at version 1.8, and I have also seen suggestions of downgrading to kernel 2.32... I can't seem to find an appropriate kernel in Synaptic to do so.  Does anyone have any suggestions regarding this, or perhaps additional advice?

Thanks,
Adam

---

### Post by auvie on 2011-02-08
So I fooled around with ACPI a bit and realized that the permissions weren't set to allow my regular user account to do things like suspend, etc.  When I allowed access, suddenly gnome-power-manager started working great.  However, the permissions reset upon reboot.

while I could make it so the permissions are set each time after booting, it doesn't make sense that I should have to do this after freshly installing Ubuntu.  Any ideas?

---

### Post by anydroid on 2011-03-10
For all those still struggling with Ubuntu on the R700, another [BIOS update]("http://uk.computers.toshiba-europe.com/innovation/download_drivers_bios.jsp?service=UK&mode=allMachines&action=search&teddProduct=5379&selShortMod=1019") has emerged (1.90-WIN_EC1.40).

My laptop won't associate with a WPA2 network when running on battery only; but it's quite happy to leech off my neighbour's unsecured network.

I've already built the latest BCM4313 firmware ([500.100.82.38]("http://www.broadcom.com/support/802.11/linux_sta.php")) against my kernel (2.6.35-27-generic i686) but didn't notice any improvements over the Linux STA version shipping with Maverick.

Log of successful WPA2 connection, on AC:
```

Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) starting connection 'Auto Galactica'
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  completed -> disconnected
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0/wireless): access point 'Auto Galactica' has security, but secrets are required.
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> (eth0): device state change: 5 -> 6 (reason 0)
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> (eth0): device state change: 6 -> 4 (reason 0)
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0/wireless): connection 'Auto Galactica' has security, and secrets exist.  No new secrets needed.
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Config: added 'ssid' value 'Galactica'
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Config: added 'scan_ssid' value '1'
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Config: added 'psk' value '<omitted>'
Mar 10 11:29:53 tosh NetworkManager[1128]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 10 11:29:53 tosh NetworkManager[1128]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> Config: set interface ap_scan to 1
Mar 10 11:29:53 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  disconnected -> scanning
Mar 10 11:30:24 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  scanning -> associating
Mar 10 11:30:25 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  associating -> associated
Mar 10 11:30:25 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  associated -> 4-way handshake
Mar 10 11:30:25 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  4-way handshake -> group handshake
Mar 10 11:30:25 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  group handshake -> completed
Mar 10 11:30:25 tosh NetworkManager[1128]: <info> Activation (eth0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Galactica'.

```

Unsuccessful WPA2 connection, running on battery:
```

Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) starting connection 'Auto Galactica'
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0/wireless): access point 'Auto Galactica' has security, but secrets are required.
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> (eth0): device state change: 5 -> 6 (reason 0)
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> (eth0): device state change: 6 -> 4 (reason 0)
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0/wireless): connection 'Auto Galactica' has security, and secrets exist.  No new secrets needed.
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Config: added 'ssid' value 'Galactica'
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Config: added 'scan_ssid' value '1'
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Config: added 'psk' value '<omitted>'
Mar 10 11:55:53 tosh NetworkManager[1128]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 10 11:55:53 tosh NetworkManager[1128]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> Config: set interface ap_scan to 1
Mar 10 11:55:53 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  disconnected -> scanning
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  scanning -> associating
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  associating -> associated
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  associated -> 4-way handshake
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  4-way handshake -> group handshake
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> (eth0): supplicant connection state:  group handshake -> completed
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> Activation (eth0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Galactica'.
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> dhclient started with pid 4042
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar 10 11:55:54 tosh NetworkManager[1128]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Mar 10 11:56:40 tosh NetworkManager[1128]: <warn> (eth0): DHCPv4 request timed out.
Mar 10 11:56:40 tosh NetworkManager[1128]: <info> (eth0): canceled DHCP transaction, DHCP client pid 4042
Mar 10 11:56:40 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Mar 10 11:56:40 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Mar 10 11:56:40 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 10 11:56:40 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Mar 10 11:56:40 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Mar 10 11:56:40 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Mar 10 11:56:40 tosh NetworkManager[1128]: <info> (eth0): device state change: 7 -> 9 (reason 5)
Mar 10 11:56:40 tosh NetworkManager[1128]: <warn> Activation (eth0) failed for access point (Galactica)
Mar 10 11:56:40 tosh NetworkManager[1128]: <info> Marking connection 'Auto Galactica' invalid.
Mar 10 11:56:40 tosh NetworkManager[1128]: <warn> Activation (eth0) failed.
Mar 10 11:56:40 tosh NetworkManager[1128]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 10 11:56:40 tosh NetworkManager[1128]: <info> (eth0): device state change: 9 -> 3 (reason 0)
Mar 10 11:56:40 tosh NetworkManager[1128]: <info> (eth0): deactivating device (reason: 0).

```

Any tips ?!

---

### Post by god_at_hell on 2011-03-12
Does anyone know what the changes for this update are? I find the description on the toshiba page ("This Bios Update adds increased functionality to your system.") somewhat unclear.

---

### Post by egemenaydin on 2011-03-19
Hello everyone. I was having freezing issues on my R705. After upgrading BIOS to 1.80 the problem had been solved. However, updating the kernel to 2.6.35-28 has the problem emerged again. While working on battery, system freezes and fan works like crazy.  I turned back to the kernel 2.6.35.22 there is no freezing problem so far.

---

### Post by egemenaydin on 2011-03-30
> **egemenaydin said:**
> Hello everyone. I was having freezing issues on my R705. After upgrading BIOS to 1.80 the problem had been solved. However, updating the kernel to 2.6.35-28 has the problem emerged again. While working on battery, system freezes and fan works like crazy.  I turned back to the kernel 2.6.35.22 there is no freezing problem so far.

Update: I am again experiencing freezing problem with kernel 2.6.35-22, too.

---

### Post by DarkTide on 2011-03-30
Thanks for the post! It has been very useful for some one as new to ubuntu as me
I'm glad to meet you
best wish for you :)

---

### Post by titao on 2011-04-02
hi,

i own a toshiba r630-155 and i only have linux installed. how can update bios??i've tried to update from win95 cd console, freedos and with win xp cd i couldn't get a console. with win95 and freedos i always got the message that the installer must be run from a win32 system.
anyone knows what can i do to update without installing windows?

thanks

---

### Post by janvanmaar on 2011-04-08
titao, I did a successful BIOS upgrade using Linux only by following the instructions from this link:
[http://blog.nguyenvq.com/2010/12/20/update-system-bios-on-a-linux-machine-with-a-windowsdos-updater/](http://blog.nguyenvq.com/2010/12/20/update-system-bios-on-a-linux-machine-with-a-windowsdos-updater/)
It does not go to full details in all steps, let me know if you happen to need more help/information about something.

---

### Post by Shepherd X on 2011-04-14
Anyone know if the Toshiba Portege R835 hardware is as compatible with Ubuntu as the R705? I don't know what's changed except for the Intel Sandy Bridge processor in the R835 model.

---

### Post by omerp on 2011-04-14
More brightness goodness...:

There's one thing that the "cleaner" brightness fix -- the one based on *toshset* and discussed in post #10 of this thread -- never managed to take care of: after resuming from suspend, brightness changes initiated by gnome-power-manager (for example, if you had your system set to dim the brightness after some period of inactivity) would not be reflected in the actual brightness of the screen. This would actually sometimes create weird situations where the first time after suspend that you changed the brightness manually (assuming you already had the post-#10-based brightness fix in place), the brightness would first "jump" to where gnome-power-manager had tried to put it, and then you would have to start adjusting from there.

Well, I found a fix for this. It is based on creating a script that listens to the relevant dbus signal reflecting gnome-power-manager's attempts to change the brightness, and calls "toshset -bl on" when that happens. Since it's listening using IO-blocking, the listener doesn't use any extra CPU while nothing is happening.

Here's what you need to do. Create two scripts. The first is called "gpm-monitor":

```
#! /usr/bin/env python

import sys
import os

while True:
    line = sys.stdin.readline()
    if 'uint' in line:
        os.system('toshset -bl on')


```The second is called "gpm-monitor-wrapper":

```
#! /bin/bash

dostuff() {
    dbus-monitor --session "type='signal',interface='org.gnome.PowerManager.Backlight',member='BrightnessChanged'" | gpm-monitor
}

dostuff &
disown %


```Put them both somewhere like /usr/local/bin, and then just make sure gpm-monitor-wrapper is run with root permissions every time you login.

(If you are a newbie and don't know how to put things in /usr/local/bin or run things with root permissions, take a look at the documentation for the "sudo" command. What I actually ended up doing was using the Gnome "Startup Applications" facility to start "sudo gpm-monitor-wrapper" upon login, and just made sure my "sudoers" file let that particular command through without asking for a password.)

---

### Post by noctis2 on 2011-04-16
> **omerp said:**
> More brightness goodness...:


I'll get an Error when executing the script in line 8 from gpm-monitor. 
"IndentationError: unepected indent".

---

### Post by omerp on 2011-04-16
> **noctis2 said:**
> I'll get an Error when executing the script in line 8 from gpm-monitor. 
"IndentationError: unepected indent".

Ah yes, the perils of Python...

Make sure that all the indentation in gpm-monitor matches: the first two lines after the 'while' statement should be indented by one tab, and the one after that (which starts with 'os.system') should start with 2 tabs. Also, make sure your text editor of choice is not replacing these with spaces (or that if it is, it is replacing *all of them* with spaces; really, the crucial bit is that the indentation of the last line *starts* with the indentation that the lines before it had).

Sorry about that.

---

### Post by noctis2 on 2011-04-17
> **omerp said:**
> Ah yes, the perils of Python...

Make sure that all the indentation in gpm-monitor matches: the first two lines after the 'while' statement should be indented by one tab, and the one after that (which starts with 'os.system') should start with 2 tabs. Also, make sure your text editor of choice is not replacing these with spaces (or that if it is, it is replacing *all of them* with spaces; really, the crucial bit is that the indentation of the last line *starts* with the indentation that the lines before it had).

Sorry about that.

Yes the tabs were replaced with spaces.
Now it works! Thanks a lot!

---

### Post by rp1987 on 2011-04-20
Hi all,

Am kinda new to Ubuntu. Using 10.10 Maverick. I have an 500GB extn with a lot of important data. The company and make of the external is "Western Digital My Passport Essential". The prob am facing is that it has an executable called unlock.exe which is compatible for Windows and to my knowledge in Mac. But am unable to unlock the drive and access my files in the OS that am using currently. Pls help me out with this. 

I have fast approaching deadlines immediately after the Easter break and I dont wanna end up working in the last min (like I always do).

Thanks in advance.

Cheers,
rp

---

### Post by Shepherd X on 2011-04-20
oops

---

### Post by stephanosg on 2011-04-25
Chiming in late to this thread I'm the owner of an R700-1DG [edit: BIOS 2.10, Firmware 1.40]. Going to be trying Natty beta 2 shortly but these are the only points I have to say about running 10.10 for a couple of weeks:

Everything seems to work for me out of the box (Fn keys, brightness etc, even the 3G was recognised with no manual intervention on my part).

Does seem to run rather hot (acpitool reported 53 degs. C and the back left does get warm). Lowest clock I see on the CPU seems to be 933MHz, I've not seen 600 yet)
As others seem to have found battery life is a bit of a black art.

One thing I've noticed that others haven't is that even at idle I *always* have a loadavg of 1. No running processes that I can see, nothing blocking, no zombies, nada. I even rebuilt the thing and it's consistently there. Powertop tells me that the i915 kernel module seems to be causing alot of wakeups (ditto iwlagn when the wireless is on) but if I disable networking and boot to the console I still have the mysterious load average.

Anyway I'm going to try Natty now and see what that looks like.

---

### Post by stephanosg on 2011-04-26
Well 11.04b2 installed just fine as well (again R700-1DG; BIOS 2.10, Firmware 1.40). Notable things I've seen so far:

o two finger scrolling available now in the system preferences
o acpitool can't read temperatures any more...
o ... but lm-sensors now can:

```

steph@magnesium:~$ acpitool 
  Battery #1     : charged, 100.0%
  AC adapter     : on-line 
  Thermal info   : <not available>
steph@magnesium:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +24.0°C  (crit = +107.0°C)  

```o I still have the mystery load-average of 1 :confused:
o in Firefox (maybe other things too but I saw it there first) I've had trouble a couple of times clicking with the mouse: left-click doesn't work on OK buttons, can't highlight text etc. 
o no longer have the Intel MCP (or whatever it was) overheating message in the logs

---

### Post by JacquiOh on 2011-05-01
Hi everyone

Considering the upgrade to 11.04...

But I have to select an old kernel now to keep my laptop from crashing everytime I unplug it. Will that still be there for me to select if I upgrade?

---

### Post by stephanosg on 2011-05-01
> **JacquiOh said:**
> Hi everyone

Considering the upgrade to 11.04...

But I have to select an old kernel now to keep my laptop from crashing everytime I unplug it. Will that still be there for me to select if I upgrade?

Hola (drunk)

A few days in now to 11.04 and the only side effect I've seen is slightly odd behaviour (and really very occasionally) with the trackpad. Subjectively it doesn't feel anywhere near as hot as 10.10. As for crashes, talking out of my **** I don't see why reverting to an older kernel would be any harder. Being brazen (again, drunk!) I'd suggest taking a full backup and trying to upgrade/reinstall 11.04

---

### Post by samoht9 on 2011-05-04
In regard to brightness, I tried all of the script changes and shortcuts on here, but nothing would work for me.  Stumbled on something in the Fedora forums that did work however.  Instead of suspending to ram I set Ubuntu to hibernate and suspend to disk.  For whatever reason when waking from a hibernate state I was able to change the brightness without an issue.  Suspending to ram still doesn't allow brightness to function even with the fixes previously provided implemented.  (Note I did not try patching the tosh-set drivers on the latest kernel).

I am not sure why this works, but it appears that it does.  If anyone has any insight into why this functions the way it does I would love to know why.

---

### Post by omerp on 2011-05-04
> **samoht9 said:**
> In regard to brightness, I tried all of the script changes and shortcuts on here, but nothing would work for me. [...] (Note I did not try patching the tosh-set drivers on the latest kernel).

Why you would expect any of this to work without a functioning *toshset* command is beyond me.

> **samoht9 said:**
> Stumbled on something in the Fedora forums that did work however. Instead of suspending to ram I set Ubuntu to hibernate and suspend to disk. For whatever reason when waking from a hibernate state I was able to change the brightness without an issue. Suspending to ram still doesn't allow brightness to function even with the fixes previously provided implemented.

I am not sure why this works, but it appears that it does. If anyone has any insight into why this functions the way it does I would love to know why. 

I'm fairly sure this was also mentioned earlier in this thread, but what the heck: resuming from hibernate (a.k.a. suspend-to-disk) is basically like rebooting; your machine goes through the regular power cycle that it goes through on every boot (you'll notice that you even go through the grub boot menu when your machine is "resuming"). So of course, the chipset is at the same state that it would be at after a reboot.

---

### Post by solnyshok on 2011-05-14
My experience with Natty is so far much better than with Maverick. No freezes. I did clean reinstall on my R630. Out of the gate there is no working toshset and 2 finger scroll, and brightness adjustment fails after suspend.

But now there is option for enabling 2 finger scroll in mouse settings and it works.

Today, I used tips from [https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/644898?comments=all](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/644898?comments=all)
to get toshset working with 2.6.38.9-generic kernel
I took pre-compiled fixed toshiba_acpi.ko and copied into 2 locations, rmmod, modprobe and voila toshset is working now.

sudo rmmod toshiba_acpi
put precompiled toshiba_acpi.ko as root into
/lib/modules/2.6.38-9-generic/extra (replace with your current kernel version, had to creat folder 'extra').
/lib64/modules/2.6.38-9-generic/kernel/drivers/platform/x86
sudo modprobe toshiba_acpi

for brightness had to add new keyboard shortcuts for FN+F6, and FN+F7. both commands are {sudo toshset -bl on} without {}

So far, I am happy bunny. Uh, also noticed, that with Natty, laptop runs much cooler and works for 5 hours instead of 3-3.5 as before.

---

### Post by solnyshok on 2011-05-14
bluetooth is always off when my laptop boots and after suspend.

Somehow, in order to activate bluetooth, I need to send "off" command first, otherwise it doesn't work. so I added this command as shortcut:
sh -c "sudo toshset -bluetooth off && sudo toshset -bluetooth on &"

to turn it off "sudo toshset -bluetooth off" is enough.

---

### Post by stephanosg on 2011-05-16
> **solnyshok said:**
> So far, I am happy bunny. Uh, also noticed, that with Natty, laptop runs much cooler and works for 5 hours instead of 3-3.5 as before.Ditto. Question though, do you have the mystery load average of 1 problem as well?

---

### Post by chris23 on 2011-05-17
Hi to all,
I just installed in my R700 the ubuntu natty. 
I have a few questions, if anyone could help it would be very nice.

As another friend is previous post..i have problem with the touchpad..OK buttons cannot be click...very weird...

Would toshset resolve this? what is toshset exactly?

Also, can i make use of the two buttons on the right corner? the eco and the output one? what did u do with them?

---

### Post by stephanosg on 2011-05-17
> **chris23 said:**
> As another friend is previous post..i have problem with the touchpad..OK buttons cannot be click...very weird...
I saw that only once or twice and only initially after install. I don't see it any more so it may go away for you as you install updates.

---

### Post by solnyshok on 2011-05-17
> **stephanosg said:**
> Ditto. Question though, do you have the mystery load average of 1 problem as well?
Yes, I have. Is that bad? What does it mean? 
This is the most power efficient and most responsive ubuntu install I ever had, but I need to note, that under W7, CPU scales down to 25% of max frequency, while in ubuntu only to 50%.

---

### Post by stephanosg on 2011-05-19
> **solnyshok said:**
> Yes, I have. Is that bad? What does it mean? 
This is the most power efficient and most responsive ubuntu install I ever had, but I need to note, that under W7, CPU scales down to 25% of max frequency, while in ubuntu only to 50%.Well it's not bad, per se I'd just like to understand where it's coming from [(See this for a description of what the load average means)]("http://www.linuxjournal.com/article/9001"). I've booted mine without X and tried to shut down as much as I can and it still seems to be doing *something* so my best guess at the moment is a misbehaving driver or the like. I've not had much time to poke around though. As for CPU scaling, yeah I think folks have said upthread that it's not scaling all the way back (I've never seen mine slower than 933MHz which still seems high to me).

[EDIT] Found it, it's caused by the intel_ips kernel module and power saving driver. Looks like it's spurious and can be ignored, and hopefully a fix is on the way (see this [U]kernel mailing list discussion about it)

[/U]

---

### Post by chris23 on 2011-05-19
guys is your microphone working ? it doesn't show up as input in sound preferences...

---

### Post by solnyshok on 2011-05-21
I have R630, and microphone works in Natty. No issues at all.

---

### Post by chris23 on 2011-05-21
OK i figure it out. it was not allowed in the users settings.

Can anybody tell me if i install toshset what else should i except than the brightness functionality after resume?

---

### Post by noctis2 on 2011-05-22
Is their any chance to adjust the saturation of the screen? The display of my R630 looks a little greyish and with the windows driver of intel hd thers an option to increase the saturation, but in ubuntu i havent find any also after hours of searching.

---

### Post by anydroid on 2011-05-22
+1
I'm much happier with performance under Natty, even though Natty itself seems to have some issues. For me they are:
[LIST=1]
[*]Random logouts, getting kicked back to GDM login
[*]Occasional freezes (max fan) requiring hard reset... although much less frequent with Natty
[*]Some panel applets fail to load with Gnome Classic Desktop, esp. CPU freq monitor.
[/LIST]

I haven't bothered with toshset as everything I need seems to be working...

---

### Post by omerp on 2011-05-22
--> **anydroid**: Do your brightness controls work after suspend, without toshset? (Or did you mean that this is just not part of "everything you need", which would be totally understandable...?)

---

### Post by anydroid on 2011-05-23
> **omerp said:**
> --> **anydroid**: Do your brightness controls work after suspend, without toshset? (Or did you mean that this is just not part of "everything you need", which would be totally understandable...?)

Brightness controls are not working after suspend, but I rarely use suspend and even when I do the resume-brightness isn't annoyingly high.

---

### Post by B-Town on 2011-05-28
Hi I'm running Kubuntu 11.04 on by Portege R705 mostly without problems.  I do have a couple of issues and was wondering if anyone had any ideas.

1) I've installed Toshset and it runs (i.e. I followed the instructions on patching the kernel) and I can use it to fix the brightness after suspend issue. However, the first time I run toshset it messes up the KDE battery applet (basically applet thinks I don't have a battery at all--I'm not expert enough to know what other parts of the system are affected).

2) Occasionally after a suspend the computer completely freezes. The desktop comes back up but the mouse is frozen and no keyboard commands seem to do anything either (i.e I can't switch to a different terminal).  This never happened to me in 10.10 and it happens infrequently enough that I don't have any idea what might be triggering the behavior.  (I never got around to installing toshset on 10.10 if it makes a difference).

Otherwise things are working great...

Thanks!

---

### Post by anydroid on 2011-05-30
Freeze after suspend only emerged after I applied the toshset patch to 11.04.

Anyone else experiencing random logouts ?!

---

### Post by solnyshok on 2011-05-31
yes, I have had 2 random logouts and one freeze during last 2 weeks. Cannot see any system in that though, except that I also have patched toshset and it happens only when not plugged in.

---

### Post by chris23 on 2011-06-02
is anyone experiencing low volume?

---

### Post by omerp on 2011-06-02
> **chris23 said:**
> is anyone experiencing low volume?

Through speakers or line out?

---

### Post by chris23 on 2011-06-02
> **omerp said:**
> Through speakers or line out?

through the speakers mate

---

### Post by omerp on 2011-06-02
> **chris23 said:**
> through the speakers mate

Gotcha. Are you sure it's a Ubuntu thing? (In other words, do they behave any better under Windoze?)

I have to say, I have always found the internal speakers on the Portege to be unbelievably bad. It's the one thing I don't like about the hardware on this laptop (admittedly, it's a feature I rarely use, so it's not that big of a deal).

---

### Post by chris23 on 2011-06-02
> **omerp said:**
> Gotcha. Are you sure it's a Ubuntu thing? (In other words, do they behave any better under Windoze?)

I have to say, I have always found the internal speakers on the Portege to be unbelievably bad. It's the one thing I don't like about the hardware on this laptop (admittedly, it's a feature I rarely use, so it's not that big of a deal).


yes i am  pretty sure that in windows were much much louder...
maybe theres a fix somewhere...but its ok for me..i use speakers :)

---

### Post by B-Town on 2011-07-05
On a related sound issue. Does anyone have the following problem?

If  you set the microphone to a given volume then when used (in Skype at  least) the volume decays to  a nearly silent level.  This seems to make  it difficult for the other person to hear you.  Literally in the mxer  you can see the sound drop a level every second or so.

If on a portege r705 41 with Kubuntu 11.04.
This didn't seem to happen in 10.10.

Thanks.

---

### Post by omerp on 2011-07-05
> **B-Town said:**
> If  you set the microphone to a given volume then when used (in Skype at  least) the volume decays to  a nearly silent level.  This seems to make  it difficult for the other person to hear you.  Literally in the mxer  you can see the sound drop a level every second or so.

The following worked for me:

In Skype: Options --> "Sound Devices" --> uncheck "Allow Skype to automatically adjust my mixer levels."

It's not a perfect solution, of course, since ideally you'd like auto level-adjustment, but apparently some wires get crossed between Skype and pulseaudio(?)

---

### Post by lyaya on 2011-07-11
Hi

I'm on a recent R700 on oneiric.

FYI, the device doesn't halt with:
[LIST]
[*]2.6.38-8.42
[*]2.6.39-02063903.201107091121
[*]3.0.0-4.5
[/LIST]

And it doesn't suspend with 3.0. (it got stuck, have to shut it down by holding the power button for 5sec)

---

### Post by anydroid on 2011-07-17
After six trouble-free months I hit a big wall with this machine.

Recent updates on 11.04 prevented me logging into X as anyone but root. GDM wouldn't launch from the command line, but would if called via "logout" from root's desktop. All desktops were unresponsive, with Gnome Classic hanging entirely.

I think the problem was related to wireless drivers as the machine was hanging while attempting to connect to wifi. Interestingly the restricted driver had been deactivated during the upgrade [I should have paid more attention to the proposed updates before clicking accept, but backports were NOT turned on].

Attempts to reactivate the restricted wifi driver as root did not stick (i.e. after reboot).

Several HARD RESETS later, I decided I would use this disaster as an opportunity to restore Win7 and upgrade my BIOS to B2.10-EC1.50-WIN.

Somewhere in all of this process my webcam has disappeared -- it doesn't appear under device manager on Win7 or with lsusb on linux. Running Cheese reports "no device found".

I tested toggling Webcam on/off in BIOS and this doesn't restore the device.

So... did I fry my own webcam with hard resets in Ubuntu; or is there a bug in the new BIOS which drops webcam support?

If it's the former... is there any dd magic to dump new firmware into a fried webcam?

(.... and it was all going so well  :-({|= )

**UPDATE:**
It's a hardware issue, the camera works when the lid is within two inches of being closed.

---

### Post by solnyshok on 2011-07-27
FYI, Bios was updated to 2.1 some time ago. I could not find changelog.

---

### Post by B-Town on 2011-08-17
Freezing when coming back from sleep.

I mentioned this before but but I am still having problems with ubuntu (or in my case kubuntu) completely freezing up when I come back from sleep mode.  This has only been an issue in 11.04 (not in 10.10 which is what I had previously).  I'm on a portege R705 and have updated the BIOS to the most recent (as of two weeks ago).

I've narrowed down some of the factors:
1) The compute must be unplugged (possibly it also is necessary that it went  to sleep unplugged as well though I'm not sure).
2) The wireless is on (this is always on so may be superfluous..but see below).
3) The computer is woken from sleep.

What happens is that:
1) The computer wakes up and shows the password screen
then either
2a) it freezes at the password screen
2b) it allows me to login and then freezes
2c) It allows me to login in and do a few things with some windows but other processes are frozen and then the whole system freezes.
3) I have to do a hard reboot.

I noticed today that my wireless was the first process to stop responding (firefox, krunner were all okay at first).  So that is why I think it might be related to the wireless.

Any one else have this issue?

Also I'm still mostly a novice at this so don't know where to look to see (log files for instance) what is causing the problem.  I don't want to submit a bug report as I don't have much idea where the problem is and it is fairly infrequent.

Thanks!

---

### Post by solnyshok on 2011-10-07
Hi, people

Anybody using Oneiric and solved brightness regulation problem?

In the Gnome2 there was very usefull Keyboard shortcut menu, where I could redefine Brightness keys with 
sudo toshset -bl on 
command. But in they unity shell, this setting panel changed, and changing Brightness key definitions there, doesn't help. hmmm, that is, brightness regulation works after suspend, but it jumps 2-3 notches with every BrightnessUp/Down keypress.

---

### Post by chris23 on 2011-10-17
> **solnyshok said:**
> Hi, people

Anybody using Oneiric and solved brightness regulation problem?

In the Gnome2 there was very usefull Keyboard shortcut menu, where I could redefine Brightness keys with 
sudo toshset -bl on 
command. But in they unity shell, this setting panel changed, and changing Brightness key definitions there, doesn't help. hmmm, that is, brightness regulation works after suspend, but it jumps 2-3 notches with every BrightnessUp/Down keypress.

How did you manage to get the brightness working when coming from sleep mode? or it was working by default?


@ALL
Is it me or 11.04 was faster and much more stable than Oneiric?

cheers

---

### Post by solnyshok on 2011-10-19
11/04 was faster to boot and sleep for sure. But I will stay in 11/10 because it has improved SMB networking speed. Previously, I could not get smooth playback of HD videos (4-8GB mkv) over wifi from windows shares. Now it works out of the box.

Brightness controls do not work after suspend on clean install.
You need to install toshset fix and define BrightnessUp and BrightnessDown keypress events to perform "sudo toshset -bl on"

---

### Post by chris23 on 2011-10-19
> **solnyshok said:**
> 11/04 was faster to boot and sleep for sure. But I will stay in 11/10 because it has improved SMB networking speed. Previously, I could not get smooth playback of HD videos (4-8GB mkv) over wifi from windows shares. Now it works out of the box.

Brightness controls do not work after suspend on clean install.
You need to install toshset fix and define BrightnessUp and BrightnessDown keypress events to perform "sudo toshset -bl on"

thanks for the feedback. Can you please give some tips on how to install toshset and define the events? does this works with the 11.10 kernel or it need downgrade?
thanks in advance :)

---

### Post by solnyshok on 2011-10-21
it works with 11/10. you need to add ppa 
[http://ppa.launchpad.net/keks9n/main/ubuntu](http://ppa.launchpad.net/keks9n/main/ubuntu)

then sudo apt-get update
sudo apt-get install toshiba-acpi-fix

solution for brightness control is on the first page of this thread.
what I do not like about it - is that brightness up/down commands seems to be issued several times in a row, and brightness level adjusts very sharply. therefore, I instead defined 8 key combinations (Alt+1...Alt+8) in the custom shortcuts (go to settings, keyboard, shortcuts, custom shortcuts) and assigned to each key following command

sudo toshset -inten X -bl on
where X is a value from 0 to 7, different for each key combination 
0 is darkest, 7 is brightest

---

### Post by chris23 on 2011-10-21
> **solnyshok said:**
> it works with 11/10. you need to add ppa 
[http://ppa.launchpad.net/keks9n/main/ubuntu](http://ppa.launchpad.net/keks9n/main/ubuntu)

then sudo apt-get update
sudo apt-get install toshiba-acpi-fix

solution for brightness control is on the first page of this thread.
what I do not like about it - is that brightness up/down commands seems to be issued several times in a row, and brightness level adjusts very sharply. therefore, I instead defined 8 key combinations (Alt+1...Alt+8) in the custom shortcuts (go to settings, keyboard, shortcuts, custom shortcuts) and assigned to each key following command

sudo toshset -inten X -bl on
where X is a value from 0 to 7, different for each key combination 
0 is darkest, 7 is brightest

Many thank for your time!
unfortunately, for my case nothing happen. Emmm, the thing you have described 'seems to be issued several times in a row' i have it even from a fresh start. After suspend, its just not working at all.
when i ran the sh file i got the below for output

```
./tosh-brn-up.sh: 6: DeviceConfig: not found
LCD backlight: on
```

any feedback welcome :)
--edit
running your commands thought..they seem to adjust the brightness just fine...

---

### Post by hotweiss on 2011-10-31
> **solnyshok said:**
> it works with 11/10. you need to add ppa 
[http://ppa.launchpad.net/keks9n/main/ubuntu](http://ppa.launchpad.net/keks9n/main/ubuntu)

then sudo apt-get update
sudo apt-get install toshiba-acpi-fix

solution for brightness control is on the first page of this thread.
what I do not like about it - is that brightness up/down commands seems to be issued several times in a row, and brightness level adjusts very sharply. therefore, I instead defined 8 key combinations (Alt+1...Alt+8) in the custom shortcuts (go to settings, keyboard, shortcuts, custom shortcuts) and assigned to each key following command

sudo toshset -inten X -bl on
where X is a value from 0 to 7, different for each key combination 
0 is darkest, 7 is brightest

Would you know how I could contact the person who maintains this ppa?

---

### Post by solnyshok on 2011-11-01
Try from here
[https://launchpad.net/~keks9n](https://launchpad.net/~keks9n)

---

### Post by de_Selby on 2011-11-05
> **solnyshok said:**
> it works with 11/10. you need to add ppa 
[http://ppa.launchpad.net/keks9n/main/ubuntu](http://ppa.launchpad.net/keks9n/main/ubuntu)

then sudo apt-get update
sudo apt-get install toshiba-acpi-fix

solution for brightness control is on the first page of this thread.
what I do not like about it - is that brightness up/down commands seems to be issued several times in a row, and brightness level adjusts very sharply. therefore, I instead defined 8 key combinations (Alt+1...Alt+8) in the custom shortcuts (go to settings, keyboard, shortcuts, custom shortcuts) and assigned to each key following command

sudo toshset -inten X -bl on
where X is a value from 0 to 7, different for each key combination 
0 is darkest, 7 is brightest

I made 2 scripts, one to increase brightness and one to decrease

bri_inc.sh

```
#!/bin/bash

CBRI=`toshset -inten |awk '{print $3}'|cut -f1 -d/`

if [ $CBRI = 7 ]
then
        CBRI=6
fi

toshset -inten `echo $CBRI | awk '{print $1+1}'` -bl on
```


bri_dec.sh

```
#!/bin/bash

CBRI=`toshset -inten |awk '{print $3}'|cut -f1 -d/`

if [ $CBRI = 0 ]
then
        CBRI=1
fi

toshset -inten `echo $CBRI | awk '{print $1-1}'` -bl on
```


You also need to allow read/write access to the toshiba device in dev for this to work

```
sudo chmod a+rw /dev/toshiba
```

Then you can assign the increase and decrease scripts to the Fn + F6/F7 keys.

---

### Post by archish on 2011-11-13
> **connect404 said:**
> 
[SIZE=2][COLOR=Green]Video
[/COLOR][/SIZE]
[LIST]
[*]Intel video card is fully supported.
[*]Compiz is on by default and all desktop effects work great
[*]Full SD (720p) playback works 100%
[*]VGA & HDMI outputs are recognized
[*]VGA & HDMI outputs can be configured as secondary or mirrored devices and detect/display correctly.
[*]Have had this plugged into both a TV and LCD monitor and everything works flawlessly.
[/LIST]


I have just installed 10.04.3 on my Portege R700. It came with Win7 preinstalled. For connecting to my LCD TV in windows I was pressing the Fn+F5 twice to change the output to TV only. This enabled me to get full 1080p output for movies/desktop. Now how do I get the TV only output, I tried playing around it was either mirrored or secondary.

Any pointers as how to get only secondary device as output in full 1080p mode?

---

### Post by solnyshok on 2011-11-14
Hi, I think I now figured out why my laptop was downscaling to 1/4 of normal speed in Windows, but only to 1/2 in Linux. Yesterday, I installed ThrottleStop under Windows, and found, that Toshiba applied 50% throttling to CPU modulation. When I chose to remove throttling, CPU became hotter, but still within thermal limits, and twice faster. I have i450m. So, for one year, whenever Windows reported speed of 2.4-2.6GHz, CPU was running 1.2-1.3 in reality. 

Removing throttling did nothing to change Windows Experience score, but (builtin) benchmark time went down from 70 sec to 35 seconds. Thermals stayed within 4-5 degrees from max during this period. Usually there is no program (other than stress testing benchmark) that could load 100% all 4 cores for 30 seconds, so I decided to adopt throttling free profile, while on AC. Laptop is much speedier now, and fan kicks in only a bit quicker than before. On the other hand, while on battery, it is possible to set Cmod even lower than Toshiba's 50% (say 25%) to achieve longer battery life. 

Now, this is situation in Windows7, does anybody know about CPU clock throttling control for Linux?

---

### Post by solnyshok on 2011-11-14
@de_Selby those scripts unfortunately did not change that erratic brightness changing behaviour. I tested them in bash, they seem to correctly identify current LCD intensity, but brightness still changed 2-3 notches up/down. Seems that one keypress is processed by several hooks (apci, keybindings, etc. I do not really know). I removed scripts I had installed before, and removed bindings in the keyboard settings, but it did not help.

---

### Post by de_Selby on 2011-11-15
What happens if you just run bri_inc.sh and bri_dec.sh from a terminal? 

They're just executing the "toshset -inten X -bl on" so I can't see how it would change by more than one level.

---

### Post by chris23 on 2011-11-18
> **de_Selby said:**
> I made 2 scripts, one to increase brightness and one to decrease

bri_inc.sh

```
#!/bin/bash

CBRI=`toshset -inten |awk '{print $3}'|cut -f1 -d/`

if [ $CBRI = 7 ]
then
        CBRI=6
fi


toshset -inten `echo $CBRI | awk '{print $1+1}'` -bl on
```


bri_dec.sh

```
#!/bin/bash

CBRI=`toshset -inten |awk '{print $3}'|cut -f1 -d/`

if [ $CBRI = 0 ]
then
        CBRI=1
fi

toshset -inten `echo $CBRI | awk '{print $1-1}'` -bl on
```


You also need to allow read/write access to the toshiba device in dev for this to work

```
sudo chmod a+rw /dev/toshiba
```

Then you can assign the increase and decrease scripts to the Fn + F6/F7 keys.


thanks man! just what i needed. they work perfeclty!
thanks again for sharing!
---
edit

I manage to assign the script to ctrl+f6 rather than Fn+f6...it seems than Fn+f6 cannot be overriden ...any feedback on that?

---

### Post by de_Selby on 2011-11-19
Well it depends what tool you're using to modify the key bindings - I'm using xmonad so I just edited the config file for that, but the key codes etc that you need can be gotten from running xev and then pressing the keys. Here's the info for the two keys:

```
KeyPress event, serial 45, synthetic NO, window 0x2600001,
    root 0xae, subw 0x0, time 159378154, (680,451), root:(681,468),
    state 0x0, keycode 232 (keysym 0x1008ff03, XF86MonBrightnessDown), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x2600001,
    root 0xae, subw 0x0, time 159319468, (569,290), root:(570,307),
    state 0x0, keycode 233 (keysym 0x1008ff02, XF86MonBrightnessUp), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```

The key bits there are the keycodes (232 and 233) the keysyms (0x1008ff03 and 0x1008ff02) and the names (XF86MonBrightnessDown and XF86MonBrightnessUp).

I'm not sure what config file you should edit for gnome or whatever you're using though.

---

### Post by chris23 on 2011-11-21
> **de_Selby said:**
> Well it depends what tool you're using to modify the key bindings - I'm using xmonad so I just edited the config file for that, but the key codes etc that you need can be gotten from running xev and then pressing the keys. Here's the info for the two keys:

```
KeyPress event, serial 45, synthetic NO, window 0x2600001,
    root 0xae, subw 0x0, time 159378154, (680,451), root:(681,468),
    state 0x0, keycode 232 (keysym 0x1008ff03, XF86MonBrightnessDown), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x2600001,
    root 0xae, subw 0x0, time 159319468, (569,290), root:(570,307),
    state 0x0, keycode 233 (keysym 0x1008ff02, XF86MonBrightnessUp), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```

The key bits there are the keycodes (232 and 233) the keysyms (0x1008ff03 and 0x1008ff02) and the names (XF86MonBrightnessDown and XF86MonBrightnessUp).

I'm not sure what config file you should edit for gnome or whatever you're using though.

thanks for your feedback. One more question, after assigning the scripts to the keys, do you still get the progress bar of the brightness?

---

### Post by and.hunt on 2012-01-04
> **B-Town said:**
> Freezing when coming back from sleep.

I mentioned this before but but I am still having problems with ubuntu (or in my case kubuntu) completely freezing up when I come back from sleep mode.  This has only been an issue in 11.04 (not in 10.10 which is what I had previously).  I'm on a portege R705 and have updated the BIOS to the most recent (as of two weeks ago).

I've narrowed down some of the factors:
1) The compute must be unplugged (possibly it also is necessary that it went  to sleep unplugged as well though I'm not sure).
2) The wireless is on (this is always on so may be superfluous..but see below).
3) The computer is woken from sleep.

What happens is that:
1) The computer wakes up and shows the password screen
then either
2a) it freezes at the password screen
2b) it allows me to login and then freezes
2c) It allows me to login in and do a few things with some windows but other processes are frozen and then the whole system freezes.
3) I have to do a hard reboot.

I noticed today that my wireless was the first process to stop responding (firefox, krunner were all okay at first).  So that is why I think it might be related to the wireless.

Any one else have this issue?

Also I'm still mostly a novice at this so don't know where to look to see (log files for instance) what is causing the problem.  I don't want to submit a bug report as I don't have much idea where the problem is and it is fairly infrequent.

Thanks!

I have similar issues -- using an older kernel (2.6.32.x)  which was still installed from a previous ubuntu version worked for me, but messed up graphics drivers, and sine I need 3d I had to use the newer kernel. I'm currently trying to do a more detailed analysis of what is happening -- usually the computer freezes even before the login screen, sometimes I just get a random freeze in the middle of using the computer. I'm also on 11.04, but will try to upgrade to 11.10 sometime to see if that improves things (but at the moment I don't have the time to deal with the potential side issues of such an update...).

---

### Post by Dan.S.Lee.10 on 2012-01-23
I own an R705-P25, and right now have only UBUNTU 11.10 installed.  I am trying to install LINUXMINT12 through a LiveCD.  But when I enter the BIOS after holding F12, and try to change the boot order, I'm unable to. Any key I press just causes the BIOS boot order screen to just blink.  I believe the BIOS is at v1.5 right now. Is there an alternative way to install a different distro? Or do I need to update the BIOS?(I've seen the FreeDOS method but I think it calls for me being able to boot from USB, which I can't seem to do). Any suggestions? 

-LinuxBeginner-

---

### Post by chris23 on 2012-02-22
Does anybody figure out how to get sound through the hdmi to tv?
Or is it working br default for you?

---

### Post by bakinsoda on 2012-02-22
It should work if you go to the sound option (icon on top right)...sound preferences.  Go to Hardware > profile dropdown > select HDMI.  It's one of those options.

---

### Post by chris23 on 2012-02-23
> **bakinsoda said:**
> It should work if you go to the sound option (icon on top right)...sound preferences.  Go to Hardware > profile dropdown > select HDMI.  It's one of those options.

Ive tried that. no hdmi sound though.

---

### Post by chris23 on 2012-05-12
upgrading to 12.10 seems to solve the brightness problem. but it doesnt work at all when resuming from hibernation...any idea?

---


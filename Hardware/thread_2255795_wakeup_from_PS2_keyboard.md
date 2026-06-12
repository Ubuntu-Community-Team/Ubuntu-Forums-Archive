---
title: "wakeup from PS/2 keyboard"
date: 2014-12-07
forum: Hardware
---

### Post by pi3guy on 2014-12-07
[SIZE=2][FONT=arial]Hello everyone,

Running 14.04. I am trying to allow wake up from suspend by pressing any keyboard button. Right now, I can only resume by pressing the power button on my desktop. I have a dual boot, and this works in Windows so I don't think I need to change any BIOS setting. I have already done some searching but haven't yet found a solution. If I run 

cat /proc/acpi/wakeup

it shows: PS2K      S4    *disabled

[/FONT][/SIZE][SIZE=2][FONT=arial]I then try to run

sudo su
echo PS2K > /proc/acpi/wakeup

No error messages, but PS2K still shows up as disabled the next time I run [/FONT][/SIZE][FONT=arial]cat /proc/acpi/wakeup[/FONT][SIZE=2][FONT=arial]

I also tried without luck:
[COLOR=#000000][SIZE=2]echo KBC0 > /proc/acpi/wakeup 
[/SIZE]
as advised in this thread 
[/COLOR][/FONT][/SIZE]http://ubuntuforums.org/showthread.php?t=991593
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]
My system:
14.04 64-bit on a custom desktop. 
motherboard: ASUS h97 m-itx 
gfx driver: nvidia-343 from edgers. 
Gnome-compiz

Your help is greatly appreciated
[/FONT][/SIZE]

---

### Post by tgalati4 on 2014-12-07
Open a terminal, install *acpitool* and post:

```
sudo apt-get install acpitool
acpitool -w
```

You can turn parts of the power bus on using -W switch.

You could also set "Allow USB devices to wake" in BIOS and wiggle your USB mouse.  That works in some cases--but won't work with only ps/2 devices.

You might need to modify a script in /etc/acpi.  Add the keycode that you want to trigger the resume event.  It takes some trial-and-error.

Some BIOS have a programmable key for wakeup.  I set mine to "p" on one desktop to wake up.  On another desktop, any key will wake, and yet another only the "wake" key will wake up the computer.

---

### Post by pi3guy on 2014-12-08
Thanks for your reply. I don't think acpitool fixed my problem though
running acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. PEG0	  S4	*disabled  pci:0000:00:01.0
  2. PEGP	  S4	*disabled  pci:0000:01:00.0
  3. PEG1	  S4	*disabled
  4. PEGP	  S4	*disabled
  5. PEG2	  S4	*disabled
  6. PEGP	  S4	*disabled
  7. PS2K	  S4	*disabled
  8. GLAN	  S4	*enabled   pci:0000:00:19.0
  9. EHC1	  S4	*enabled   pci:0000:00:1d.0
  10. EHC2	  S4	*enabled   pci:0000:00:1a.0
  11. XHC	  S4	*enabled   pci:0000:00:14.0
  12. HDEF	  S4	*disabled  pci:0000:00:1b.0

running sudo su
then acpitool -W 7
  Changed status for wakeup device #7 (PS2K)


   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. PEG0	  S4	*disabled  pci:0000:00:01.0
  2. PEGP	  S4	*disabled  pci:0000:01:00.0
  3. PEG1	  S4	*disabled
  4. PEGP	  S4	*disabled
  5. PEG2	  S4	*disabled
  6. PEGP	  S4	*disabled
  7. PS2K	  S4	*disabled
  8. GLAN	  S4	*enabled   pci:0000:00:19.0
  9. EHC1	  S4	*enabled   pci:0000:00:1d.0
  10. EHC2	  S4	*enabled   pci:0000:00:1a.0
  11. XHC	  S4	*enabled   pci:0000:00:14.0
  12. HDEF	  S4	*disabled  pci:0000:00:1b.0

Do you mean edit an existing script in /etc/acpi or create a new one?

---

### Post by tgalati4 on 2014-12-08
*acpitool* generally only lets you enable/disable parts of the pci bus.  It's helpful to keep the network card awake during sleep so you can use Wake-on-Lan.  The PS/2 is part of the serial bus and is controlled by BIOS.  

For modifying /etc/acpi/events, you typically browse through the "event" scripts and find one that is similar to what you are trying to do.  Modify it and see what the effect is.  You would have to research what the event triggers are for ASUS.  For instance, this is a desktop computer, but if you have a "lid" button, then you could assign a hotkey to that "lid" button to give similar sleep/wake behavior of a laptop lid.

Examine what devices are defined on your system:

```
cat /proc/bus/input/devices
```

> tgalati4@Mint14-Extensa /proc/bus/input $ cat devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

.
.
.

tgalati4@Mint14-Extensa /proc/acpi/button/lid/LID0 $ cat state
state:      open



You would write a script to echo the state value and assign it to a hotkey using the "Keyboard Shortcuts" GUI.  Assign one key to "sleep" typically the "sleep" button on an extended keyboard, and one key to "wake", either the "wake" key if you have one, or Control-Shift-P to represent "Power On".

Try a newer USB keyboard that has a sleep and wake key.  It might work out of the box.

---


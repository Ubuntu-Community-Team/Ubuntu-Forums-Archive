---
title: "USB drives switch off after a while"
date: 2021-04-05
forum: Hardware
---

### Post by phile-mitti99 on 2021-04-05
[FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][COLOR=#050505][FONT=Helvetica]Hello Ubuntu community. 

I recently switched to Ubuntu, but I have a bit of a problem. After a while, the USB drives switch off, and the kammara is no longer available either. T[/FONT][/COLOR][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]hat happens after a different amount of time, sometimes after 5 minutes and sometimes after a few hours after I have activated it[FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][COLOR=#050505][FONT=Helvetica]. I looked it up on the internet, but I have not found a case where this problem occurred. Are there some settings to solve this? Does anyone have any idea?
[/FONT][/COLOR][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]when I restart the laptop everything works for a while.[FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][COLOR=#050505][FONT=Helvetica]
I have a Lenovo E15 laptop.

[/FONT][/COLOR][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]
[/FONT][/FONT]
I wrote lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:0029 Intel Corp. 
Bus 003 Device 002: ID 06cb:00da Synaptics, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

This is how it looks when the USB drives are switched off. When these are switched on, other devices appear.


Certain folders do not appear in the path /sys/bus/usb/devices either.
1-0:1.0  3-0:1.0  3-3:1.0  3-4:1.0  4-0:1.0  usb2  usb4
2-0:1.0  3-3      3-4      3-4:1.1  usb1     usb3



I have set /sys/bus/usb/devices/1-1/power/autosuspend to '-1'
and /sys/bus/usb/devices/1-1/power/level to 'on'
also /sys/bus/usb/devices/1-1/power/control to 'on'
but these switch off anyway.

---

### Post by TheFu on 2021-04-05
Maybe **hdparm** can tell the drives to never spin down?  Not all drive firmware and controllers support that, however.  
What happens on a non-laptop?  
Are the drives powered separately from the USB connection?  I'd guess the laptop is going into power-saving mode if there.  Try to power external spinning drives from dedicated plug power, not USB.

---

### Post by phile-mitti99 on 2021-04-05
It does not depend on the battery level. I'm still not sure, how could you find out?

---

### Post by TheFu on 2021-04-05
> **phile-mitti99 said:**
> It does not depend on the battery level. I'm still not sure, how could you find out?

Laptops behave differently when on wall power and battery.
External storage should always be plugged into wall power for best performance and to prevent spinning down - not get power from the laptop.
I don't know how to say this clearer.

---

### Post by phile-mitti99 on 2021-04-05
do you happen to know some commands to reduce power consumption?

---

### Post by TheFu on 2021-04-05
> **phile-mitti99 said:**
> do you happen to know some commands to reduce power consumption?

hdparm has some options.  The manpage for hdparm spells those out. Access it with **man hdparm** or use **xman**.  Whenever doing things like this, it is critical to read the manpage for the commands.  May want to search all manpages for "power" .... **apropos power** will search the command summaries in all manpages. That's very helpful when you don't know where to start, plus the manpages on you system ARE FOR the command versions ON YOUR SYSTEM, unlike google.

If you want to reduce power use, unplug devices, turn down the screen brightness, and most importantly - PLUG IN ALL THE DEVICES TO THE WALL for power.  You seem to ignore that statement. Perhaps you've already done everything suggested, but if you don't tell us what you are doing, how can we know?

---

### Post by mat-jonczyk on 2021-04-06
Hello,

I think that you may have better luck with smartctl then with hdparm.

You can install it with
[B]sudo apt install smartmonotools
sudo update-smart-drivedb
[/B]
Then you can view a list of drives with
**sudo smartctl --scan**

and view device info with
**sudo smartctl --xall /dev/sdb**

(replace **/dev/sdb** with the drive name from smartctl --scan).

You can try disabling spinoff with
**sudo smartctl --set=apm,off /dev/sdb**
or
**sudo smartctl --set=apm,254 /dev/sdb**
(only one of them may do the trick).

That said, I have two external hard drives from TOSHIBA, that turn off after some inactivity time no matter what I do. There simply is no way I have found to make them stop doing so. In the past, I have used a small shell script to periodically poll them and keep them awake.

Edit: in case of these two TOSHIBA hard drives: the drives spin down after inactivity, but still are reachable. If they are accessed again, they simply spin up. The drives you describe seem to be inaccessible after spindown.

> When these are switched on, other devices appear.
Please provide output of **lsusb** with these drives switched on.

Edit: please also provide model name and number of these drives.

---

### Post by phile-mitti99 on 2021-04-06
Hey,

I can try these commands,
but when I do 'sudo smartctl --xall / dev / sdb'enter see' this directory was not found '.

---

### Post by mat-jonczyk on 2021-04-06
There should be no spaces around the slash marks: "**/**"

sudo smartctl --xall /dev/sdb

not:

sudo smartctl --xall / dev / sdb

---

### Post by phile-mitti99 on 2021-04-06
[ATTACH=CONFIG]288226[/ATTACH]
There is no space between the '/'. Shoud I create this folder?

---

### Post by mat-jonczyk on 2021-04-06
> should I create this folder?

No. Execute

**sudo smartctl --xall /dev/sdb**

while these drives are connected and accessible.

Do the problems disappear after you plug out and then plug in these drives? Do you need to restart the laptop to use these drives again?

---

### Post by phile-mitti99 on 2021-04-06
When I unplug the devices and plug them back in, they don't work. Only after rebooting the laptop are the drives available again

---

### Post by TheFu on 2021-04-06
> **phile-mitti99 said:**
> Hey,

I can try these commands,
but when I do 'sudo smartctl --xall / dev / sdb'enter see' this directory was not found '.

Please learn to use **_command completion_** or _**tab completion**_ in the shell.  It is easy and will prevent ever getting the wrong file or directory name again. Forever.  Look for a youtube video on it - since it is easy to explain in a video, but hard to explain clearly in text.  10 seconds and you are a master.
Basically, if you are typing more than 2-3 characters at a time, then you are doing it wrong.

I didn't look at anything other than the /dev/sd {whatever} part.

For more shell efficiencies: [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)
Don't worry about knowing or understanding all of them. Skim everything and use what makes sense.  Every 3-6 months (set a calendar entry), come back and re-skim it again. More things will make sense and you'll be more efficient.  I'm more efficient with a shell in a terminal than using a mouse for almost everything. My brain thinks in a specific way to minimize typing, but still do what I want.  File/directory "globbing" is very powerful.  But some commands, like smartctl won't use globbed filenames that expand into more than 1 input at a time.

---

### Post by TheFu on 2021-04-06
And for commands you don't know, please, please, please, review the manpage for it.  Every command on Unix-like systems has a manual page which explains all the options and inputs and outputs and how those can be formatted. There are caveats for when it doesn't work as expected and perhaps pitfalls.  Administrator commands like hdparm and smartctl each have manpages that need to be read to ensure we don't do damage.

---

### Post by phile-mitti99 on 2021-04-06
For me there is no directory with /etc/sdb. I can write /etc/s and press tab, but it doesn't suggest the file sdb and when I enter /etc/sdb an error occurs because I don't have this file.


[B]Smartctl open device: /dev/sdb failed: No such device
[/B]
Does this file not exist because of my errors because of the USB?

---

### Post by TheFu on 2021-04-06
> **phile-mitti99 said:**
> For me there is no directory with /etc/sdb. I can write /etc/s and press tab, but it doesn't suggest the file sdb and when I enter /etc/sdb an error occurs because I don't have this file.


[B]Smartctl open device: /dev/sdb failed: No such device
[/B]
Does this file not exist because of my errors because of the USB?

Well, /etc/ is wrong.  Disk storage device files are under /dev/.  And just to be clear - I've made exactly the same mistake, but I know when tab-completion "bonks" at me, it means the file doesn't exist, so I need to re-check my inputs.  Also, each tool should come with a bash-completion update so ensure different inputs that are order-specific as options cannot be entered in the wrong order.

---

### Post by mat-jonczyk on 2021-04-06
> When I unplug the devices and plug them back in, they don't work.  Only after rebooting the laptop are the drives available again


This is strange. Could you provide the kernel log from this laptop? It could be obtained by typing "dmesg" in the terminal. Do:
```
dmesg > dmesg_2020-04-06.txt
```
This will cause the output of the **dmesg** command to be stored in a file called "dmesg_2020-04-06.txt". The ">" char instructs a redirection.

Please provide the kernel log after all the following: the drive stops working,  you plug it out and then in. 
This file can be attached  in advanced editor on this forum - there is an icon in the top row.

---

### Post by TheFu on 2021-04-06
```
dmesg -w
```
will show the "tail" of the file, in real-time.
If you want to save it to a file, use 
```
$ dmesg -w | tee /tmp/log.dmesg

[884072.532135] usb 2-3: USB [COLOR="#FF0000"]disconnect[/COLOR], device number 5
[884078.957120] usb 2-3: [COLOR="#008000"]new SuperSpeed Gen 1 USB device number 6 using xhci_hcd[/COLOR]
[884078.984199] usb 2-3: New USB device found, idVendor=11b0, idProduct=3307, bcdDevice=0.13
[884078.984203] usb 2-3: New USB device strings: Mfr=3, Product=4, SerialNumber=2
[884078.984205] usb 2-3: Product: UHSII uSD Reader
[884078.984207] usb 2-3: Manufacturer: Kingston
[884078.984209] usb 2-3: SerialNumber: 000000000013
[884078.991763] usb-storage 2-3:1.0: USB Mass Storage device detected
[884078.991936] scsi host16: usb-storage 2-3:1.0
[884080.002716] scsi 16:0:0:0: Direct-Access     Kingston UHSII uSD Reader 0013 PQ: 0 ANSI: 6
[884080.003249] sd 16:0:0:0: Attached scsi generic sg2 type 0
[884080.394000] sd 16:0:0:0: [sdc] Spinning up disk...
[884081.408185] .ready
[884081.770634] sd 16:0:0:0: [sdc] 15954944 512-byte logical blocks: (8.17 GB/7.61 GiB)
[884081.771436] sd 16:0:0:0: [sdc] Write Protect is off
[884081.771438] sd 16:0:0:0: [sdc] Mode Sense: 21 00 00 00
[884081.772213] sd 16:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[884081.804506]  sdc: sdc1
[884081.807440] sd 16:0:0:0: [sdc] Attached SCSI removable disk
[884089.400357] usb 2-3: USB [COLOR="#FF0000"]disconnect[/COLOR], device number 6
```

That example shows a USB3 converter with a microSD being removed, inserted and removed.
The log.dmesg will have much more of dmesg output than we expect. Jump to the bottom, but in the terminal, just the last few lines are displayed.

---

### Post by phile-mitti99 on 2021-04-06
```
[  946.626629] usb 2-2: USB disconnect, device number 2
[  953.368668] usb 2-2: new SuperSpeed Gen 1 USB device number 3 using xhci_hcd[  953.390642] usb 2-2: New USB device found, idVendor=0480, idProduct=0900, bcdDevice= 3.15
[  953.390646] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  953.390648] usb 2-2: Product: External USB 3.0
[  953.390650] usb 2-2: Manufacturer: TOSHIBA
[  953.390651] usb 2-2: SerialNumber: 20200824007277F
[  953.391697] usb-storage 2-2:1.0: USB Mass Storage device detected

```

if my USB works it is as it should be. if the USB drives turn off I can do that again and send a piece of CODE.

---

### Post by phile-mitti99 on 2021-04-06
My USB drives have switched off and I have written **dmesg -w,** when I unplug a device it does not log anything

---

### Post by TheFu on 2021-04-06
> **phile-mitti99 said:**
> My USB drives have switched off and I have written **dmesg -w,** when I unplug a device it does not log anything

If there isn't any power, how can they tell the OS anything? 
If the monitor is switched off, do you expect the computer to know when it is connected and disconnected?

---

### Post by mat-jonczyk on 2021-04-06
> **phile-mitti99 said:**
> My USB drives have switched off and I have written **dmesg -w,** when I unplug a device it does not log anything

Please post  whole output of dmesg - logs from the beginning, from the time the computer was started.

I suspect it may be a problem with the hardware itself, like worn out USB ports or cables.

---

### Post by phile-mitti99 on 2021-04-07
[ATTACH]288229[/ATTACH]

I compressed the file in a ZIP, otherwise the file was too big. In the last area, the USB drive switched off.

---

### Post by TheFu on 2021-04-07
> **phile-mitti99 said:**
> [ATTACH]288229[/ATTACH]

I compressed the file in a ZIP, otherwise the file was too big. In the last area, the USB drive switched off.

If the drive disconnects while it is being used, that's a physical problem. Could be the port on the computer, USB cable, port on the external disk, the USB controller could have a short, or the disk could be failing.

Or is the external power supply having a short?  I don't recall an answer for whether any external power is supplied to the USB external disk. Is it?

---

### Post by phile-mitti99 on 2021-04-07
My hard drive is only supplied with power from the USB port. I noticed, however, that when the laptop is connected to the power supply, the USB drives turn off. This happens for different lengths of time, but it also seems to me that when I run two virtual machines and use the mouse, the USB drives switch off. I think this switches off when there is high power consumption.

---

### Post by TheFu on 2021-04-07
> **phile-mitti99 said:**
> My hard drive is only supplied with power from the USB port. I noticed, however, that when the laptop is connected to the power supply, the USB drives turn off. This happens for different lengths of time, but it also seems to me that when I run two virtual machines and use the mouse, the USB drives switch off. I think this switches off when there is high power consumption.

I don't think there is a fix possible for that drive. Be careful to purchase externally powered drives in the future.
These days, for VM storage, I'd strongly consider an external SSD assuming usb3 connectivity. That would remove the external power requirement too.

---

### Post by phile-mitti99 on 2021-04-07
I'm still a student at a technical school and I learn about computer science, at least I have learned and have a document from the hard drive open. I have this document open for about 11 hours and I believe that the hard drive has not gone into standby mode. The USB drives also run for these 11 hours. But when the hard drive is in standby mode and I used the mouse, the USB drives switch off. Can it also be due to the hardware?

---

### Post by phile-mitti99 on 2021-04-08
I entered **lsusb -vv **and analyzed the power consumption of each device

Hard drive = MaxPower: 900mA
Camera = MaxPower: 500mA
USB-Stick = MaxPower: 500mA
Mouse = MaxPower: 100mA

The hard drive consumes a lot of power, so i'm trying to switch to a stick because it needs less power. If the problem no longer occurs, I'll let you know.

---


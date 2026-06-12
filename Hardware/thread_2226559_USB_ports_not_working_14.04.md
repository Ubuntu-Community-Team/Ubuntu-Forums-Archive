---
title: "USB ports not working 14.04"
date: 2014-05-27
forum: Hardware
---

### Post by norris-alan on 2014-05-27
Hello, 

This is my first post so thank you in advance and I apologize for any poor etiquette.

I upgraded to 14.04 on Friday and my usb ports were working fine. I fell asleep last night with my phone hooked up with a charge key and my computer lost power during the night. I am afraid I may have ruined my hardware. I have searched for a few hours threads similar to mine. Many were helpful but so far I have had no results in getting my usb ports to work again.

From other threads, here is some info I see commonly asked for:

lsusb:
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lspci for hardware info:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Qualcomm Atheros AR8152 v1.1 Fast Ethernet (rev c1)
03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


I have also attached a dmesg file to my post.

I am worried I have fried my hardware and more than anything I am curious if someone could help me determine if this is a hardware or software issue.

Here are a few various things I have tried to tests my ports as well:

I have restarted my computer. Also have shut down and removed battery for several minutes.

I checked my bios for any usb related options. One option was a "legacy" option, which I have tried to boot and test ports with this feature on and off, neither worked. Also chose a "default" / "optimum" settings from bios and rebooted, neither worked.

I have another hard drive from two years ago with windows seven. I popped the old drive in and booted from windows, ports still weren't working. 


What is a good next step in trouble shooting or what additional info should I look at/ what am I missing from info I have?

Thank you.

---

### Post by matt_symes on 2014-05-28
Hi

I suspect software.

Try booting into a livecd/usb from the bios.

Do you have one of the above ?

I'll have a look at your dmeg output.

Kind regards

---

### Post by norris-alan on 2014-05-28
Hi Matt,

Thanks for the suggestion. I booted to a livecd and still had no luck with my usb ports... But now I have another trick for the future ;)

---

### Post by matt_symes on 2014-05-29
Hi

> I booted to a livecd and still had no luck with my usb ports...

That does not bode too well. 

Boot into the BIOS and reset the BIOS to any "failsafe defaults" it may have or at least take a look to see nothing is arry with your settings.

I'm looking at your dmseg now as was not able to before.

Kind regards

---

### Post by matt_symes on 2014-05-29
Hi

```

<snip>
[    4.053443] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.053481] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000050e0
[    4.053535] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    4.053537] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.053539] usb usb3: Product: UHCI Host Controller
[    4.053541] usb usb3: Manufacturer: Linux 3.13.0-27-generic uhci_hcd
[    4.053543] usb usb3: SerialNumber: 0000:00:1a.0
[    4.053644] hub 3-0:1.0: USB hub found
[    4.053652] hub 3-0:1.0: 2 ports detected
[    4.053926] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.053934] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.053972] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000050c0
[    4.054017] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    4.054020] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
<snip>
```

After looking at your mesg output, it look likes your hubs are being recognised, and drivers being loaded for them. That was kind of implied by the output from your first post.

I also looks like at least some devices are being recognised
```

[18968.784061] usb 1-3: new high-speed USB device number 2 using ehci-pci
[18969.030747] atl1c 0000:02:00.0: irq 46 for MSI/MSI-X
[18969.045001] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[18969.103935] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[18969.172187] usb 1-3: New USB device found, idVendor=0bda, idProduct=0138
[18969.172191] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[18969.172194] usb 1-3: Product: USB2.0-CRW
[18969.172196] usb 1-3: Manufacturer: Generic
[18969.172198] usb 1-3: SerialNumber: 20090516388200000
[18970.075526] usbcore: registered new interface driver usb-storage
[18970.127936] ums-realtek 1-3:1.0: USB Mass Storage device detected
[18970.149598] usb 1-3: USB disconnect, device number 2
[18970.157963] scsi6 : usb-storage 1-3:1.0
[18970.158470] usbcore: registered new interface driver ums-realtek
```

So can we try to narrow down exactly what is not being recognised.

Can you specifiy that exact hardware that is not being recoginsed please and what exactly are you expecting to see when you pug this device in ?

Also, can you open a terminal and type

```
sudo dmesg -c
```

Plug in the device into the USB port wait for 30 seconds and then type

```
dmesg
```

and post that final output back here.

The problem may be higher up.

Kind regards

---

### Post by norris-alan on 2014-05-31
Having an odd reaction today. I booted my computer and plugged in my Logitech USB keyboard and mouse combo (Logitech K260) and it was working once gain. After a few minutes, it suddenly stopped. 
 
Here is the output when I run sudo dmesg -c, then dmesg with the keyboard and mouse working:

```
[  128.956028] usb 6-1: new full-speed USB device number 2 using uhci_hcd[  129.138747] usb 6-1: New USB device found, idVendor=046d, idProduct=c52e
[  129.138752] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  129.138754] usb 6-1: Product: USB Receiver
[  129.138756] usb 6-1: Manufacturer: Logitech
[  129.329309] hidraw: raw HID events driver (C) Jiri Kosina
[  129.380276] usbcore: registered new interface driver usbhid
[  129.380281] usbhid: USB HID core driver
[  129.408095] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input8
[  129.421081] hid-generic 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[  129.450565] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input9
[  129.482082] hid-generic 0003:046D:C52E.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
```

Once the mouse and keyboard stop working after a few minutes, I ran dmesg again and got these results:

```
[  128.956028] usb 6-1: new full-speed USB device number 2 using uhci_hcd[  129.138747] usb 6-1: New USB device found, idVendor=046d, idProduct=c52e
[  129.138752] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  129.138754] usb 6-1: Product: USB Receiver
[  129.138756] usb 6-1: Manufacturer: Logitech
[  129.329309] hidraw: raw HID events driver (C) Jiri Kosina
[  129.380276] usbcore: registered new interface driver usbhid
[  129.380281] usbhid: USB HID core driver
[  129.408095] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input8
[  129.421081] hid-generic 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[  129.450565] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input9
[  129.482082] hid-generic 0003:046D:C52E.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[  323.407038] perf samples too long (2514 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  405.896082] usb 6-1: USB disconnect, device number 2

```

Although I received the "USB disconnect, device number 2" I had not removed the receiver for the keyboard / mouse

Is it possible the usb disconnect is due to:
[  323.407038] perf samples too long (2514 > 2500), lowering kernel.perf_event_max_sample_rate to 50000



Some info on my BIOS:
When the Logitech keyboard and mouse were working the first instance today, I had a "usb legacy emulator" option from my BIOS enabled. After the mouse and key board stopped working I disabled the option and after a few reboots, the mouse and keyboard worked again for a few minutes before dying out. I was able to use the usb ports with the option both off and on, so I am not sure if it has any effect. Also ran with a "restore to default" settings option, which my usb ports had worked on fine up to last week.

I know now at least the ports will work... somewhat... 



Side note, while messing around with everything I also saw this in my dmesg at one point, not sure if related:

```
[  107.492950] systemd-hostnamed[2439]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```



Thank you

---

### Post by norris-alan on 2014-05-31
Also, if this helps, when I have nothing in the usb port, stick the logitech  stick in and wait 30 seconds (as you asked me to try in your post) I get no new info in my dmesg output. :confused:
I also have tried several different items in my ports: multiple pensticks, phone chargers and a few other devices. no devices will work regularly although when the usb stick for the logitech was working the first time, my phone would pull charge and connect to the second usb port. I just am focusing on the Logitech as I have output of it working and not working.

---

### Post by jeremy31 on 2014-06-01
> **norris-alan said:**
> 
Side note, while messing around with everything I also saw this in my dmesg at one point, not sure if related:

```
[  107.492950] systemd-hostnamed[2439]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```



Thank you

This is not related, unfortunately. But it can be fixed with ```
sudo apt-get install libnss-myhostname
```

---

### Post by matt_symes on 2014-06-01
Hi

I wonder if it's your USB ports or the USB hub is auto-suspending due to power management.

What's the output of 

```
cat /sys/bus/usb/devices/usb*/power/control
```

and do you still get the same problem if you run this just after booting the machine ?

```
echo "on" | sudo tee /sys/bus/usb/devices/usb*/power/control
```

It is not persistent between machine reboots.

You can also check with powertop if you prefer something slightly more user friendly.

```
sudo apt-get install powertop
```

Look on the tunables tab.  If it's set to bad then auto-suspend is disabled and this is what you want.

Kind regards

---

### Post by norris-alan on 2014-06-01
> **jeremy31 said:**
> This is not related, unfortunately. But it can be fixed with ```
sudo apt-get install libnss-myhostname
```


Thank you.

---

### Post by norris-alan on 2014-06-01
> **matt_symes said:**
> Hi

I wonder if it's your USB ports or the USB hub is auto-suspending due to power management.

What's the output of 

```
cat /sys/bus/usb/devices/usb*/power/control
```

Output is:
```
auto
auto
auto
auto
auto
auto
auto
auto
```

> **matt_symes said:**
> 
and do you still get the same problem if you run this just after booting the machine ?

```
echo "on" | sudo tee /sys/bus/usb/devices/usb*/power/control
```

It is not persistent between machines. 

Yes, I still have the issue after a reboot when I run this command.

> **matt_symes said:**
> 
You can also check with powertop if you prefer something slightly more user friendly.

```
sudo apt-get install powertop
```

Look on the tunables tab.  If it's set to bad then auto-suspend is disabled and this is what you want.

Kind regards 


All are set to bad. Thank you.

---

### Post by norris-alan on 2014-06-01
**Additional Info:**

Today while trying to resolve this issue, I had a penstick in my usb port. I closed my laptop to take a break and when I reopened my laptop, the penstick was recognized by my computer for a short time (about one minute) and "disconnected" itself without me removing the penstick. I tried closing my laptop and reopening a few times, and the system seems to recognize the penstick each time before quickly disconnecting it. After doing so I ran dmesg and noticed some output regarding the usb:

```
[  566.249433] PM: Entering mem sleep[  566.249463] Suspending console(s) (use no_console_suspend to debug)
[  566.250567] sd 1:0:0:0: [sda] Synchronizing SCSI cache
[  566.251009] sd 1:0:0:0: [sda] Stopping disk
[  566.892034] PM: suspend of devices complete after 642.448 msecs
[  566.892165] PM: late suspend of devices complete after 0.127 msecs
[  566.908141] pcieport 0000:00:1c.0: System wakeup enabled by ACPI
[  566.924188] ehci-pci 0000:00:1d.7: System wakeup enabled by ACPI
[  566.940137] uhci_hcd 0000:00:1d.1: System wakeup enabled by ACPI
[  566.940187] uhci_hcd 0000:00:1d.0: System wakeup enabled by ACPI
[  566.956128] PM: noirq suspend of devices complete after 63.960 msecs
[  566.956260] ACPI: Preparing to enter system sleep state S3
[  566.967926] PM: Saving platform NVS memory
[  566.968198] Disabling non-boot CPUs ...
[  566.968198] ACPI: Low-level resume complete
[  566.968198] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S0_] (20131115/hwxface-580)
[  566.968198] PM: Restoring platform NVS memory
[  566.968198] ACPI: Waking up from system sleep state S3
[  567.056333] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
[  567.056386] uhci_hcd 0000:00:1d.1: System wakeup disabled by ACPI
[  567.072086] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
[  567.120177] PM: noirq resume of devices complete after 110.676 msecs
[  567.120279] PM: early resume of devices complete after 0.064 msecs
[  567.195320] usb usb3: root hub lost power or was reset
[  567.195524] usb usb4: root hub lost power or was reset
[  567.195909] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[  567.196175] usb usb5: root hub lost power or was reset
[  567.196375] usb usb6: root hub lost power or was reset
[  567.196572] usb usb7: root hub lost power or was reset
[  567.196765] usb usb8: root hub lost power or was reset
[  567.197008] pcieport 0000:00:1c.0: System wakeup disabled by ACPI
[  567.198090] ath: phy0: ASPM enabled: 0x42
[  567.516069] ata5: SATA link down (SStatus 0 SControl 300)
[  567.516131] ata1: SATA link down (SStatus 0 SControl 300)
[  567.688055] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  567.720752] ata6.00: configured for UDMA/100
[  570.152082] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  570.192181] ata2.00: configured for UDMA/133
[  570.192374] sd 1:0:0:0: [sda] Starting disk
[  570.201573] PM: resume of devices complete after 3081.289 msecs
[  570.201734] PM: Finishing wakeup.
[  570.201735] Restarting tasks ... done.
[  570.227365] video LNXVIDEO:00: Restoring backlight state
[  570.324112] usb 2-3: new high-speed USB device number 7 using ehci-pci
[  570.458711] usb 2-3: New USB device found, idVendor=154b, idProduct=005b
[  570.458716] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  570.458719] usb 2-3: Product: USB 2.0 FD
[  570.458721] usb 2-3: Manufacturer: PNY Technologies
[  570.458723] usb 2-3: SerialNumber: AD49HD1000001433
[  570.459490] usb-storage 2-3:1.0: USB Mass Storage device detected
[  570.472277] scsi10 : usb-storage 2-3:1.0
[  570.580710] atl1c 0000:02:00.0: irq 46 for MSI/MSI-X
[  570.584210] usb 1-3: new high-speed USB device number 3 using ehci-pci
[  570.597146] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  570.663806] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  570.985876] usb 1-3: New USB device found, idVendor=0bda, idProduct=0138
[  570.985881] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  570.985884] usb 1-3: Product: USB2.0-CRW
[  570.985886] usb 1-3: Manufacturer: Generic
[  570.985888] usb 1-3: SerialNumber: 20090516388200000
[  570.991761] ums-realtek 1-3:1.0: USB Mass Storage device detected
[  571.016806] scsi11 : usb-storage 1-3:1.0
[  571.017109] usb 1-3: USB disconnect, device number 3
[  571.649056] scsi 10:0:0:0: Direct-Access     PNY      USB 2.0 FD       1100 PQ: 0 ANSI: 4
[  571.651563] sd 10:0:0:0: Attached scsi generic sg2 type 0
[  571.653762] sd 10:0:0:0: [sdb] 15950592 512-byte logical blocks: (8.16 GB/7.60 GiB)
[  571.654578] sd 10:0:0:0: [sdb] Write Protect is off
[  571.654584] sd 10:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  571.655332] sd 10:0:0:0: [sdb] No Caching mode page found
[  571.655337] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[  571.659079] sd 10:0:0:0: [sdb] No Caching mode page found
[  571.659085] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[  571.659995]  sdb:
[  571.681551] sd 10:0:0:0: [sdb] No Caching mode page found
[  571.681558] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[  571.681563] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[  571.822615] wlan0: authenticate with 10:0d:7f:52:13:63
[  571.853979] wlan0: send auth to 10:0d:7f:52:13:63 (try 1/3)
[  571.856235] wlan0: authenticated
``` 


I am guessing this may be part of the problem:

```
[  567.195320] usb usb3: root hub lost power or was reset
[  567.195524] usb usb4: root hub lost power or was reset
[  567.196175] usb usb5: root hub lost power or was reset
[  567.196375] usb usb6: root hub lost power or was reset
[  567.196572] usb usb7: root hub lost power or was reset
[  567.196765] usb usb8: root hub lost power or was reset
```

---

### Post by michael-dacova on 2014-06-02
whats the make and model of the Laptop

---

### Post by matt_symes on 2014-06-02
Hi

There are have some issues in the past with the hubs disconnecting.

Can you check both your hardware and install with these commands to see if there is any commonality.

```
lspci -nnk | grep -iA2 usb
```

```
uname -a
```

```
cat /etc/lsb-release
```

It may be worth raising a bug report here.

What make and model of pen drives are you both using ?

Kind regards

---

### Post by t0omas on 2014-08-16
Same issue here.
USB ports where working after new install of ubuntu, after reboot they dont work.

> root@tom-Lenovo-G510:~# lspci -nnk | grep -iA2 usb
00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: xhci_hcd
--
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: ehci-pci
--
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: ehci-pci


> 
root@tom-Lenovo-G510:~# uname -a
Linux tom-Lenovo-G510 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


> 
root@tom-Lenovo-G510:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"


please help :-D

---

### Post by vivideo on 2015-04-07
Same issue here. During boot the red usb-mouse-light lightens up. But as soon as the login-screen appears, the light disappears and no mouse (nor any other usb-device) is working. So: usb-ports seem to load, but the devices seem to be turned off automatically during the last steps of the boot. Strangely this issue isn't happing every boot. Occasionally the start-up proceeds successfully, and all usb-devices are loaded correctly. Interesting notice from 'usbview' a program I installed to view usb activity: "Can not open the file /sys/kernel/debug/usb/devices. Verify that you have USB compiled into your kernel, have the USB core modules loaded, and have the usbdevfs filesystem mounted."  Does this ring a bell to someone?

[SIZE=2](p.s. my environment is an dual-booted win8.1/Ubuntu HP Envy 15 x360 notebook. Concerning the OS:

[SIZE=2]> 3.13.0-48-generic #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
[/SIZE]
> 00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:22d6]
    Kernel driver in use: xhci_hcd
--
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:22d6]
    Kernel driver in use: ehci-pci

[/SIZE]

---

### Post by vivideo on 2015-04-14
Still figuring out what's wrong with my USB-hosts, I entered "lsusb -v" which gave me the results quoted beneath. Does somebody know why Ubuntu couldn't "open the device"?

Hope the read some suggestions :)

> lsusb -v

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x8000 
  bcdDevice            0.04
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12

Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            3.13
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
        bMaxBurst               0

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12



---

### Post by narcisgarcia on 2015-04-17
Same problem here: at 70% of sessions USB devices completely don't work, and other 30% are working in an unstable way (p.e. pendrive remounting every X minutes). Webcam is affected too.

Already tried with:
```
echo "on" | sudo tee /sys/bus/usb/devices/usb*/power/control
```
...but no success.

> $ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

> $ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty
(Ubuntu GNOME)

```
$ lspci -nnk | grep -iA2 usb
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
	Subsystem: Lenovo Device [17aa:3978]
	Kernel driver in use: xhci_hcd
--
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
	Subsystem: Lenovo Device [17aa:3978]
	Kernel driver in use: ehci-pci
```

```
$ sudo lshw -short
H/W path       Device      Class          Description
=====================================================
                           system         20351 (LENOVO_MT_20351_BU_idea_FM_Lenovo G50-70)
/0                         bus            Lancer 5A2
/0/0                       memory         128KiB BIOS
/0/4                       processor      Intel(R) Core(TM) i3-4005U CPU @ 1.70GHz
/0/4/b                     memory         32KiB L1 cache
/0/4/c                     memory         256KiB L2 cache
/0/4/d                     memory         3MiB L3 cache
/0/4/1.1                   processor      Logical CPU
/0/4/1.2                   processor      Logical CPU
/0/4/1.3                   processor      Logical CPU
/0/4/1.4                   processor      Logical CPU
/0/4/1.5                   processor      Logical CPU
/0/4/1.6                   processor      Logical CPU
/0/4/1.7                   processor      Logical CPU
/0/4/1.8                   processor      Logical CPU
/0/4/1.9                   processor      Logical CPU
/0/4/1.a                   processor      Logical CPU
/0/4/1.b                   processor      Logical CPU
/0/4/1.c                   processor      Logical CPU
/0/4/1.d                   processor      Logical CPU
/0/4/1.e                   processor      Logical CPU
/0/4/1.f                   processor      Logical CPU
/0/4/1.10                  processor      Logical CPU
/0/a                       memory         32KiB L1 cache
/0/12                      memory         4GiB System Memory
/0/12/0                    memory         DIMM [empty]
/0/12/1                    memory         DIMM [empty]
/0/12/2                    memory         4GiB SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
/0/12/3                    memory         DIMM [empty]
/0/100                     bridge         Haswell-ULT DRAM Controller
/0/100/2                   display        Haswell-ULT Integrated Graphics Controller
/0/100/3                   multimedia     Haswell-ULT HD Audio Controller
/0/100/14                  bus            Lynx Point-LP USB xHCI HC
/0/100/16                  communication  Lynx Point-LP HECI #0
/0/100/1b                  multimedia     Lynx Point-LP HD Audio Controller
/0/100/1c                  bridge         Lynx Point-LP PCI Express Root Port 3
/0/100/1c/0    eth0        network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1c.3                bridge         Lynx Point-LP PCI Express Root Port 4
/0/100/1c.3/0  wlan0       network        QCA9565 / AR9565 Wireless Network Adapter
/0/100/1d                  bus            Lynx Point-LP USB EHCI #1
/0/100/1f                  bridge         Lynx Point-LP LPC Controller
/0/100/1f.2                storage        Lynx Point-LP SATA Controller 1 [AHCI mode]
/0/100/1f.3                bus            Lynx Point-LP SMBus Controller
/0/1           scsi0       storage        
/0/1/0.0.0     /dev/sda    disk           1TB ST1000LM024 HN-M
/0/1/0.0.0/1   /dev/sda1   volume         838GiB EXT4 volume
/0/1/0.0.0/2   /dev/sda2   volume         93GiB EXT4 volume
/0/2           scsi1       storage        
/0/2/0.0.0     /dev/cdrom  disk           DVDRAM GUA0N
/1                         power          CRB Battery 0
```
(Computer: Lenovo G50-70 - Model name: 20351)

> $ lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

---

### Post by vivideo on 2015-04-23
Do you also use Windows Narcis?

I discovered something funny: the chance Ubuntu initializes my usb-ports correctly is **greater** when I had booted the notebook with Windows 8.1 before! Although both operating systems operate separately (dual boot) on my notebook, it seems that Windows still determines the availability of resources. The crusade goes on..

---

### Post by narcisgarcia on 2015-04-23
This computer came with Windows 8.1 preinstalled, but we formatted whole disk just when package was open. Now Ubuntu GNOME 14.04 (updated) is the only operating system (no UEFI).

---

### Post by vivideo on 2015-04-23
hmmm.. in my opinion Windows is now even more suspicious ;) Could a windows-minded BIOS-setting be responsible?

---

### Post by sirgilles on 2015-05-17
I have the same problem. 

During the boot-up of Ubuntu/Mint, the USB mouse has the red light turned on. From the moment the (cinnamon) log-in screen is loaded, the light goes off and the mouse does not work. This applies to all USB ports of the laptop, except the extra-power charging port.

The solution which works for me: After logging in, put laptop in suspend, wake up again, and... voilà, the red light is on (and all other USB ports work too).

Hope this is of help.

System: Thinkpad T440s dual boot Win7/Mint 17.1

---

### Post by vivideo on 2015-05-26
Interesting solution! I tried it, but in my case it didn't work. Though, in the meantime I discovered something to increase the chance of boot including the USB-ports: Most of the successful boots happened when my power-adapter was disconnected.

Everytime a system update is being installed, I hope this bug is solved...

---

### Post by sincere-music on 2015-09-15
Has there been any progress on this? Has it even been reported as a bug? After all, being unable to use any USB ports is a large problem.
Sorry to be so straightforward, but I&#8217;m unable to troubleshoot myself. I&#8217;d need to search for professional help.

---

### Post by Razvan_Nicoara on 2015-10-14
I've had the same issue, no USB device was working. 

The fix for me was in: [B]/etc/default/grub
[/B]Changed form: 

[COLOR=#111111][FONT=Consolas]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noautogroup" 
[B]
to[/B] 

[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/FONT][/COLOR]

---

### Post by narcisgarcia on 2015-10-14
A solution for me with Acer Aspire ES1-512 has been to disable xHCI in BIOS setup.
xHCI enablement was for USB 3.0 speed.

---

### Post by vivideo on 2015-10-15
> **Razvan_Nicoara said:**
> I've had the same issue, no USB device was working. 

The fix for me was in: [B]/etc/default/grub
[/B]Changed form: 

[COLOR=#111111][FONT=Consolas]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noautogroup" 
[B]
to[/B] 

[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/FONT][/COLOR]

Thanks for posting this suggestion!
In my configuration, 'noautogroup' wasn't present, so for me the issue has nothing to do with this Grub setting.
Still, in my case it really helps to start my notebook WITHOUT the poweradapter attached!

---

### Post by muzakki.ahmad29 on 2016-01-25
> **matt_symes said:**
> Hi

I wonder if it's your USB ports or the USB hub is auto-suspending due to power management.

What's the output of 

```
cat /sys/bus/usb/devices/usb*/power/control
```

and do you still get the same problem if you run this just after booting the machine ?

```
echo "on" | sudo tee /sys/bus/usb/devices/usb*/power/control
```

It is not persistent between machine reboots.

You can also check with powertop if you prefer something slightly more user friendly.

```
sudo apt-get install powertop
```

Look on the tunables tab.  If it's set to bad then auto-suspend is disabled and this is what you want.

Kind regards

this soluiton sould be on every askubuntu.com question with this problem, thanks it works for me :guitar:

---

### Post by matt_symes on 2016-01-27
Hi

> **muzakki.ahmad29 said:**
> this soluiton sould be on every askubuntu.com question with this problem, thanks it works for me :guitar:

It will not persist after reboots though.

You may want to add the line to rc.local or edit the modules file to stop autosuspend there.

Kind regards

---

### Post by m_d2 on 2016-03-13
For me this problem does not occur on kernel 3.13.0-61-generic but does occur on any newer kernels (3.13.0-77-generic and 3.13.0-79-generic); and any of the above fixes and every other fix I found do not work.
Seems to me like it's a kernel issue.

Using Ubuntu 14.04 LTS as dualboot on an Acer Aspire E1-572

EDIT: Somehow it is working now, on all kernels.. I don't know what I did to fix it though. I only tried going into the BIOS and exiting without saving changes. Weird..
EDIT 2: Nope, didn't work for long. Still always works in the old kernel.
EDIT 3: Just had an update to kernel 3.13.0-83-generic and it did not fix the problem.

---

### Post by m_d2 on 2016-04-08
I just got updated to kernel 3.13.0-85-generic and it is still not working.

---

### Post by m_d2 on 2016-05-19
I just got updated to kernel 3.13.0-86-generic and it is still not working.

---

### Post by Dread Knight on 2016-10-31
I've upgraded to Ubuntu 16.10 and with the latest 2 kernels, I have all USB ports randomly stopping, which is ultra annoying, as I use USB mouse, keyboard and speakers.
I constantly need to remind myself spam ESC key at boot time, to select Advanced settings and pick the last kernel option; looked into setting a kernel as default, but I find that sort of stuff rather risky...

---

### Post by erchamion2 on 2016-12-14
Ok same here. usb woerks at boot time so it is not hardware.

---

### Post by erchamion2 on 2016-12-14
what i did was to install the lts enablement stack (kernel 4.4.0.53) and the problem seems to be gone by the moment. see:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---


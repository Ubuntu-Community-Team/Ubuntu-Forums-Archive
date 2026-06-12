---
title: "External Drive: auto unmounts and prevents PC booting"
date: 2012-01-14
forum: Hardware
---

### Post by cozski on 2012-01-14
Hello, I have a couple of issues with a Iomega external drive. If it's connected to my desktop at startup it prevents it from booting. At the boot stage it stops when it is checking scrolling through my usb ports (presumably to see what's connected) and goes no further. I can connect the drive once my desktop has booted and in most instances it works okay, but on some occasions it just unmounts itself.

Any suggestion/advice welcomed. Thanks.

---

### Post by madvinegar on 2012-01-15
Have you tried ticking off the option for automount?

Alt+F2, write gconf-editor hit enter and then navigate to: 

apps - nautilus -preferences and untick the box which says "media-automount".

---

### Post by varunendra on 2012-01-15
> **cozski said:**
> ..At the boot stage it **stops when it is checking** scrolling through my usb ports (presumably to see what's connected) and goes no further. 
<snip>
.. but on some occasions it just **unmounts itself**.
Looks like the system has problem recognizing the drive, and the 'unmounting itself' behaviour suggests it may be due to weak signal/powersupply.

Try replacing the USB cable and connecting it to the backside USB ports.

If it is a 2.5" drive (with no external power adapter), make sure your motherboard is able to deliver sufficient power to it. Also, make sure to use a good quality USB cable of short length (original ones are usually good enough). The backside USB ports are usually better than the front ones in terms of both power supply and signals.

Even if it is a drive with external power supply, using it with a USB cable of bad quality or too much length (more than 1.5m) may cause the same issue.

---

### Post by cozski on 2012-01-15
> **madvinegar said:**
> Have you tried ticking off the option for automount?

Alt+F2, write gconf-editor hit enter and then navigate to: 

apps - nautilus -preferences and untick the box which says "media-automount".

Hey, thanks for that... unfortunately when I click on Apps the window just closes and nothing else appears to happen... any thoughts?

---

### Post by cozski on 2012-01-15
> **varunendra said:**
> Looks like the system has problem recognizing the drive, and the 'unmounting itself' behaviour suggests it may be due to weak signal/powersupply.

Try replacing the USB cable and connecting it to the backside USB ports.

If it is a 2.5" drive (with no external power adapter), make sure your motherboard is able to deliver sufficient power to it. Also, make sure to use a good quality USB cable of short length (original ones are usually good enough). The backside USB ports are usually better than the front ones in terms of both power supply and signals.

Even if it is a drive with external power supply, using it with a USB cable of bad quality or too much length (more than 1.5m) may cause the same issue.

Hey... thanks for that. It's currently connected to the backside ports and the usb cable is a fairly short one. It also requires AC power and I don't have another one at the moment, but I guess I could get one if you think it might be the primary reason for it unmounting. It only started to do it when I installed 11.10 and was fine before that in 11.04 so I presumed there might be a link.

---

### Post by varunendra on 2012-01-15
> **cozski said:**
> It only started to do it when I installed 11.10 and was fine before that in 11.04 so I presumed there might be a link.
Yes there may be. What I suggested is just one of many possible reasons. It's just the 'unmounts itself' part of your first post that makes me suspect the signal quality. But it may be something else (including a probability that maybe 11.10 is not handling the ports as 'strongly' as 11.04 did).

Bottomline:
if its usb cable is the original one and also the drive is externally powered, you shouldn't need to bother with another cable. The ones supplied with these drives are usually good enough.

Maybe some more digging could give some clue about what is happening. As a wild shot, when it disconnects by itself, run and post the output of the following command:
```
dmesg | grep -i usb
```

---

### Post by cozski on 2012-01-15
> **varunendra said:**
> Yes there may be. What I suggested is just one of many possible reasons. It's just the 'unmounts itself' part of your first post that makes me suspect the signal quality. But it may be something else (including a probability that maybe 11.10 is not handling the ports as 'strongly' as 11.04 did).

Bottomline:
if its usb cable is the original one and also the drive is externally powered, you shouldn't need to bother with another cable. The ones supplied with these drives are usually good enough.

Maybe some more digging could give some clue about what is happening. As a wild shot, when it disconnects by itself, run and post the output of the following command:
```
dmesg | grep -i usb
```

Hey, it just unmounted - it was only mounted for around 30 seconds. Here is the code:

[HTML]sunonthecross@sunonthecross:~$ dmesg | grep -i usb
[    0.196240] usbcore: registered new interface driver usbfs
[    0.196275] usbcore: registered new interface driver hub
[    0.196338] usbcore: registered new device driver usb
[    2.347653] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.347816] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.364018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.364228] hub 1-0:1.0: USB hub found
[    2.364374] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.364398] uhci_hcd: USB Universal Host Controller Interface driver
[    2.364561] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.364795] hub 2-0:1.0: USB hub found
[    2.364988] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.365215] hub 3-0:1.0: USB hub found
[    2.365397] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.365605] hub 4-0:1.0: USB hub found
[    2.365799] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.366030] hub 5-0:1.0: USB hub found
[    2.732090] usb 1-3: new high speed USB device number 3 using ehci_hcd
[    2.865209] hub 1-3:1.0: USB hub found
[    2.976051] usb 1-5: new high speed USB device number 4 using ehci_hcd
[    3.115053] usbcore: registered new interface driver uas
[    3.116889] Initializing USB Mass Storage driver...
[    3.117192] scsi4 : usb-storage 1-5:1.0
[    3.117453] usbcore: registered new interface driver usb-storage
[    3.117459] USB Mass Storage support registered.
[    3.460033] usb 2-2: new low speed USB device number 2 using uhci_hcd
[    3.679244] input: BTC USB Multimedia Cordless Kit   as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input2
[    3.679510] generic-usb 0003:03F0:050C.0001: input,hidraw0: USB HID v1.00 Keyboard [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:1d.0-2/input0
[    3.727621] input: BTC USB Multimedia Cordless Kit   as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input3
[    3.728363] generic-usb 0003:03F0:050C.0002: input,hiddev0,hidraw1: USB HID v1.00 Mouse [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:1d.0-2/input1
[    3.728408] usbcore: registered new interface driver usbhid
[    3.728424] usbhid: USB HID core driver
[    3.892024] usb 5-1: new full speed USB device number 2 using uhci_hcd
[    4.069276] scsi5 : usb-storage 5-1:1.0
[    4.140141] usb 1-3.1: new high speed USB device number 6 using ehci_hcd
[    4.340241] usb 1-3.5: new high speed USB device number 7 using ehci_hcd
[    4.440303] usb-storage 1-3.5:1.0: Quirks match for vid 05e3 pid 0723: 8000
[    4.440800] scsi6 : usb-storage 1-3.5:1.0
[    5.072461] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    5.075453] scsi 5:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    5.078456] scsi 5:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    5.081463] scsi 5:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   29.645158] uvcvideo: Found UVC 1.00 device USB2.0 1.3MP UVC Camera (04f2:a133)
[   29.668214] input: USB2.0 1.3MP UVC Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1/1-3.1:1.0/input/input4
[   29.671463] usbcore: registered new interface driver uvcvideo
[   29.671470] USB Video Class driver (v1.1.0)
[   30.106339] usbcore: registered new interface driver snd-usb-audio
[  331.340066] usb 1-6: new high speed USB device number 8 using ehci_hcd
[  331.476898] scsi7 : usb-storage 1-6:1.0
[  935.347392] usb 1-6: USB disconnect, device number 8
[ 3044.748047] usb 1-6: new high speed USB device number 9 using ehci_hcd
[ 3044.886203] scsi8 : usb-storage 1-6:1.0
[ 3781.108466] usb 1-6: USB disconnect, device number 9
[ 7449.504229] usb 1-3.1: reset high speed USB device number 6 using ehci_hcd
[ 7449.626817] snd-usb-audio 1-3.1:1.2: no reset_resume for driver snd-usb-audio?
[ 7449.626824] snd-usb-audio 1-3.1:1.3: no reset_resume for driver snd-usb-audio?
[10238.800059] usb 1-6: new high speed USB device number 10 using ehci_hcd
[10238.938830] scsi9 : usb-storage 1-6:1.0
[10436.535752] usb 1-6: USB disconnect, device number 10
[89307.244039] usb 1-6: new high speed USB device number 11 using ehci_hcd
[89307.382164] scsi10 : usb-storage 1-6:1.0
[91840.745112] usb 1-6: USB disconnect, device number 11
[91863.160070] usb 1-6: new high speed USB device number 12 using ehci_hcd
[91863.298369] scsi11 : usb-storage 1-6:1.0
[94442.993076] usb 1-6: USB disconnect, device number 12
[106723.560191] usb 1-3.1: reset high speed USB device number 6 using ehci_hcd
[106877.496045] usb 1-4: new high speed USB device number 13 using ehci_hcd
[106877.630140] scsi12 : usb-storage 1-4:1.0
[106901.176096] usb 1-4: reset high speed USB device number 13 using ehci_hcd
[106901.288107] usb 1-4: device descriptor read/64, error -32
[106901.504055] usb 1-4: device descriptor read/64, error -32
[106901.720084] usb 1-4: reset high speed USB device number 13 using ehci_hcd
[106901.832082] usb 1-4: device descriptor read/64, error -32
[106902.048101] usb 1-4: device descriptor read/64, error -32
[106902.264084] usb 1-4: reset high speed USB device number 13 using ehci_hcd
[106902.300671] usb 1-4: device descriptor read/8, error -71
[106902.433117] usb 1-4: device descriptor read/8, error -71
[106902.648643] usb 1-4: reset high speed USB device number 13 using ehci_hcd
[106902.680446] usb 1-4: device descriptor read/8, error -71
[106902.812296] usb 1-4: device descriptor read/8, error -71
[106902.916235] usb 1-4: USB disconnect, device number 13
[106903.072091] usb 1-4: new high speed USB device number 14 using ehci_hcd
[106903.184088] usb 1-4: device descriptor read/64, error -32
[106903.408081] usb 1-4: device descriptor read/64, error -32
[106903.624094] usb 1-4: new high speed USB device number 15 using ehci_hcd
[106903.736094] usb 1-4: device descriptor read/64, error -32
[106903.952108] usb 1-4: device descriptor read/64, error -32
[106904.168077] usb 1-4: new high speed USB device number 16 using ehci_hcd
[106904.208325] usb 1-4: device descriptor read/8, error -71
[106904.340296] usb 1-4: device descriptor read/8, error -71
[106904.556088] usb 1-4: new high speed USB device number 17 using ehci_hcd
[106904.588354] usb 1-4: device descriptor read/8, error -71
[106904.720354] usb 1-4: device descriptor read/8, error -71
[106904.824205] hub 1-0:1.0: unable to enumerate USB device on port 4
[106905.092036] usb 3-2: new full speed USB device number 2 using uhci_hcd
[106905.212050] usb 3-2: device descriptor read/64, error -32
[106905.436042] usb 3-2: device descriptor read/64, error -32
[106905.652045] usb 3-2: new full speed USB device number 3 using uhci_hcd
[106905.772043] usb 3-2: device descriptor read/64, error -32
[106905.996338] usb 3-2: device descriptor read/64, error -32
[106906.212043] usb 3-2: new full speed USB device number 4 using uhci_hcd
[106906.243836] usb 3-2: device descriptor read/8, error -71
[106906.371826] usb 3-2: device descriptor read/8, error -71
[106906.584043] usb 3-2: new full speed USB device number 5 using uhci_hcd
[106906.615773] usb 3-2: device descriptor read/8, error -71
[106906.743757] usb 3-2: device descriptor read/8, error -71
[106906.844044] hub 3-0:1.0: unable to enumerate USB device on port 2


[/HTML]

---

### Post by varunendra on 2012-01-16
Some extensive search suggests it is a long existing bug which often reappears with new releases, and may get fixed itself in time after a few updates.

Meanwhile, the following fix seems to be working for most:

(_Temporary implementation_):

In short, we have to add the following line to kernel boot line of grub:
> usbcore.autosuspend=-1 usbcore.old_scheme_first=YTo do so, press and hold 'shift' key while booting to bring up grub menu. Select the default Ubuntu entry (Ubuntu, with kernel.....) and press 'E' to edit the kernel boot line for that entry. Using arrow keys, bring the cursor to the line which ends with "quite splash". Press 'End' key to bring the cursor to the end of the line. Leaving a space after "splash" (or whatever is in the end of line), type the following:
> usbcore.autosuspend=-1 usbcore.old_scheme_first=Y (mind the spaces)
Then press Ctrl+x or F10 to boot.

Once logged-in, type the following commands in terminal to make sure the change (temporary) has taken effect:
```
cat /sys/module/usbcore/parameters/autosuspend
cat /sys/module/usbcore/parameters/old_scheme_first
```the first command should return "-1" and the second one should return "Y".

Close terminal and see if the usb drive now connects any better. If the issue seems to have been fixed, we can add these parameters to /etc/default/grub file to make it permanent.

---


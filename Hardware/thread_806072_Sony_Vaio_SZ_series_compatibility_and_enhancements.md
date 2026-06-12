---
title: "Sony Vaio SZ series: compatibility and enhancements"
date: 2008-05-24
forum: Hardware
---

### Post by astadolfo3 on 2008-05-24
This forum for discussing laptop installation issues and available enhancements to the system. I have a Vaio VGN SZ 450 N and I trust that many of the solutions I found are applicable to the SZ series and laptops in general. 

Some of the important topics are:

suspend/hibernate
camera
bluetooth
graphics with dual card nvidia and intel
fingerprint reader
memory card reader
sound and controls


All of the above work well on my vaio after proper configuration.
Currently I'm running Ubuntu 8.04.

---

### Post by zerubbabel on 2008-06-09
Have you posted the "proper configuration" anywhere? I wonder whether it would apply also to the TZ series. I am hoping to get all those things to work on my TZ195N.

---

### Post by Duh_ on 2008-06-17
yes, i would be very interested, esspecially in:
- how to get hibernate/suspend to work
- installing the fingerprint software and drivers

my model is a VGN-SZ5XN. i would appreciate sime help ;)

---

### Post by srfito on 2008-07-02
Hello!

I have a new Vaio VGN-SZ71MN/B and, though most things work, I haven't managed to use the bluetooth. Everything seems to be ok, but neither the laptop finds my Sony Ericsson phone, nor the phone finds the laptop.

Did anybody have the same problem and know how to fix it?

Thanks a lot!

---

### Post by astadolfo3 on 2008-07-12
I'll try to put my configuration on a web page as soon as I get some time. In the meantime:

If suspend/hibernate is not working, see my postings on this forum:

[http://ubuntuforums.org/showthread.php?t=691669&highlight=suspend+stopped+feisty&page=2](http://ubuntuforums.org/showthread.php?t=691669&highlight=suspend+stopped+feisty&page=2)

If someone really needs it, I'll post the instructions for the fingerprint reader, however it won't help much since there are currently no applications I'm aware of that take advantage of this feature. The driver works on my PC and recognizes my finger by giving feedback on the command line. However due to the lack of applications, I can't use it to login the system or in web pages like I do in Vista. So I'm not sure if it's worth the effort for anyone to install the drivers until a suitable application exists for ubuntu. If anyone finds any application for the fingerprint reader please post it.

For bluetooth, I installed the package bluetooth, and the bluez utils. It can search and find bluetooth devices, including my Motorola V3, transfer files and connect wireless to the internet via cell phone using GPRS and UMTS (this part requires modem configuration as well).

Here's my bluetooth packages output:

me@mypc:~$ dpkg -l *blue*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  bluetooth      3.26-0ubuntu6  Bluetooth stack utilities
ii  bluez-audio    3.26-0ubuntu6  Bluetooth audio support
ii  bluez-cups     3.26-0ubuntu6  Bluetooth printer driver for CUPS
un  bluez-firmware <none>         (no description available)
ii  bluez-gnome    0.25-0ubuntu1  Bluetooth utilities for GNOME
un  bluez-pan      <none>         (no description available)
un  bluez-passkey- <none>         (no description available)
rc  bluez-pin      0.30-2.1ubuntu Bluetooth PIN helper with D-BUS support
un  bluez-sdp      <none>         (no description available)
ii  bluez-utils    3.26-0ubuntu6  Bluetooth tools and daemons
un  gnome-bluetoot <none>         (no description available)
un  gtk2-engines-l <none>         (no description available)
pn  kdebluetooth   <none>         (no description available)
ii  libbluetooth2  3.29-0ubuntu1  Library to use the BlueZ Linux Bluetooth sta
pn  libkbluetooth0 <none>         (no description available)

you should be able to detect your device with the following command:
$ hcitool scan
Scanning ...
        00:01:E3:25:08:A7       Rudy's Siemens SX1

---

### Post by JGJones on 2008-10-31
I've just gotten a Sony VGN-SZ71E laptop.

I have installed Ubuntu 8.10 on it and am glad to report that Ubuntu works well except for the following:

Webcam - no drivers although supposely you can use the R5U870 driver from this site - [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870) - my webcam is listed under the supported cameras list but I've not been able to compile the driver. There is a userspace driver available - R5u87x from here: [http://lists.mediati.org/archives/r5u870-list/2008-September/000053.html](http://lists.mediati.org/archives/r5u870-list/2008-September/000053.html) but as mentioned is in alpha. Again I wasn't able to compile this either. If anyone have better luck than me, please post :)

LCD Brightness setting - this cannot be changed...it's set to very high and can't be reduced despite having installed the suggested tool for this - any solution? It's a huge drain on battery life.

Graphics - Intel and Nvidia works just fine with Compiz, although after using Nvidia, I switched back to Intel, I'm not able to use Compiz anymore but this just happened so I've not looked into why yet.

Primarily it's just the LCD brightness and the webcam that's a problem and both are needed (I'm deaf, so I do make a lot of video calls on Skype)

Suspend - This works. But not if I close screen. I have to activate it manually via menu or Gnome-Do - it seems that Ubuntu cannot detect if I close the screen but this is a minor issue since the workaround is that I'm able to do it very fast via Gnome-Do and suspend works - so far no issues with this aspect.

Bluetooth - Hardware is detected and present. But both of my phones isn't able to see the laptop even though it's set to present. Using the hcitool scan command, the laptop isn't able to see the phones. I don't know if the bluetooth hardware works as I don't have Vista on laptop to test.

Apart from the above, I'm able to use the laptop for every day work etc.

---

### Post by pihhan on 2008-10-31
You may try TJ's PPA archive to get module. Note his packages are not official. See [https://launchpad.net/~intuitivenipple/+archive](https://launchpad.net/~intuitivenipple/+archive)

For intel graphics card, backlight control does work, but might need some settings. See bugs [https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444) and [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652). Some reports dimming for Nvidia is possible also, but i dont have one and dont know whether it work for all models.

as for bluetooth, it worked to me after resetting that interface. It should work to "sudo hciconfig hci0 reset" command. I added parameter to usb_hci module, with reset=1 (i think, i dont write from vaio, see modinfo usb_hci for parameters, search for reset).
add to (sudoedit) /etc/modprobe.d/sony-laptop:

option usb_hci reset=1

It should work then after reboot or module reload. I have another problem however. I dont use or have bluetooth device and i would like to be off to save battery, ubuntu does not easy way to turn it off, maybe because it is connected using usb.

Suspend and hibernation does work with my intel also, nothing much special needed for it.

---

### Post by JGJones on 2008-10-31
Many thanks, some good un's in there. For the webcam, I've since discovered that it's a bug where one cannot compile the r5u870 driver against the latest kernel in Ubuntu 8.10 - see bug report here - [http://bugs.mediati.org/r5u870/issue31](http://bugs.mediati.org/r5u870/issue31)

The bluetooth tips you've mentioned - they was a great help, I've reset it and it now works so I'll add it into the script as suggested although when I'll reboot is something else (uptime for me usually measures in days/weeks as I usually only suspend the laptop rather than shutting down).

---

### Post by biochip2k on 2008-11-27
> **pihhan said:**
> 
It should work then after reboot or module reload. I have another problem however. I dont use or have bluetooth device and i would like to be off to save battery, ubuntu does not easy way to turn it off, maybe because it is connected using usb.



this script turn off bluetooth (and the blue led)
```

#!/bin/bash
echo "0" > /sys/devices/platform/sony-laptop/bluetoothpower

```

it would be good to assign this script to a key-shortcup

---


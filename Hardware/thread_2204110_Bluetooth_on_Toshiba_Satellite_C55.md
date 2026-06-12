---
title: "Bluetooth on Toshiba Satellite C55"
date: 2014-02-06
forum: Hardware
---

### Post by matthew20 on 2014-02-06
I have been running Ubuntu Desktop 12.04LTS on my Toshiba Satellite C55-A5384 since Christmas with no real problems. Today I wanted to pair a Bluetooth device (an Adafruit Bluefruit serial device) to my computer and haven't had any success.

Running lspci -nn shows:

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)

I do see the Bluetooth icon in the status bar at the top of my screen. When I click on Bluetooth Settings, I have Bluetooth turned on and visibility of "ubunto-0" on. However, when I click on the "+" icon to bring up the Bluetooth New Device Setup wizard, on the Device Search screen, I get the spinny wheel next to "Searching for devices..." but no devices are found.

My Galaxy S4 phone can 'see' the Adafruit Bluefruit, but won't see my laptop, and my laptop 'sees' neither of my devices.

Can anyone suggest some troubleshooting steps? I haven't found any promising leads in the searching that I've done.

Thanks!

---

### Post by varunendra on 2014-02-10
Welcome to the forums matthew20 !

If you haven't found a fix yet, try installing BlueMan-
```
sudo apt-get install blueman
```
It will create its own Bluetooth icon in the system tray and offers more and better control over bluetooth adapter.

Click on its icon to produce its drop-down menu > click "Adapters.." > make sure "Always visible" (or "Temporarily visible", as required) is enabled > Close

Click on the icon again to reproduce the menu > click "Local Services" > choose "Transfer" > make sure "File Receiving" and "File Sharing" are enabled (with the additional options as required) > Apply > Close

If the "Adapters.." option seems to be grayed out, it means only the bluetooth daemon is active, the device is not.

By the way, what you saw in the output of "lspci" is your wireless card, not the bluetooth adapter. Bluetooth adapters are located at USB bus, so you'll see it in the output of -
```
lsusb
```
Or "usb-devices" command for more info.

---

### Post by matthew20 on 2014-02-10
[Duplicate post]

---

### Post by matthew20 on 2014-02-10
Thanks, Varun!

I believe my laptop's Bluetooth adapter has a VID/PID of 0930:0220, which is a Toshiba VID. That's the only VID/PID on my system that makes sense as the Bluetooth adapter. (The others are hubs, the webcam, and the integrated SD card reader.)

Running "hcitool dev" shows device hci0 and the adapter's MAC address.

However, even with blueman, I am unable to discover any bluetooth devices with this adapter. I put my Samsung Galaxy into "visible to all nearby Bluetooth devices" and it doesn't see my computer, nor does my computer see the phone. 

When I plug a USB bluetooth dongle into one of the USB ports and scan for devices, I get a dropdown allowing me to select which adapter to use for scanning. The laptop will detect my phone through the external dongle, but not with the internal Bluetooth radio.

I've tried a few solutions I found online, including:
 - sudo hciconfig hci0 reset
 - editing /etc/bluetooth/main.conf and setting RememberPowered to false
 - sudo rfkill unblock bluetooth

None of these helped.

It looks like Marco Piazza may have released a patch to support this hardware about Nov. 28 of last year. (See [http://www.spinics.net/lists/linux-bluetooth/msg40925.html](http://www.spinics.net/lists/linux-bluetooth/msg40925.html).) However, I lack the expertise to find, install, and configure this patch. Is there a "Installing Linux Patches for Dummies" resource available? Is there any easy way to determine if my machine is already running this patch?



Thanks again!

-Matthew

---

### Post by varunendra on 2014-02-11
Yes, that is the Toshiba bluetooth adapter, but considering this mailing list [post]("https://lkml.org/lkml/2014/1/4/120") by Linus Torvalds himself, the support for it is almost certainly not yet included in mainstream kernel. The "ToDo" list in the post mentions -
> Marco Piazza (1):
      Bluetooth: Add support for Toshiba Bluetooth device [0930:0220]

As for patching, you'll need to get the source (code) of the drivers "ath3k" and "btusb" > apply the patch (or manually add required lines) to the relevant files > build > install.

This is probably too much trouble for just bluetooth support, unless it is really very important for you.

We may try an old, dirty trick to inject the id of the device in the running kernel driver to see if it works. For generic devices, it usually works. If you wish to try that (at your own risk of crashing the session, a reboot will reset it), here's the command sequence to load the target drivers "ath3k" and "btusb", then inject the device ID into the "ath3k" driver -
```
sudo su
modprobe -v ath3k
modprobe -v btusb
echo 0930 0220 > /sys/bus/usb/drivers/ath3k/new_id
exit
```

Since it works in parallel with driver "btusb", I don't know if it'll work or not. If not, you may also include the following command before or after the above "echo..." command -
```
echo 0930 0220 > /sys/bus/usb/drivers/btusb/new_id
```
If it works, congratulations from me. If it successfully crashes your running session, come here, congratulate me and don't ever try that again :P

It seems the support for this device will be natively available in kernel 3.13 when it becomes mainstream.

---

### Post by matthew20 on 2014-02-11
Varun, I appreciate your assistance. Regrettably, neither of the suggested fixes worked for me. Knowing that support for this hardware device is in the pipeline for 3.13 is encouraging; I think I may just wait for the release of 14.04 LTS rather than chase this down further on my current platform.

---

### Post by varunendra on 2014-02-12
>  I think I may just wait for the release of 14.04 LTS rather than chase this down further on my current platform.
I agree, and I'm sure your feedback about your experience with the mainstream kernel (3.13 or higher) should help may otherwise remain stuck with older kernels for a long time.

---


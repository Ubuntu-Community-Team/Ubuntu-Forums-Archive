---
title: "ASUS G751 - Problems and solutions"
date: 2015-01-16
forum: Hardware
---

### Post by Jukka_Alasalmi on 2015-01-16
Hi everyone,

I've just purchased an ASUS G751-JT laptop, and most things are working fine also in (K)ubuntu. There are a few hickups on the way, and I'm hoping this could be a thread for reporting and solving the issues.

The first issue with my installation was (no surprises here) with the graphics driver. I had to modify the boot options during the installation to have "nomodeset" and "text". I also removed the "splash" and "quiet" settings. This allowed me to continue with the setup.

After the installation, I had to still set the above two options until I had everything updated. The only driver currently supporting the GFX 970M and GFX 980M adapters is the nvidia-343 package. To get them, I ran the following commands:

```

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install build-essential linux-source linux-headers generic
sudo apt-get install nvidia-343
sudo nvidia-xconfig
```

After the reboot, the display driver was working perfectly.

Another issue was a 20 second delay that is caused by the macro keys. This shows up as the following lines in the dmesg log:

```

[    2.757458] usb 3-10: New USB device found, idVendor=0b05, idProduct=17fd
[    2.757461] usb 3-10: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.757463] usb 3-10: Product: ASUS ROG Macrokey
[    2.757464] usb 3-10: Manufacturer: ASUS
[    2.764810] input: ASUS ASUS ROG Macrokey as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/0003:0B05:17FD.0002/input/input14
[    2.764893] hid-generic 0003:0B05:17FD.0002: input,hidraw1: USB HID v1.10 Keyboard [ASUS ASUS ROG Macrokey] on usb-0000:00:14.0-10/input0
[    2.771815] hid (null): usage index exceeded
[    2.772023] hid-generic 0003:0B05:17FD.0003: usage index exceeded
[    2.772025] hid-generic 0003:0B05:17FD.0003: item 0 2 2 2 parsing failed
[    2.772033] hid-generic: probe of 0003:0B05:17FD.0003 failed with error -22
[   22.793963] usbhid 3-10:1.2: can't add hid device: -110
[   22.793976] usbhid: probe of 3-10:1.2 failed with error -110
```

I'm not exactly sure what is the root cause of the issue, but it is somehow related to an issue with how the macro keys report their capabilities. To fix this, I modified a line in /etc/default/grub from:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x0b05:0x17fd:0x0004"
```

After that, the boot is 20 seconds faster, because there is no longer the timeout when waiting for the device to be configured correctly.

Hopefully this will be helpful to others!

I'm still having some issues, though:

1) The touchpad doesn't get disabled by the key shortcut (Fn-F9). The wrist detection in Windows seems to detect correctly when my wrist hits the touchpad, but in Linux, this is a constant problem (because of the massive size of the touchpad [which, though, is very, very good otherwise, but just problematic in Linux]). A good way to help with this problem is to go to the System Settings => Keyboard and input devices => Touchpad => Touchbad on/off tab and check the "Disable touchpad when typing" option and increase the delay to a quite big number.
2) The display brightness doesn't work with the key shortcuts (Fn-F5 and Fn-F6). The brightness control itself works, since for example after a delay, the brightness does auto-adjust to a dimmer level and after moving the mouse, it goes back to full level.
[s]3) The headphone jack is not working correctly. When I plug in headphones, I still get the audio through the laptop speakers.[/s]

I'll post a reply if I'm able to figure these out by myself, but meanwhile, if somebody else has these solved, I'd greatly appreciate any tips!

Edit:
As mentioned above, the brightness control itself works. So in KDE System Settings, I can set custom shortcuts (Shortcuts and gestures -> Global shortcuts -> Increase brightness/Decrease brightness). I've set mine to Ctrl-F5 and Ctrl-F6 so that the symbols still give a hint on which keys to press.

There is a way to get the keys wthorking, but unfortunately, it disables the brightness control itself from working. If you want to try this, you need to add the following parameter to the GRUB_CMDLINE_LINUX_DEFAULT (as instructed above): "acpi_osi=". I've tried also adding "acpi_backlight=vendor" with that, but it doesn't help.

Edit 2:
To get the headphone jack work correctly, add the following line to /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=asus-mode5
```
Reboot the computer and the audio should work now. There are some settings which allow the usage of the bass speaker, but again, there's a tradeoff, since with those, the headphones don't work correctly.

Edit 3: There appears to be problems with the VSync by default in KDE, causing tearing when moving windows around or scrolling in the web browser etc. To fix the issue, I ran the following command:

```
sudo mkdir /etc/X11/xorg.conf.d
```

And created a file under that called 20-nvidia.conf, adding these lines:

```
Section "Device"
    Identifier      "Device0"
    Driver          "nvidia"
    Option          "TripleBuffer"      "True"
EndSection
```

After that and logging out and back in, you should see the following line in /var/log/Xorg.0.log:

```
[  2558.621] (**) NVIDIA(0): Option "TripleBuffer" "True"
```

That indicates that the setting was correctly detected and the vertical tearing should not happen anymore. It seems that the setting in nvidia-settings does not have the same effect (possibly the option either does not have an effect, or it has an effect too late in the startup).

---

### Post by inlimbo on 2015-01-27
Hi,

I'm working on much the same as you. But with ubuntu. I have asked a qustion about the sound to alsa:
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/261148](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/261148)

Tell me, is your headphones working on the correct jack? Or the line-out jack next to the USB?
Have you tried external mic?

I did some stuff to get the steam key working here, but it seems that the "video" key and the "rog" key next to the keypad will also launch steam :/ I haven't had the time to figure out how to filter out the other buttons.
[http://askubuntu.com/questions/572993/how-to-make-the-steam-key-on-asus-rog-laptop-work](http://askubuntu.com/questions/572993/how-to-make-the-steam-key-on-asus-rog-laptop-work)

---

### Post by Jukka_Alasalmi on 2015-01-31
Hi,

By adding the "options snd-hda-intel model=asus-mode5" to the /etc/modprobe.d/alsa-base.conf file and rebooting after that, my headphones are working in the corect jack (the one closest to the front edge of the laptio). I don't have an external mic actually, so I haven't tried that.

Thanks for the info on the ALSA thread! I subscribed there to keep up-to-date on that as well.

I haven't actually tried to configure the gaming specific keys, since so far I have not used them in Windows, either, and am not that familiar with fiddling around with the key bindings, so unfortunately I have no tips on that one.

---

### Post by inlimbo on 2015-02-03
> **Jukka_Alasalmi said:**
> 
There is a way to get the keys wthorking, but unfortunately, it disables the brightness control itself from working. If you want to try this, you need to add the following parameter to the GRUB_CMDLINE_LINUX_DEFAULT (as instructed above): "acpi_osi=". I've tried also adding "acpi_backlight=vendor" with that, but it doesn't help.


I have observed this too. Either xbacklight is working (without "acpi_osi=") or the fn keys are wokring but not xbacklight (with "acpi_osi=").

---

### Post by Bastik on 2015-02-17
Hallo guys,

I found a workaround for backlight control, working fine in Ubuntu 14.10: 

**sudo apt-get install xbacklight** (in 14.10, xbacklight is in the standart repositories, no need to add ppa).

Command for backlight up: **xbacklight +10**

Command for backlight down: **xbacklight -10**
 
The value (10) can be an individual number.

Then I bound some keyshortcuts: System-Settings -> Keyboard ->  Shortcuts -> Own Shortcuts and added the commands and applied  Ctrl+Shift+F5/F6 for upo and down.

Hope this helps.

Best regards

Kitsab

---

### Post by inlimbo on 2015-03-03
I noticed that the keyboard light is not turned on after sleep. Here is a quick fix. Edit /usr/lib/pm-utils/sleep.d/95led on the line after 
*      echo "7 off" >/proc/acpi/ibm/led*

add this line
*      echo 10 | sudo tee /sys/class/leds/asus\:\:kbd_backlight/brightness*

keyboard should light up after waking from sleep.

---

### Post by rrobe53 on 2015-04-03
> **Jukka_Alasalmi said:**
> 
Another issue was a 20 second delay that is caused by the macro keys. This shows up as the following lines in the dmesg log:

```

[    2.757458] usb 3-10: New USB device found, idVendor=0b05, idProduct=17fd
[    2.757461] usb 3-10: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.757463] usb 3-10: Product: ASUS ROG Macrokey
[    2.757464] usb 3-10: Manufacturer: ASUS
[    2.764810] input: ASUS ASUS ROG Macrokey as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/0003:0B05:17FD.0002/input/input14
[    2.764893] hid-generic 0003:0B05:17FD.0002: input,hidraw1: USB HID v1.10 Keyboard [ASUS ASUS ROG Macrokey] on usb-0000:00:14.0-10/input0
[    2.771815] hid (null): usage index exceeded
[    2.772023] hid-generic 0003:0B05:17FD.0003: usage index exceeded
[    2.772025] hid-generic 0003:0B05:17FD.0003: item 0 2 2 2 parsing failed
[    2.772033] hid-generic: probe of 0003:0B05:17FD.0003 failed with error -22
[   22.793963] usbhid 3-10:1.2: can't add hid device: -110
[   22.793976] usbhid: probe of 3-10:1.2 failed with error -110
```

I'm not exactly sure what is the root cause of the issue, but it is somehow related to an issue with how the macro keys report their capabilities. To fix this, I modified a line in /etc/default/grub from:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x0b05:0x17fd:0x0004"
```

After that, the boot is 20 seconds faster, because there is no longer the timeout when waiting for the device to be configured correctly.

I tried doing this, but I still get the issues while booting, although I am on Arch Linux. Here's the link to that forum with the ouput of those commands [https://bbs.archlinux.org/viewtopic.php?id=195577](https://bbs.archlinux.org/viewtopic.php?id=195577)

---

### Post by Octavian_Pais on 2015-11-28
Hello,

I found an easy fix for the brightness keys on the Asus G751JM, it is actually a combination of packages.
Not really sure which one is the responsible one but I will dig deeper and reply.

Here it is:
- GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi= "
 (The usb quirks is for the asus macro buttons which delay the boot by 20 seconds.)
- Kernel image and headers 4.4.0-040400 RC2
- Nvidia drivers 352.63 (proprietary, tested) from ubuntu driver manager.

I hope this works for you guys too.

P.S.: As I tested neither of them alone are fixing the problem.

---

### Post by Serge_Malo on 2015-12-15
Hi all,

Thanks for this thread, very helpful!
I was wondering if any of you had been able to use the Thunderbolt of the ROG G751 under Ubuntu?
I have installed Ubuntu 14.04.3 (Kernel 3.19). Everything seems to run Ok, but I can't get the Thunderbolt to work. I suppose I need to install a driver, but I can't find it.
When I run lspci, I see this: 
PCI bridge: Intel Corporation device 157e

I suppose this the Thunderbolt device, but it looks like no driver is loaded for it.

Any ideas are welcome!

Best regards,
Serge

---

### Post by mina.reza on 2016-08-10
[COLOR=#1D2129][FONT=helvetica]Dear ubuntu user/expert[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]**I stoped ubuntu upgrading version from 14.04 to 16.04 in middle**.
 now I have problem in boot repairing on USB, I created .iso file on USB with *Unetbootin *and I can boot my PC with USB but Unfortunatly I can't boot it on my laptop([/FONT][/COLOR] ASUS G751 [COLOR=#1D2129][FONT=helvetica]). 
I am very grateful for any suggestion.

Bests,
mina[/FONT][/COLOR]

---

### Post by turpineric on 2017-06-25
> **Jukka_Alasalmi said:**
> Hi,

By adding the "options snd-hda-intel model=asus-mode5" to the /etc/modprobe.d/alsa-base.conf file and rebooting after that, my headphones are working in the corect jack (the one closest to the front edge of the laptio). I don't have an external mic actually, so I haven't tried that.

Thanks for the info on the ALSA thread! I subscribed there to keep up-to-date on that as well.

I haven't actually tried to configure the gaming specific keys, since so far I have not used them in Windows, either, and am not that familiar with fiddling around with the key bindings, so unfortunately I have no tips on that one.

Unbelievable,IT'S OK FOR ME, it's up and running again. 6 months I waiting that. Thank you thank you very much.

---

### Post by coffeecat on 2017-06-25
Back to sleep, ancient thread.

---


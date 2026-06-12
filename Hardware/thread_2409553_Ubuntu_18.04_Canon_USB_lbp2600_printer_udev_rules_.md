---
title: "Ubuntu 18.04 Canon USB lbp2600 printer udev rules not working"
date: 2019-01-03
forum: Hardware
---

### Post by andreberg on 2019-01-03
I've succesfully installed and have running a Canon LBP6000 printer in Ubuntu 18.04. Install using Canon drivers and following Canon's install guide. Needed to install a few additional libraries, but besides that, no major issues. I used to have this same printer running under 16.04.

The only issue is that the printer only runs when I start the ccpd daemon. And I must do that every time I want to print something. So each time I must enter the following code in Terminal:

```
sudo /etc/init.d/ccpd start
```

I saw on the forum (but alas, cannot find it anymore) that a udev rule could be used to run this script automatically every time the printer was plugged in or switched on. Essentially, I could have a running printer whenever I wanted to, independent if the printer was on before the laptop was booted, or if I turned the printer on after the laptop booted.

After some digging around and reading a lot about how to write udev rules I was able to come up with the following rule:

```
ACTION=="add", KERNEL=="lp1", SUBSYSTEMS=="usb", ATTRS{idProduct}=="271a", ATTRS{idVendor}=="04a9", RUN+="/etc/init.d/ccpd start"

ACTION=="remove", KERNEL=="lp1", SUBSYSTEMS=="usb", ATTRS{idProduct}=="271a", ATTRS{idVendor}=="04a9",RUN+="/etc/init.d/ccpd stop"
```

Tested the rule and would run the script in the end. I tried this with a simple script to make a new directory in my desktop with ```
RUN+="/bin/mkdir /home/[user]/Desktop/test
``` which works nicely. However it refuses to run the script I want to start the ccpd daemon.

As well, the ACTION=="remove" rule does not work at all.

Any help would be appreciated.

Here is the result of: lsusb

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 04f2:b5db Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 017: ID 04a9:271a Canon, Inc. 
Bus 001 Device 002: ID 1a81:1012 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

And this is the result of: udevadm info -ap /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/usbmisc/lp1 (truncated)

```
KERNEL=="lp1"
    SUBSYSTEM=="usbmisc"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0':
    KERNELS=="1-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usblp"
    ATTRS{authorized}=="1"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceClass}=="07"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bInterfaceProtocol}=="02"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{ieee1284_id}=="MFG:Canon;MDL:LBP6000/LBP6018;CMD:CAPT;VER:3.0;CLS:PRINTER;DES:Canon LBP6000/LBP6018"
    ATTRS{supports_autosuspend}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:14.0/usb1/1-2':
    KERNELS=="1-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{authorized}=="1"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bMaxPower}=="2mA"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bmAttributes}=="c0"
    ATTRS{busnum}=="1"
    ATTRS{configuration}==""
    ATTRS{devnum}=="17"
    ATTRS{devpath}=="2"
    ATTRS{idProduct}=="271a"
    ATTRS{idVendor}=="04a9"
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="Canon"
    ATTRS{maxchild}=="0"
    ATTRS{product}=="Canon CAPT USB Device"
    ATTRS{quirks}=="0x0"
    ATTRS{removable}=="removable"
    ATTRS{serial}=="0000B1A97Gna"
    ATTRS{speed}=="480"
    ATTRS{urbnum}=="11"
    ATTRS{version}==" 2.00"

  looking at parent device '/devices/pci0000:00/0000:00:14.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{authorized}=="1"
    ATTRS{authorized_default}=="1"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bMaxPower}=="0mA"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bcdDevice}=="0415"
    ATTRS{bmAttributes}=="e0"
    ATTRS{busnum}=="1"
    ATTRS{configuration}==""
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{idProduct}=="0002"
    ATTRS{idVendor}=="1d6b"
    ATTRS{interface_authorized_default}=="1"
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="Linux 4.15.0-43-generic xhci-hcd"
    ATTRS{maxchild}=="7"
    ATTRS{product}=="xHCI Host Controller"
    ATTRS{quirks}=="0x0"
    ATTRS{removable}=="unknown"
    ATTRS{serial}=="0000:00:14.0"
    ATTRS{speed}=="480"
    ATTRS{urbnum}=="292"
    ATTRS{version}==" 2.00"
```

And finally, this is the result of: udevadm test /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/usbmisc/lp1

```
calling: test
version 237
This program is for debugging only, it does not run any program
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

Load module index
Parsed configuration file /lib/systemd/network/99-default.link
Created link configuration context.
Reading rules file: /lib/udev/rules.d/39-usbmuxd.rules
Reading rules file: /lib/udev/rules.d/40-usb-media-players.rules
Reading rules file: /lib/udev/rules.d/40-usb_modeswitch.rules
Reading rules file: /lib/udev/rules.d/40-vm-hotadd.rules
Reading rules file: /lib/udev/rules.d/50-apport.rules
Reading rules file: /lib/udev/rules.d/50-firmware.rules
Reading rules file: /lib/udev/rules.d/50-udev-default.rules
Reading rules file: /lib/udev/rules.d/55-dm.rules
Reading rules file: /lib/udev/rules.d/55-ippusbxd.rules
Reading rules file: /lib/udev/rules.d/56-hpmud.rules
Reading rules file: /lib/udev/rules.d/60-block.rules
Reading rules file: /lib/udev/rules.d/60-cdrom_id.rules
Reading rules file: /lib/udev/rules.d/60-crda.rules
Reading rules file: /lib/udev/rules.d/60-drm.rules
Reading rules file: /lib/udev/rules.d/60-evdev.rules
Reading rules file: /lib/udev/rules.d/60-input-id.rules
Reading rules file: /lib/udev/rules.d/60-inputattach.rules
Reading rules file: /lib/udev/rules.d/60-libgphoto2-6.rules
Reading rules file: /lib/udev/rules.d/60-libsane1.rules
Reading rules file: /lib/udev/rules.d/60-pcmcia.rules
Reading rules file: /lib/udev/rules.d/60-persistent-alsa.rules
Reading rules file: /lib/udev/rules.d/60-persistent-input.rules
Reading rules file: /lib/udev/rules.d/60-persistent-storage-dm.rules
Reading rules file: /lib/udev/rules.d/60-persistent-storage-tape.rules
Reading rules file: /lib/udev/rules.d/60-persistent-storage.rules
Reading rules file: /lib/udev/rules.d/60-persistent-v4l.rules
Reading rules file: /lib/udev/rules.d/60-sensor.rules
Reading rules file: /lib/udev/rules.d/60-serial.rules
Reading rules file: /lib/udev/rules.d/61-gdm.rules
Reading rules file: /lib/udev/rules.d/61-gnome-settings-daemon-rfkill.rules
Reading rules file: /lib/udev/rules.d/61-persistent-storage-android.rules
Reading rules file: /lib/udev/rules.d/64-btrfs.rules
Reading rules file: /lib/udev/rules.d/64-xorg-xkb.rules
Reading rules file: /lib/udev/rules.d/65-libwacom.rules
Reading rules file: /lib/udev/rules.d/66-snapd-autoimport.rules
Reading rules file: /lib/udev/rules.d/69-cd-sensors.rules
Reading rules file: /lib/udev/rules.d/69-libmtp.rules
Reading rules file: /lib/udev/rules.d/69-wacom.rules
Reading rules file: /lib/udev/rules.d/70-joystick.rules
Reading rules file: /lib/udev/rules.d/70-mouse.rules
Reading rules file: /lib/udev/rules.d/70-power-switch.rules
Reading rules file: /lib/udev/rules.d/70-printers.rules
Reading rules file: /etc/udev/rules.d/70-snap.core.rules
Reading rules file: /lib/udev/rules.d/70-spice-vdagentd.rules
Reading rules file: /lib/udev/rules.d/70-touchpad.rules
Reading rules file: /lib/udev/rules.d/70-u2f.rules
Reading rules file: /lib/udev/rules.d/70-uaccess.rules
Reading rules file: /lib/udev/rules.d/71-power-switch-proliant.rules
Reading rules file: /lib/udev/rules.d/71-seat.rules
Reading rules file: /lib/udev/rules.d/71-u-d-c-gpu-detection.rules
Reading rules file: /lib/udev/rules.d/73-seat-late.rules
Reading rules file: /lib/udev/rules.d/73-special-net-names.rules
Reading rules file: /lib/udev/rules.d/73-usb-net-by-mac.rules
Reading rules file: /lib/udev/rules.d/75-net-description.rules
Reading rules file: /lib/udev/rules.d/75-probe_mtd.rules
Reading rules file: /lib/udev/rules.d/77-mm-cinterion-port-types.rules
Reading rules file: /lib/udev/rules.d/77-mm-dell-port-types.rules
Reading rules file: /lib/udev/rules.d/77-mm-ericsson-mbm.rules
Reading rules file: /lib/udev/rules.d/77-mm-haier-port-types.rules
Reading rules file: /lib/udev/rules.d/77-mm-huawei-net-port-types.rules
Reading rules file: /lib/udev/rules.d/77-mm-longcheer-port-types.rules
Reading rules file: /lib/udev/rules.d/77-mm-mtk-port-types.rules
Reading rules file: /lib/udev/rules.d/77-mm-nokia-port-types.rules
Reading rules file: /lib/udev/rules.d/77-mm-pcmcia-device-blacklist.rules
Reading rules file: /lib/udev/rules.d/77-mm-platform-serial-whitelist.rules
Reading rules file: /lib/udev/rules.d/77-mm-qdl-device-blacklist.rules
Reading rules file: /lib/udev/rules.d/77-mm-simtech-port-types.rules
Reading rules file: /lib/udev/rules.d/77-mm-telit-port-types.rules
Reading rules file: /lib/udev/rules.d/77-mm-usb-device-blacklist.rules
Reading rules file: /lib/udev/rules.d/77-mm-usb-serial-adapters-greylist.rules
Reading rules file: /lib/udev/rules.d/77-mm-x22x-port-types.rules
Reading rules file: /lib/udev/rules.d/77-mm-zte-port-types.rules
Reading rules file: /lib/udev/rules.d/78-graphics-card.rules
Reading rules file: /lib/udev/rules.d/78-sound-card.rules
Reading rules file: /lib/udev/rules.d/80-debian-compat.rules
Reading rules file: /lib/udev/rules.d/80-drivers.rules
Reading rules file: /lib/udev/rules.d/80-ifupdown.rules
Reading rules file: /lib/udev/rules.d/80-iio-sensor-proxy.rules
Reading rules file: /lib/udev/rules.d/80-libinput-device-groups.rules
Reading rules file: /lib/udev/rules.d/80-mm-candidate.rules
Reading rules file: /lib/udev/rules.d/80-net-setup-link.rules
Reading rules file: /lib/udev/rules.d/80-udisks2.rules
Reading rules file: /lib/udev/rules.d/84-nm-drivers.rules
Reading rules file: /lib/udev/rules.d/85-brltty.rules
Reading rules file: /etc/udev/rules.d/85-canon-capt.rules
Reading rules file: /lib/udev/rules.d/85-hdparm.rules
Reading rules file: /lib/udev/rules.d/85-hplj10xx.rules
Reading rules file: /lib/udev/rules.d/85-nm-unmanaged.rules
Reading rules file: /lib/udev/rules.d/85-regulatory.rules
Reading rules file: /lib/udev/rules.d/90-alsa-restore.rules
Reading rules file: /lib/udev/rules.d/90-bolt.rules
Reading rules file: /lib/udev/rules.d/90-console-setup.rules
Reading rules file: /lib/udev/rules.d/90-fwupd-devices.rules
Reading rules file: /lib/udev/rules.d/90-libgpod.rules
Reading rules file: /lib/udev/rules.d/90-libinput-model-quirks.rules
Reading rules file: /lib/udev/rules.d/90-pulseaudio.rules
Reading rules file: /lib/udev/rules.d/95-cd-devices.rules
Reading rules file: /lib/udev/rules.d/95-dm-notify.rules
Reading rules file: /lib/udev/rules.d/95-upower-csr.rules
Reading rules file: /lib/udev/rules.d/95-upower-hid.rules
Reading rules file: /lib/udev/rules.d/95-upower-wup.rules
Reading rules file: /lib/udev/rules.d/97-hid2hci.rules
Reading rules file: /lib/udev/rules.d/99-systemd.rules
rules contain 393216 bytes tokens (32768 * 12 bytes), 36265 bytes strings
28433 strings (240784 bytes), 25160 de-duplicated (207793 bytes), 3274 trie nodes used
GROUP 7 /lib/udev/rules.d/50-udev-default.rules:52
RUN '/etc/init.d/ccpd start' /etc/udev/rules.d/85-canon-capt.rules:1
handling device node '/dev/usb/lp1', devnum=c180:1, mode=0660, uid=0, gid=7
preserve permissions /dev/usb/lp1, 020660, uid=0, gid=7
preserve already existing symlink '/dev/char/180:1' to '../usb/lp1'
.MM_USBIFNUM=00
ACTION=add
DEVNAME=/dev/usb/lp1
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/usbmisc/lp1
MAJOR=180
MINOR=1
SUBSYSTEM=usbmisc
USEC_INITIALIZED=5450123477
run: '/etc/init.d/ccpd start'
Unload module index
Unloaded link configuration context.
```

Thanks

---

### Post by andreberg on 2019-01-03
Finally found the threads. These are

[https://help.ubuntu.com/community/CanonCaptDrv190#UDEV_rules](https://help.ubuntu.com/community/CanonCaptDrv190#UDEV_rules)
[https://ubuntuforums.org/showthread.php?t=1982917&page=5&highlight=udev+rule+usb+printer](https://ubuntuforums.org/showthread.php?t=1982917&page=5&highlight=udev+rule+usb+printer) (post #41)

Both threads suggest that if the rule is not working it could be caused by the system-config-printer-udev package and suggest removing the package altogether.

Tried that but the rules still not work as expected.

---

### Post by andreberg on 2019-01-14
No replies... seems this is not a hot topic... or the printer is too damn old and not worth the hassle!

Well I finally find a workaround and for the sake of those who might find it useful here it is.

I reviewed this page:

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

At the very end the page mentions some Known Issues (64-bit systems; UDEV Rules; Only one CCPD process running after system startup). On the last they suggest inserting this script into the end of /etc/rc.local file

[PHP]
sleep 10 && /etc/init.d/ccpd restart
[/PHP]

The problem in Ubuntu 18.04 is that there is no /etc/rc.local file. Searching for a workaround I stumbled upon the following thread:

[https://askubuntu.com/questions/886620/how-can-i-execute-command-on-startup-rc-local-alternative-on-ubuntu-16-10](https://askubuntu.com/questions/886620/how-can-i-execute-command-on-startup-rc-local-alternative-on-ubuntu-16-10)

This thread suggests the use of systemd given that according to systemd's manpage, if the /etc/rc.local file exists and is executable, it gets pulled automatically into multi-user.target. So following the second solution on the thread I was able to recreate a /etc/rc.local file and copy into it the needed code that restarts the /etc/init.d/ccpd service upon the system boot. This maintains the ccpd daemon up and running allowing to have the usb printer operational either if you turn it on after or before boot, or even if you turn it off/on accidentally, or even if you unplug the usb cable and then plug it back in.

In short these are the steps you must follow to enable the /etc/rc.local file:

1.- Create a service on systemd by

[PHP]
sudo gedit /etc/systemd/system/rc-local.service
[/PHP]

2.- Add the following code into it:

[PHP]
[Unit]Description=/etc/rc.local Compatibility
ConditionPathExists=/etc/rc.local

[Service]
Type=forking
ExecStart=/etc/rc.local start
TimeoutSec=0
StandardOutput=tty
RemainAfterExit=yes
SysVStartPriority=99

[Install] WantedBy=multi-user.target
[/PHP]

In my case most of the code was already there after creating the service, with the exception of the last two lines

[PHP]
[Install] 
WantedBy=multi-user.target
[/PHP]

3.- Create the /etc/rc.local file and make sure its executable with the following code:

[PHP]
sudo chmod +x /etc/rc.local
[/PHP]

Then add the following code into the newly created file:

[PHP]
#!/bin/sh -e#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
[/PHP]

4.- Enable your newly created systemd service:

[PHP]
sudo systemctl enable rc-local
[/PHP]

5.- Start service and check status:

[PHP]
sudo systemctl start rc-local.service
sudo systemctl status rc-local.service
[/PHP]

6.- Finally I added the code to restart the ccpd daemon to the /etc/rc.local file BEFORE the "exit 0" line. So my /etc/rc.local file would look like this:

[PHP]
#!/bin/sh -e#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sleep 10 && /etc/init.d/ccpd restart

exit 0
[/PHP]

And then rebooted.

Hope this helps someone!

---

### Post by affaire on 2019-03-01
I ran into the same problem and after some googling I found this solution on github using systemd.

[https://gist.github.com/akikoskinen/98b18251ca05b152d2df3548d057ef49](https://gist.github.com/akikoskinen/98b18251ca05b152d2df3548d057ef49)

cheers!

---


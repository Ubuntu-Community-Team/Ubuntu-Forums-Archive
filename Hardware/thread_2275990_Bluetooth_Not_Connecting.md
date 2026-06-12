---
title: "Bluetooth Not Connecting"
date: 2015-04-29
forum: Hardware
---

### Post by aaron87 on 2015-04-29
Hi, When I first installed Ubuntu the bluetooth worked great! It connected quickly to my speaker and allowed me to switch my audio output to the speaker on the spot!
However, since the first reboot it has not been working. Sometimes it will detect the device, but when I select it as my audio output it doesn't do anything. It won't let me 'test' the sound and when I close sound settings and reopen it will be deselected. Lately, it hasn't even been detecting my speaker any more. This isn't an issue with the speaker as I am able to see and connect to the device via my laptop(which has ubuntu installed as well) just not from my desktop.

After running a dmesg, I noticed there is a firmware error but googling the error did not produce any useful results to my case.

This bluetooth device is a USB bluetooth adapter called Kinivo BT400
```

dmesg | grep blue
[    4.689639] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0a5c-21e8.hcd failed with error -2

```

---

### Post by jeremy31 on 2015-04-29
```
wget https://www.dropbox.com/s/xgyftdcjkb90qaf/fw-0a5c-21e8.hcd
```
```
sudo cp fw-0a5c-21e8.hcd /lib/firmware/brcm/BCM20702A0-0a5c-21e8.hcd
```
```
sudo modprobe -r btusb
```
```
sudo modprobe btusb
```

Then it should work

---

### Post by aaron87 on 2015-04-30
Thank man! It worked(for now).

---

### Post by jeremy31 on 2015-04-30
If you are using Blueman you may need to ```
pactl load-module module-bluetooth-discover
``` after each boot because of a bug in Blueman that will unload module-bluetooth-discover

---


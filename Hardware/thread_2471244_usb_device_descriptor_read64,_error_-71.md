---
title: "usb device descriptor read/64, error -71"
date: 2022-01-24
forum: Hardware
---

### Post by Syphotellion on 2022-01-24
This seems like a fairly common problem, but none of the solutions I have looked at have yet helped me.

I originally posted this as an "answer" at Ask Ubuntu, since I don't have enough reputation for a "comment".  My answer has since been deleted, and I don't see any better way to get a discussion going about what may or may not be different than my issue.
[https://askubuntu.com/questions/1384002/after-a-recent-system-update-some-usb-devices-are-not-recognised](https://askubuntu.com/questions/1384002/after-a-recent-system-update-some-usb-devices-are-not-recognised)

[HR][/HR]Some possible solutions that haven't yet worked for me.


[LIST=1]
[*]`use_both_schemas=yes` from e.g. [https://urukrama.wordpress.com/2009/01/27/usb-drive-not-recognised-error-71/](https://urukrama.wordpress.com/2009/01/27/usb-drive-not-recognised-error-71/)
[LIST=1]
[*]I don't know, but I suspect that since I see both `read/64` and `read/8`, that it's already trying both?
[/LIST]

[*]"unplug everything and power off" from e.g. [https://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error](https://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error)
[LIST=1]
[*]being a laptop, this was more difficult for me. but it still didn't help
[/LIST]

[*]downgrade the linux kernel.
[LIST=1]
[*]this didn't help me
[/LIST]

[*]downgrade other recent package updates.
[LIST=1]
[*]this may be the next thing i try.
[/LIST]

[*]I contacted Dell support, trying to verify that there was not an actual hardware problem.the laptop is only a few months old, so it is still covered by "basic" warranty.  We ran a hardware diagnostic (Pre-Boot System Assessment) which passed, suggesting that there are no hardware issues.
[/LIST]


----------




Apparently I don't have enough reputation to comment, but I have a similar issue that just started this week.


```

Jan 18 13:48:30 alan-gaming kernel: [    1.439634] usb 3-5: new high-speed USB device number 3 using xhci_hcd
Jan 18 13:48:33 alan-gaming kernel: [    6.695784] usb 3-5: device descriptor read/64, error -71
Jan 18 13:48:38 alan-gaming kernel: [   11.819813] usb 3-5: device descriptor read/64, error -71
Jan 18 13:48:38 alan-gaming kernel: [   12.055610] usb 3-5: new high-speed USB device number 4 using xhci_hcd
Jan 18 13:48:44 alan-gaming kernel: [   17.319806] usb 3-5: device descriptor read/64, error -71
Jan 18 13:48:49 alan-gaming kernel: [   22.443753] usb 3-5: device descriptor read/64, error -71
Jan 18 13:48:49 alan-gaming kernel: [   22.551771] usb usb3-port5: attempt power cycle
Jan 18 13:48:50 alan-gaming kernel: [   23.203619] usb 3-5: new high-speed USB device number 5 using xhci_hcd
Jan 18 13:48:54 alan-gaming kernel: [   27.991643] usb 3-5: device descriptor read/8, error -71
Jan 18 13:48:54 alan-gaming kernel: [   28.120395] usb 3-5: device descriptor read/8, error -71
Jan 18 13:48:55 alan-gaming kernel: [   28.563620] usb 3-5: new high-speed USB device number 6 using xhci_hc

```


In my case, the USB device that has stopped working is my laptop camera.  It was working at least as of 10 January:
```

Jan 10 09:06:45 alan-gaming kernel: [    1.447941] usb 3-5: new high-speed USB device number 3 using xhci_hcd
Jan 10 09:06:45 alan-gaming kernel: [    1.617076] usb 3-5: New USB device found, idVendor=0c45, idProduct=6a09, bcdDevice=82.62
Jan 10 09:06:45 alan-gaming kernel: [    1.617079] usb 3-5: New USB device strings: Mfr=2, Product=1, SerialNumber=0
Jan 10 09:06:45 alan-gaming kernel: [    1.617080] usb 3-5: Product: Integrated_Webcam_HD
Jan 10 09:06:45 alan-gaming kernel: [    1.617081] usb 3-5: Manufacturer: CNFHH52R2034300E33E0

```

I suspect one of these updates from the 17th or 18th may be involved?
```

 Start-Date: 2022-01-17  18:13:22
Commandline: aptdaemon role='role-commit-packages' sender=':1.849'
Upgrade: ubuntu-advantage-tools:amd64 (27.4.2~20.04.1, 27.5~20.04.1), ubuntu-drivers-common:amd64 (1:0.9.0~0.20.04.1, 1:0.9.0~0.20.04.4), linux-firmware:amd64 (1.187.24, 1.187.25)
End-Date: 2022-01-17  18:13:47


Start-Date: 2022-01-18  13:38:52
Commandline: aptdaemon role='role-commit-packages' sender=':1.849'
Install: linux-modules-5.13.0-25-generic:amd64 (5.13.0-25.26~20.04.1, automatic), linux-headers-5.13.0-25-generic:amd64 (5.13.0-25.26~20.04.1, automatic), linux-modules-extra-5.13.0-25-generic:amd64 (5.13.0-25.26~20.04.1, automatic), linux-image-5.13.0-25-generic:amd64 (5.13.0-25.26~20.04.1, automatic), linux-hwe-5.13-headers-5.13.0-25:amd64 (5.13.0-25.26~20.04.1, automatic)
Upgrade: linux-headers-generic-hwe-20.04:amd64 (5.11.0.46.51~20.04.23, 5.13.0.25.26~20.04.12), linux-image-generic-hwe-20.04:amd64 (5.11.0.46.51~20.04.23, 5.13.0.25.26~20.04.12), linux-generic-hwe-20.04:amd64 (5.11.0.46.51~20.04.23, 5.13.0.25.26~20.04.12)
End-Date: 2022-01-18  13:39:26

```


But I've tried downgrading my Kernel (to 5.11.0-43-generic), and that hasn't seemed to help.


There is a lot of _old_ advice about this issue.

[LIST]
[*]`use_both_schemas=yes` from e.g. [https://urukrama.wordpress.com/2009/01/27/usb-drive-not-recognised-error-71/](https://urukrama.wordpress.com/2009/01/27/usb-drive-not-recognised-error-71/)
[LIST]
[*]I don't know, but I suspect that since I see both `read/64` and `read/8`, that it's already trying both?
[/LIST]

[*]"unplug everything and power off" from e.g. [https://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error](https://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error)
[LIST]
[*]this didn't help. being a laptop, this may be harder? I have not yet tried opening up the laptop to disconnect the battery and/or resetting the CMOS.
[/LIST]
[/LIST]


What else can we try?

---

### Post by Syphotellion on 2022-01-26
[LIST=1]
[*]i was able to disable the webcam in the BIOS, and the system started up with no errors -- and no issues / slowness with discovering other USB devices.
[*]after going back into the BIOS and re-enabling the webcam, the system resumed reporting the same USB errors. so the above was not a great long term fix -- i would like to be able to use my webcam.
[/LIST]

---

### Post by florianreech on 2022-02-02
Hello,

I have the same problem on my Dell Precision 3541 on Ubuntu 21.10. I have disabled the webcam in BIOS but this is not a long term fix like you said. The `uname -r` command output is 5.13.0-28-generic. My colleagues have the same computers with the same version and have no problems.

Just wait for an update that can solve the problem ... or a magic trick !

---

### Post by florianreech on 2022-02-15
Problem solved after replace the webcam hardware with the Dell Pro support.

---


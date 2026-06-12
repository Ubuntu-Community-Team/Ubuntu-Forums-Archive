---
title: "Bluetooth rtl8761bu problem."
date: 2024-07-29
forum: Hardware
---

### Post by ffafoz on 2024-07-29
Good afternoon,
USB bluetooth adapter is available.
It is defined like this.

```

[FONT=monospace][COLOR=#18B218][227331.427866] [/COLOR][COLOR=#B26818]usb 1-6: [/COLOR][COLOR=#000000]new full-speed USB device number 6 using xhci_hcd[/COLOR]
[COLOR=#18B218][227331.555046] [/COLOR][COLOR=#B26818]usb 1-6: [/COLOR][COLOR=#000000]New USB device found, idVendor=0bda, idProduct=a729, bcdDevice= 2.00[/COLOR]
[COLOR=#18B218][227331.555049] [/COLOR][COLOR=#B26818]usb 1-6: [/COLOR][COLOR=#000000]New USB device strings: Mfr=1, Product=2, SerialNumber=3[/COLOR]
[COLOR=#18B218][227331.555050] [/COLOR][COLOR=#B26818]usb 1-6: [/COLOR][COLOR=#000000]Product: Bluetooth 5.3 Radio[/COLOR]
[COLOR=#18B218][227331.555052] [/COLOR][COLOR=#B26818]usb 1-6: [/COLOR][COLOR=#000000]Manufacturer: Realtek[/COLOR]
[COLOR=#18B218][227331.555053] [/COLOR][COLOR=#B26818]usb 1-6: [/COLOR][COLOR=#000000]SerialNumber: 00E04C239987[/COLOR]
[COLOR=#18B218][227331.558751] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#000000]hci0: RTL: examining hci_ver=0a hci_rev=000b lmp_ver=0a lmp_subver=8761[/COLOR]
[COLOR=#18B218][227331.559702] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#000000]hci0: RTL: rom_version status=0 version=1[/COLOR]
[COLOR=#18B218][227331.559705] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#000000]hci0: RTL: loading rtl_bt/rtl8761bu_fw.bin[/COLOR]
[COLOR=#18B218][227331.566735] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#000000]hci0: RTL: loading rtl_bt/rtl8761bu_config.bin[/COLOR]
[COLOR=#18B218][227331.566919] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#000000]hci0: RTL: cfg_sz 6, total sz 30210[/COLOR]
[COLOR=#18B218][227331.715847] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#000000]hci0: RTL: fw version 0xdfc6d922[/COLOR]
[COLOR=#18B218][227331.783957] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#000000]MGMT ver 1.22[/COLOR]
[/FONT]
```


From the looks of it seems to be all good, but occasionally there are problems with connecting to various devices. not immediately after booting, but after a while.
In the logs I see these errors

```

[FONT=monospace][COLOR=#18B218][227486.545107] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]hci0: command tx timeout[/COLOR]
[/FONT]
```
or
```

[FONT=monospace][COLOR=#18B218][216024.831536] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 17)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][216098.518685] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 17)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][216522.377837] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 17)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][218276.309116] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 17)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][218600.421766] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 16)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][218697.648804] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 17)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][219297.910319] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 4)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][220067.541670] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 13)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][220339.003401] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 17)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][220903.352551] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 13)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][221088.352450] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 16)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][221689.783685] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 17)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][222477.045898] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 1)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][222961.361939] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 9)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][223447.919058] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 17)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][223750.389957] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 17)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][223842.867789] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 3)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][224247.829183] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 12)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][224654.432997] [/COLOR][COLOR=#B26818]Bluetooth: [/COLOR][COLOR=#B21818]Unexpected start frame (len 9)[/COLOR]
[/FONT]
```


How fix this ?
OS

```

[FONT=monospace]DISTRIB_RELEASE=24.04[/FONT]
[FONT=monospace][COLOR=#000000]Kernel : 6.8.0-39-generic[/COLOR]
[/FONT]
```

---

### Post by currentshaft on 2024-07-29
Are you using wireless (wifi)? If so, which channel are you on?

---

### Post by ffafoz on 2024-07-29
I'm sorry, but what does this have to do with Wi-Fi?
I'm using a USB bluetooth adapter.
I don't use Wifi on this pc, everything is connected by cable.

---

### Post by #&amp;thj^% on 2024-07-29
Please see if this has any promise: [https://fosspost.org/fix-bluetooth-rtl8761b-problem-on-linux-ubuntu-22-04](https://fosspost.org/fix-bluetooth-rtl8761b-problem-on-linux-ubuntu-22-04)

---

### Post by ffafoz on 2024-07-29
> **1fallen said:**
> Please see if this has any promise: [https://fosspost.org/fix-bluetooth-rtl8761b-problem-on-linux-ubuntu-22-04](https://fosspost.org/fix-bluetooth-rtl8761b-problem-on-linux-ubuntu-22-04)
nope, sorry. 
this is diferent problem.
This person has a problem with drivers, I do not have such a problem, I have for some reason it falls out intermittently here in timeout.

---

### Post by #&amp;thj^% on 2024-07-29
So you feel your driver is ok?
Anywho will you show this:
```
journalctl -b | grep -i bluetooth
```

---


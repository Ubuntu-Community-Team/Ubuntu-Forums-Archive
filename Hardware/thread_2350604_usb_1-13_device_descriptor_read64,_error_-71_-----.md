---
title: "usb 1-13: device descriptor read/64, error -71 -----&gt;Lost connection to Canon printer"
date: 2017-01-25
forum: Hardware
---

### Post by sunbear-c22 on 2017-01-25
I am unable to connect to my printer from Ubuntu 16.04. My printer was previously working. 

Don't know what caused the lost connection. Found this mesg when using system_setting/printers to re-connect to printer:
[I]CUPS server error
There was an error during the CUPS operation: 'failed to connect to server'.
OS cannot find printer on local host.[/I]

I ran the following commands to investigate if I had any boot up error and discover I have an issue relating to my usb.
$ dmesg -d | grep error
[    1.991080 <    0.075392>] usb 1-13: device descriptor read/64, error -71
[    2.206916 <    0.215836>] usb 1-13: device descriptor read/64, error -71
[    2.750659 <    0.035643>] usb 1-13: device descriptor read/64, error -71
[    2.966844 <    0.171468>] usb 1-13: device descriptor read/64, error -71
[    3.750627 <    0.043891>] usb 1-13: device not accepting address 8, error -71
[    4.430689 <    0.203945>] usb 1-13: device not accepting address 10, error -71
[    5.028502 <    0.244193>] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro

I have tried connecting the printer to different usb port but to no avail.
Cairo-dock indicated it connection to printer but unable to mount.

Can some advice me how to resolve my printer/usb problem?

---


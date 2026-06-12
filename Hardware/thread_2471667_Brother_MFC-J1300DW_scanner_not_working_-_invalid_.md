---
title: "Brother MFC-J1300DW scanner not working - invalid argument"
date: 2022-02-06
forum: Hardware
---

### Post by oygle on 2022-02-06
After finally getting this Brother MFC-J1300DW to print a page ( see [https://ubuntuforums.org/showthread.php?t=2471590](https://ubuntuforums.org/showthread.php?t=2471590) ) , now the scanner does not work. Tried three different tools for scanning, either device not found, unable to connect to scanner, or 'inavlid argument'. The tools were all SANE based.

There is a post 8 years ago at [https://askubuntu.com/questions/389636/invalid-argument-brother-scanner-not-working-after-upgrade-brscan2-driver](https://askubuntu.com/questions/389636/invalid-argument-brother-scanner-not-working-after-upgrade-brscan2-driver) , and have tried a few of the suggestions to no avail. This statement ..

> 
 1   The error **Invalid argument** is not a argument problem, but is a write access problem.
 2   The other problem is that the bus and dev number are wrong from the scanimage error.


could be a solution for my situation, as

```
lsusb
```

> Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 008: ID 0cf3:0036 Qualcomm Atheros Communications 
Bus 001 Device 005: ID 0c45:670b Microdia 
Bus 001 Device 004: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 013: ID 04f9:040b Brother Industries, Ltd 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 011: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
scanimage -L
```

> device `brother4:bus3;dev1' is a Brother MFC-J1300DW USB scanner
device `escl:[http://127.0.0.1:60001](http://127.0.0.1:60001)' is a ESCL MFC-J1300DW flatbed scanner

One says bus 1 and device 13, the other says bus 3 and device 1

Now, this statement > You can use the following script to update the permissions for the scanner. and the code ..

```
lsusb | grep -i brother | sed 's/://' | awk '{printf "/dev/bus/usb/%s/%s", $2,$4}' | xargs -i -t sudo chmod 666 "{}"
```

If I modify the code to suit , is that code **SAFE** to use ?

---

### Post by brian_p on 2022-02-06
I haven't any intention of tackling this in the context of Brother drivers and assume you are using Ubuntu 20.04.

 [list]Go to [https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan). Note that your scanner is supported.[/list]
  [list]Move on to [https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/](https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/).[/list]
  [list]Download and install ipp-usb and sane-airscan.[/list]
 [list]Disconnect and reconnect to USB.[/list]
 Give ```
scanimage -L
```

---

### Post by oygle on 2022-02-06
@brian_p , thanks

I downloaded and installed those two debs, then

```
scanimage -L
```

> device `brother4:bus3;dev5' is a Brother MFC-J1300DW USB scanner
device `escl:[http://127.0.0.1:60000](http://127.0.0.1:60000)' is a ESCL MFC-J1300DW flatbed scanner
device `airscan:e0:MFC-J1300DW' is a eSCL MFC-J1300DW ip=127.0.0.1

Tried scanning, used 3 different GUI's plus some terminal commands, but none of them worked. Same error message. Even rebooted and tried all that again, no scanning worked, same messages.

Thanks for your help though. I may either:

* Full backup/wipe 20.04 and install latest Kubuntu
OR
* Uninstall the brother drivers, hook up a CAT6 cable, and reinstall the Brother drivers and use the network/LAN.

---

### Post by brian_p on 2022-02-06
Can you scan with ```
simple-scan "airscan:e0:MFC-J1300DW"
``` or ```
xsane "airscan:e0:MFC-J1300DW"
```

---

### Post by oygle on 2022-02-06
Thanks for your reply. Tried both of those commands. 

The first gave a > Failed to scan. Error communicating with scanner.

and the second gave a > Failed to open device 'airscan:e0:MFC-J1300DW':  Error during device I/O

---

### Post by brian_p on 2022-02-06
ipp-usb and sane airscan are functioning corrrectly because scanimage gives an output. You also have permission to access the USB bus, otherwise there wouldn't have been any output from scanimage -L.

Have you tried switching the device off and on, changing USB port and rebooting?

---

### Post by oygle on 2022-02-06
> **brian_p said:**
> Have you tried switching the device off and on, changing USB port and rebooting?

Yes, tried all that, many times. Even changed leads, change usb from a 3.0 port to a 2.0 port, off the hub, on the hub.

Now I know where people get the phrase

> Oh **Brother** from.

---

### Post by oygle on 2022-02-06
It's working now, printer and scanner. Stay clear of Brother printer drivers, see [https://pastebin.com/gU5f01Ky](https://pastebin.com/gU5f01Ky)

---

### Post by him610 on 2022-02-06
From post #3
> device `brother4:bus3;dev5' is a Brother MFC-J1300DW USB scanner
device `escl:[http://127.0.0.1:60000](http://127.0.0.1:60000)' is a ESCL MFC-J1300DW flatbed scanner
device `airscan:e0:MFC-J1300DW' is a eSCL MFC-J1300DW ip=127.0.0.1

You have the same device connected to your machine three different ways. You might have a better chance of connecting in the future if you would only connect using one method.

---

### Post by brian_p on 2022-02-07
> **him610 said:**
> 

You have the same device connected to your machine three different ways. You might have a better chance of connecting in the future if you would only connect using one method.

Unwanted or non-working SANE drivers (for example, brother4 and escl) may be commented out in */etc/sane.d/dll.conf*.

---

### Post by kurt18947 on 2022-02-07
> **oygle said:**
> It's working now, printer and scanner. Stay clear of Brother printer drivers, see [https://pastebin.com/gU5f01Ky](https://pastebin.com/gU5f01Ky)

I've had pretty good luck with Brother drivers but I suspect that using a mix of Brother drivers and 'driverless' drivers (if that's the correct term) cause problems. The problem I had with a new Brother MFC-J4535DW using the auto installed drivers was that the document feeder for the scanner wasn't seen and the manual/bypass paper feed on the back didn't show up. It isn't easy to discourage the automatic driver installation upon a restart.

---

### Post by him610 on 2022-02-07
> Stay clear of Brother printer drivers
I totally disagree with that statement. The Brother drivers are not the problem, it is probably operator headspace.
I have a Brother MFC-7360N (a little older than yours) that has only used Brother drivers with all functions (print, copy, scan, fax transmit & receive) operational. Learned a long time ago to avoid USB connections to printer as computer USB ports tend to wander at the least convenient times - like when one needs to print something urgently.
Glad you got your print and scan capability back. Now, go print;)

---


---
title: "Cinergy DVB-T Stick, ID 187f:0600, no data from NIT(actual)"
date: 2015-01-12
forum: Hardware
---

### Post by padremayi on 2015-01-12
I have a Terratec, ID 187f:0600 Siano Mobile Silicon, USB dongle. My device is recognized by the system but I have a problem with the channels.
The frequencies are ok, with another device I can see all channels.
Please read all my post for any help ;)

At first, I used this guide:
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

After that "dmesg" showed that system was searching for "isdbt_rio.inp" firmware. If I use that firmware from [http://linuxtv.org](http://linuxtv.org), "w_scan" shows me an error, it says that my dongle can't search for TERRESTRIAL.

So, for using smsmdtv mode "DVB-T" as the default option, I forced the kernel module in this way:

```
echo "options smsmdtv default_mode=0" | sudo tee /etc/modprobe.d/smsmdtv.conf 

```After that system searches for "dvb_rio.inp", good ;-)

dmesg:

```
[ 1327.312795] usb 1-3: new high-speed USB device number 4 using ehci-pci
[ 1327.446103] usb 1-3: New USB device found, idVendor=187f, idProduct=0600
[ 1327.446121] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1327.446130] usb 1-3: Product: MDTV Receiver
[ 1327.446138] usb 1-3: Manufacturer: MDTV Receiver
[ 1327.451833] usb 1-3: Direct firmware load failed with error -2
[ 1327.451849] usb 1-3: Falling back to user helper
[ 1327.456026] smscore_load_firmware_from_file: line: 1168: failed to open firmware file "dvb_rio.inp"
[ 1327.456535] DVB: registering new adapter (Siano Rio Digital Receiver)
[ 1327.457351] usb 1-3: DVB: registering adapter 0 frontend 0 (Siano Mobile Digital MDTV Receiver)...

```I used "dvb_rio.inp" from my Windows installation. Now I have this output from "lsusb":

```
Bus 002 Device 002: ID 0402:7675 ALi Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0489:e03c Foxconn / Hon Hai 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 187f:0600 Siano Mobile Silicon 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```dmesg:

```
[ 1390.167433] usb 1-3: new high-speed USB device number 5 using ehci-pci
[ 1390.300895] usb 1-3: New USB device found, idVendor=187f, idProduct=0600
[ 1390.300913] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1390.300922] usb 1-3: Product: MDTV Receiver
[ 1390.300930] usb 1-3: Manufacturer: MDTV Receiver
[ 1390.776240] DVB: registering new adapter (Siano Rio Digital Receiver)
[ 1390.777275] usb 1-3: DVB: registering adapter 0 frontend 0 (Siano Mobile Digital MDTV Receiver)...

```lsmod | grep sms:

```
smsdvb                 27513  0 
dvb_core              125880  1 smsdvb
smsusb                 17819  0 
smsmdtv                53748  2 smsdvb,smsusb
rc_core                27389  1 smsmdtv

```Finally I can scan and tune with a specific frequency but I can't obtain services from multiplexes.

"w_scan -c IT" output:

```
w_scan version 20130331 (compiled for DVB API 5.10)
using settings for ITALY
DVB aerial
DVB-T Europe
scan type TERRESTRIAL, channellist 4
output format vdr-2.0
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
    /dev/dvb/adapter0/frontend0 -> TERRESTRIAL "Siano Mobile Digital MDTV Receiver": good :-)
Using TERRESTRIAL frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.a
frontend 'Siano Mobile Digital MDTV Receiver' supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
FREQ (44.25MHz ... 867.25MHz)
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
Scanning 7MHz frequencies...
177500: (time: 00:00) (time: 00:01) signal ok:
    QAM_AUTO f = 177500 kHz I999B7C999D999T999G999Y999
Info: no data from NIT(actual)
184500: (time: 00:15) 
191500: (time: 00:18) (time: 00:19) signal ok:
    QAM_AUTO f = 191500 kHz I999B7C999D999T999G999Y999
Info: no data from NIT(actual)
198500: (time: 00:33) 
205500: (time: 00:36)
...
...

```I created a file named "frequency" with this content for doing a test:

```
# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy

T 177500000 7MHz 2/3 NONE QAM64 8k 1/8 NONE # MUX-B Rai
T 698000000 8MHz 2/3 NONE QAM64 8k 1/8 NONE # Mediaset 1

```and when I launch "dvbscan frequency" I obtain:

```
Unable to query frontend status
```

With the command "scan frequency" I obtain:
 
```
scanning frequency
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 177500000 1 2 9 3 1 2 0
initial transponder 698000000 0 2 9 3 1 2 0
>>> tune to: 177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 698000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
dumping lists (0 services)
Done.
```

With "dvbv5-scan frequency":
 
```
ERROR key/value without a channel group while parsing line 3 of frequency

```I tried to insert these options in /etc/modprobe.d/options:

```
options smsdvb force_lna_activation=1
options smsusb force_lna_activation=1
options dvb_rio force_lna_activation=1

```to force Low Noise Amplifier but nothing changed.

Kaffeine is tuned with many frequency (Light green led) but can't receive channels. The same with TvHeadend that doesn't obtain services for multiplexes (but the signal is ok).

Do you have any advice? Thanks ;)

---

### Post by padremayi on 2015-01-14
[FONT=arial]Hi to all,[/FONT]

[FONT=arial]I have this output from tzap when trying to scan a frequency that I know to work:[/FONT]

```
[FONT=arial]Version: 5.10   FE_CAN { DVB-T }[/FONT]
[FONT=arial]tuning to 698000000 Hz[/FONT]
[FONT=arial]video pid 0x0654, audio pid 0x0655[/FONT]
[FONT=arial]status 00 | signal 0000 | snr 0000 | ber 00000000 | unc 00000000 |[/FONT]
[FONT=arial]status 1f | signal 0000 | snr 0104 | ber 00000000 | unc 00000000 | FE_HAS_LOCK[/FONT]
[FONT=arial]status 1f | signal 0000 | snr 0104 | ber 00000000 | unc 00000000 | FE_HAS_LOCK[/FONT]
[FONT=arial]status 1f | signal 0000 | snr 0104 | ber 00000000 | unc 00000000 | FE_HAS_LOCK[/FONT]
[FONT=arial]status 1f | signal 0000 | snr 0104 | ber 00000000 | unc 00000000 | FE_HAS_LOCK[/FONT]
[FONT=arial]status 1f | signal 0000 | snr 0104 | ber 00000000 | unc 00000000 | FE_HAS_LOCK[/FONT]
[FONT=arial]...[/FONT]
[FONT=arial]...[/FONT]
```

[FONT=arial]and I can't receive the channel (no video, no audio, no service from multiplex).[/FONT]

[FONT=arial]Maybe a demux problem?[/FONT]

[FONT=arial]Ubuntu 14.04.1 LTS[/FONT]

[FONT=arial]Thanks for any help

[/FONT]

---

### Post by padremayi on 2015-02-04
Ok I found a solution, we need to force mode 4, not 0.
Both are for DVB-T but with difference:


options smsmdtv default_mode=**4**

---

### Post by duderich on 2015-02-15
Hi,
usind Xubuntu 14.04 for me the TerraTec 145258 Cinergy DVB-T Stick worked without installing V4L. I wasnt able to install V4L, a lot of errors...

Other solution: Just downloaded the driver dvb_rio.inp from [http://ww.minidvblinux.de/bug/view.php?id=174&nbn=1.]("http://ww.minidvblinux.de/bug/view.php?id=174&nbn=1.") and copied them to /lib/firmware.

Then the already known modification
```
echo "options smsmdtv default_mode=4" | sudo tee /etc/modprobe.d/smsmdtv.conf
```

TV is running!

Cheers!

---


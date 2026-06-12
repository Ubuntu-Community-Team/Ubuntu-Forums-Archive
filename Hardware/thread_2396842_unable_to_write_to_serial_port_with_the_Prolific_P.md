---
title: "unable to write to serial port with the Prolific PL2303 USB-Serial adapter on 18.04"
date: 2018-07-21
forum: Hardware
---

### Post by akos.maroy on 2018-07-21
Hi,

I'm unable to write to the serial port when using a Prolific PL2303 USB-Serial adapter. I tried three USB-Serial adapters, two of this type and a third one, and for both PL2303 adapters, the effect is the same: I can connect to the serial port using minicom or kermit, I see the input from the serial port, but I cannot write to it. this is also shown by the adapter, which has a built-in LED which would light up when sending data, and it never lights up. the PL2303 shows up a /dev/ttyUSB0, while the other adapter that works shows up as /dev/ttyACM0

some additional info:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04 LTS
Release:	18.04
Codename:	bionic
$ lsmod | grep pl2303
pl2303                 20480  1
usbserial              45056  3 pl2303
$ statserial /dev/ttyUSB0
Device: /dev/ttyUSB0

Signal  Pin  Pin  Direction  Status  Full
Name    (25) (9)  (computer)         Name
-----   ---  ---  ---------  ------  -----
FG       1    -      -           -   Frame Ground
TxD      2    3      out         -   Transmit Data
RxD      3    2      in          -   Receive  Data
RTS      4    7      out         1   Request To Send
CTS      5    8      in          0   Clear To Send
DSR      6    6      in          0   Data Set Ready
GND      7    5      -           -   Signal Ground
DCD      8    1      in          0   Data Carrier Detect
DTR     20    4      out         1   Data Terminal Ready
RI      22    9      in          0   Ring Indicator

```

I wonder what I'm doing wrong, and how to make writing work on these USB-Serial adapters.


Akos

---

### Post by kazakore on 2018-07-21
I was trying to use this exact same device earlier today (or at least that's the name reported by dmesg) and thought I was doing something wrong as I'd never used minicom before. In the end I dug out the work Doze machine and managed to get it working on that in barely seconds! Just tried again and still can't get comms working. On top of that when it's connected my mouse cursor becomes all jerky and horrible so something doesn't seem quite right...

---

### Post by kazakore on 2018-07-22
Back at work and just tried again, this time using Putty as it's a program I know.

I was about to give up as still not working after having pressed Esc a fair number of time (there's no handshaking and this system expects to receive ESC to open the session) and tried alternating Enter with it and it came alive (although I missed the username prompt.)

So the unit does work under Ubuntu (Studio) 18.04 and I would expect you should be able to get it to work with minicom as well.

On connection of the device the cursor became a little unresponsive/jerky again but then again when I was on the Doze machine the touchpad did also keep on seeming to stop working. That laptop is a total POS though and at first I assumed that was why, but now think it must be related to this device. Not just a Linux issue anyway...

---

### Post by jeremy31 on 2018-07-22
See if you are part of the dialout group as that is normally needed

---

### Post by akos.maroy on 2018-07-22
> **jeremy31 said:**
> See if you are part of the dialout group as that is normally needed

naturally I am. if I wouldn't, I couldn't have opened /dev/ttyUSB0 or /dev/ttyACM0 in the first place

---


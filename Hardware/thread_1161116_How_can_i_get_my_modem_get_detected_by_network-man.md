---
title: "How can i get my modem get detected by network-manager?"
date: 2009-05-16
forum: Hardware
---

### Post by filipe_aguiar on 2009-05-16
Yesterday i bought a **onda msa405hs** 3g modem and with some effort i can connect to the internet without any problems. But i can **only** connect using the terminal and wvdial (or pon).

The network-manager doesn't detect the modem at all. I created 2 files for hall detection:

*/etc/udev/rules.d/45-onda-msa405hs.rules*
```

ACTION!="add", GOTO="ONDA_End"
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", RUN+="/sbin/tim-web"
LABEL="ONDA_End"

```

and

*/usr/share/hal/fdi/preprobe/20thirdparty/10-onda-msa405hs.fdi*
```

<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
    <match key="usb.vendor_id" int="0x19d2"> <!-- ONDA -->
      <match key="usb.product_id" int="0x2000"> <!-- MSA405HS -->
        <merge key="info.ignore" type="bool">true</merge>
      </match>
    </match>
    <match key="serial.device" string="/dev/ttyUSB3">
        <append key="info.capabilities" type="strlist">modem</append>
        <append key="modem.command_sets" type="strlist">GSM-07.07</append>
        <append key="modem.command_sets" type="strlist">GSM-07.05</append>
    </match>
  </device>
</deviceinfo>

```

The */etc/udev/rules.d/45-onda-msa405hs.rules* works fine, when i plug the modem it runs the tim-web script that changes the modem mode using usb_modeswitch.

But then my network-manager doesn't detect the modem even when i can use it to connect normaly.

I'm forgotting something? Is anithing wrong with my configurations?

I would apreciate some help. And thanks in advance.

P.S. Sorry for my bad english, i'm not very good at writting.

---

### Post by GeorgeVita on 2009-05-16
Hi **filipe_aguiar**,
in your example, the /etc/udev/rules.d/45-onda-msa405hs.rules file will run after the **19d2 : 2000** USB peripheral attached. It will run the usb_modeswitch and change the **19d2 : 2000** to something else like **19d2 : 0031** or **19d2 : 0015** or even **19d2 : 0001**

You can find the exact productID using **lsusb**

Then a small "trim" to the .fdi will be used to finalise your trying!

Regards,
George

---


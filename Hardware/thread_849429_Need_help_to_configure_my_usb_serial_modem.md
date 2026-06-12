---
title: "Need help to configure my usb serial modem"
date: 2008-07-04
forum: Hardware
---

### Post by knowsath on 2008-07-04
I am new to Linux.Recently I tried Ubuntu.:)but failed to get connect my huawei ETS 2288 modem.:confused:I did a lot of google and forum search,tried a lot of guides with no improvement.can anybody help  me.as far i understand my problem is in usb to serial cable.
which is detected in my xp as multiport USB 3410 (Texas Instrument)and workig well.
when i issue dmesg command It shows me as follows:
sathik@F1:~$ dmesg
[  527.950072] usb 1-1: USB disconnect, address 5
[  533.882657] usb 1-1: new full speed USB device using uhci_hcd and address 6
[  534.076628] usb 1-1: configuration #1 chosen from 1 choice
[  534.080566] ti_usb_3410_5052: probe of 1-1:1.0 failed with error -5

Advance thanks  for anybody who really want help me

---

### Post by knowsath on 2008-07-04
My Ubuntu version is 8.0 LTS (Hardy)
kernal 2.6.24

Do i need a  patch and compile new kernal to support this cable?
Already I tried hotplug script ti_usb_3410_5420 .but no use.
I need this message should be shown when issu "dmesg" command. 
[  160.992574] usb 1-2: TI USB 3410 1 port adapter converter now attached to ttyUSB0
How can I get this attached?

---

### Post by knowsath on 2008-07-04
[COLOR="Red"]**Please Anybody say a word of help.**[/COLOR]
I thing the line in above dmesg output
[ 534.076628] usb 1-1: configuration #1 chosen from 1 choice
should be
[  160.974571] usb 1-2: configuration #1 chosen from 2 choices 
like this
can any body explain  this line better

---

### Post by knowsath on 2008-07-04
:(:(:(:(:(:confused:

---

### Post by smartboy08 on 2008-11-29
How it can be installed on Ubuntu 8.10?

---


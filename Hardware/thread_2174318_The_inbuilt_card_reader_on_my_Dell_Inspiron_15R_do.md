---
title: "The inbuilt card reader on my Dell Inspiron 15R does not recognize my microSD card."
date: 2013-09-13
forum: Hardware
---

### Post by rkarulkar94 on 2013-09-13
The MicroSD card is in a PNY adapter, and is in working condition. I plug it into the reader and nothing happens. Is this a software or hardware problem? How should I fix it?
EDIT: I'm using 13.04 64 bit.

---

### Post by scbingham on 2013-09-14
Is the inbuilt card reader recognised by the system?

From terminal, type lsusb, without the sd card inserted.

For example, mine shows:
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader

When I had 12.04 32bit installed, my reader wasn't detected. When I installed 12.04 64bit, it was.

If your reader is detected, at least you can rule that out as an issue & then look at the sd card or adapter.

BTW, you haven't mentioned your Ubuntu version, which may help others help you.

---

### Post by rkarulkar94 on 2013-09-14
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:648d Microdia 
Bus 002 Device 003: ID 8087:07da Intel Corp

This is the entire output. Maybe my card reader is not Realtek?

---

### Post by rkarulkar94 on 2013-09-14
I checked, the card reader is in fact realtek.

---

### Post by scbingham on 2013-09-14
A quick google reveals there have been bugs with some Realtek card readers, that appear to have been fixed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1196816](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1196816)

If you're running a later version of Ubuntu (you still haven't said), then the problem may be with your sd card.
If so, have you tried it in another reader? Have you tried using disk utility? What format is the sd card?

---

### Post by rkarulkar94 on 2013-09-14
I'm sorry, I edited the main post, I'm using 13.04 64bit. My microsd card works fine in my phone. Can it be an issue with the SD card adapter? The problem I have, is that nothing happens after I insert the card.

---

### Post by scbingham on 2013-09-14
Interestingly, I just tried my phone micro sd card in an adapter in my inbuilt card reader & it's not detected. I also tried in an external usb card reader, both in an adapter & not. Neither was detected.
Mounting my phone as a usb device allows me to read/write to the sd card, so does Airdroid.

Seems odd as I've accessed it directly in the past. Unfortunately, I have no answers for you, except access that sd card via your phone.

Sorry I can't be of help. Maybe someone else can shed some light.

---

### Post by rkarulkar94 on 2013-09-14
So basically, what you're saying is that it's a problem reading a microSD, not a hardware problem?

---

### Post by scbingham on 2013-09-14
Sort of. Unfortunately I don't have another card to hand to try at the moment. Frustrating.

I have read cards directly before.

---

### Post by rkarulkar94 on 2013-09-14
I'm trying to use the lsusb to give me details about the device ID 0bda:0129 on bus 001. How can I do that with lsusb -s? I can't figure out the exact way to input the command.

---

### Post by scbingham on 2013-09-14
I'm not sure what details you're looking for. Disk utility gives some details of devices, including card readers.

lsusb list details of the usb bus & lists devices connected to it. Type man lsusb in the terminal.

---

### Post by rkarulkar94 on 2013-09-14
I cannot figure out what this is. This is one of the outputs of lsusb.

Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp.

---

### Post by scbingham on 2013-09-14
Not sure what just happened to my reply.
Anyway,

I'm not sure what details you're looking for. Disk utility will give details of devices, including card readers.
lsusb gives details of the usb bus & lists devices connected to it but that's about it. Type man lsusb in the terminal.

---

### Post by rkarulkar94 on 2013-09-14
The disk utility does not show anything other than my HDD, CD Drive, something that says Generic USB2.0-crw. Could that be the card reader? I was worried that the card reader was broken.

---

### Post by scbingham on 2013-09-14
Possibly. Mine is listed under Peripheral Devices as a Generic Card reader & clicking on it gives some info.

As for proving your card reader, maybe try another card?

---

### Post by rkarulkar94 on 2013-09-14
I don't have a full size SD card that can work without an adapter. Only the microSD in question with an adapter. The card works fine in my phone and when I connect the phone to the computer.

---

### Post by scbingham on 2013-09-14
At least it's usable, even if not in an ideal way. I just tried my micro sd in another adapter & it still isn't read.

Maybe someone with more experience can shed some light for you.

---


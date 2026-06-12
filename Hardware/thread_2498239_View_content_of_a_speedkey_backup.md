---
title: "View content of a speedkey backup"
date: 2024-06-05
forum: Hardware
---

### Post by paulouxps3 on 2024-06-05
Hello, 

I have an old machine (not a normal computer, it is a machine used in agriculture) which uses a "Speedkey backup adapter" as a backup. It is useful when there is a power outrage and we need to upload back the data into the machine.

For a project, I need to see the contents of this backup speedkey and the goal is to be able to write data into it in order to upload other data in the machine.

The problem is the following : the machine is old and the speedkey backup as an "adapter" because it is a DB25 (VGA with 25 pins). I bought an DB-25 to USB but I see nothing when I connect it to a computer.
I tried to connect it to a computer running Windows 10 and to a computer running Ubuntu 24.04 LTS. I see nothing in the file explorer or in the "disk" application.

By the way, I have no idea of what a "speedkey" is.

I wonder if anybody know this type of hardware. Maybe the cheap adapter DB-25 to USB is only a 1 way ? I don't know if it is possible.

Any help would be appreciated because we need this machine to work and replacing it is very very expensive <3 .
I can give you more details if needed or if you don't understand everything (English isn't my native language)

---

### Post by currentshaft on 2024-06-05
I know nothing about Speedkey, but the DB-25 connector you'd described might be used for a serial connection - not VGA.

Try running the following commands with the cable connected:

sudo apt install minicom
sudo minicom -D /dev/ttyUSB0

Here's more information: [https://en.wikipedia.org/wiki/RS-232](https://en.wikipedia.org/wiki/RS-232)

---

### Post by him610 on 2024-06-05
> DB-25
A few decades ago computers came with a DB-25 serial (RS-232) connection, and a DB-25 parallel (IEEE-1284) connection. The physical difference was that one connection had pins and the other had sockets - I don't recall which was which though. 
The DB-25 serial was replaced by a DB-9 serial which was mostly replaced by USB. There are still some external devices that use the DB-9 serial port.
The DB-25 parallel, used to connect to printers, was replaced by USB.

---

### Post by Holger_Gehrke on 2024-06-06
Neither parallel nor serial port included pins for supplying power. So unless your Speedkey has batteries or some other power supply, it has to get it's power through that connector, which makes me think it's at best a non-standard variant if not a completely proprietary connection. Just because it's a well known connector doesn't mean it carries the signals you'd expect. This is probably going to become a major reverse engineering job if you try to go ahead with it.

Holger

---

### Post by paulouxps3 on 2024-06-06
Thank you currentshaft for your answer ! 
I ran the command but nothing append and I have an error because dev/ttyUSB0 is not found. I checked the dev folder and nothing changes hen I connect or disconnect the cable :/

---

### Post by paulouxps3 on 2024-06-06
It can be a proprietary connection because it was an expensive adapter from the company.

I found on the french Wikipedia page ([https://fr.wikipedia.org/wiki/RS-232#M%C3%A9canique](https://fr.wikipedia.org/wiki/RS-232#M%C3%A9canique)) that pin 9 and 10 can be used to carry power. I also found this information on [https://www.aggsoft.com/rs232-pinout-cable/serial-cable-connections.htm](https://www.aggsoft.com/rs232-pinout-cable/serial-cable-connections.htm).

Thank you for your response and I don't really know what to try next... Maybe call the company that sell the speedkey backup adapter ?

---

### Post by currentshaft on 2024-06-06
> **paulouxps3 said:**
> Thank you currentshaft for your answer ! 
I ran the command but nothing append and I have an error because dev/ttyUSB0 is not found. I checked the dev folder and nothing changes hen I connect or disconnect the cable :/

Run "sudo dmesg" when you connect the cable, it might be showing up as a different device in /dev/

---

### Post by paulouxps3 on 2024-06-07
Thank you ! I have the following result :

[  611.785085] usb 1-2: new full-speed USB device number 7 using xhci_hcd
[  611.912416] usb 1-2: New USB device found, idVendor=1a86, idProduct=7584, bcdDevice= 2.54
[  611.912427] usb 1-2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[  611.912431] usb 1-2: Product: USB2.0-Print 

I don't really know what does it mean...

---

### Post by currentshaft on 2024-06-07
Interesting, those IDs come back to a "QinHeng Electronics  HID-based serial adapter"

No additional lines like "now attached to ttyUSB0"?

Do you see any similar devices in /dev like "/dev/ttyACM0"?

"ls -ltr /dev" will list the latest attached device names.

---

### Post by paulouxps3 on 2024-06-08
There is no additional information when I run the command "sudo dmesg".

Moreover, I see nothing changing with "ls -ltr /dev". With or without the cable plugged.
And no, I don't see something like "/dev/ttyACM0" like it would do when I connect an Arduino for example.

Thank you very much for your help but I think I will give up. It's frustrating because this plug is the only thing that blocks the entire project.
Thank you again :)

---


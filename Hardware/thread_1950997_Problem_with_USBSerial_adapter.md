---
title: "Problem with USB/Serial adapter"
date: 2012-04-01
forum: Hardware
---

### Post by wbosher on 2012-04-01
[SIZE=3][FONT=Calibri]Hi,[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I have recently set up my USB to serial connection to log into Cisco switches/Routers. When in Putty or Minicom, I am getting strange characters showing up and cannot read anything.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I understand that this is often cause by the incorrect speed setting, but I have confirmed this is correct - speed 9600 8N1[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I am able to Telnet to the devices, so not an issue with Putty - I suspect problem is with the USB/Serial connection, although it works fine from Windows so rollover cable/adapter must be ok.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I have entered the following commands:[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]sudo modprobe usbserial vendor=0×*** product=0×*** (I didn&#8217;t actually use asterisks) [/FONT][/SIZE]
 
 
[SIZE=3][FONT=Calibri]Ran &#8220;dmesg&#8221; again and lines similar like this, it appears to be set up ok :[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]usbserial_generic 1-1:1.0: generic converter detected[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]usb 1-1: generic converter now attached to ttyUSB0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]usbcore: registered new interface driver usbserial_generic[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I've also put the line "usbserial vendor=0×*** product=0×***" inside &#8220;/etc/modules&#8221; file[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]When opening putty or minicom, I'm using /dev/ttyUSB0[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I am very new to this OS (Ubuntu 11.10), have only been using it for a few days so still very much a newbie.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I have done a lot of Goggling but just can find any information about this problem, apart from speed setting which as I said is correct.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Please help![/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Thanks in advance,[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Wayne[/FONT][/SIZE]

---

### Post by dandnsmith on 2012-04-02
Do you get the odd characters right from the start, or does it look alright for a bit and then switch? It's possible that you're getting some odd control characters which don't affect the Windows stuff (seen this happen, and did something like copy and paste into an editor which made things OK again).

---

### Post by wbosher on 2012-04-02
It's right from the beginning. When the router/switch boots up it would normally show a whole lot of hash/pound symbols as the IOS unpacks then ask to press enter to continue, this just shows garbage.

---

### Post by dandnsmith on 2012-04-03
Only thing I can think of is that it's a timing issue.
Perhaps you need something other than/in addition to the 96008N1 to get it correct - I've really forgotten all the (little) serial codings that I used to know over the intervening decades.

---

### Post by wbosher on 2012-04-03
I've tried other timing variations but this made no difference. The only thing I can think of is that my USB/serial adapter isn't compatible with Ubuntu for some reason. :confused:
 
Might just need to stick with Windows to do this.

---

### Post by Artif on 2012-04-04
1) USB-RS232 cable have a chip and some times not all pins are soldered. You may have fully functional "RS232 to USB" chip, but only with Rx, Tx and Ground pins to be enabled. If your hardware/sofware is trying to use full RS232 functionality, it may fail in this case. May be there is a way to limit somehow any functionality on any side? At hardware or software level...

2) You may try to find "cable's" chip marking and look for whether or not such a chip have any drivers for Linux. Whether or not someone already had problems with it or there were no problems before. Cable's appearance or model number will not give you information about chip name. The only way to see the name is to find it via utilities like lshw, or to have a look directly at a chip.

---

### Post by wbosher on 2012-04-04
Thanks Artif. I'll see if I can find a driver for it, I guess that's most likely the issue as the cable itself is fine because it work in Windows.
 
Better hit the Googles  :P

---

### Post by wbosher on 2012-04-05
I think the problem is with the adapter...Ubuntu just doesn't like it.

It's a cheap HL-340 and after doing some Goggling, it looks like I'm not the only one having trouble with this thing in Ubuntu.

It seems to recognise it ok though  :confused:

wbosher@wbosher-Aspire-5315:~$ lsusb
Bus 006 Device 003: ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter


Guess I should have spent a little more $$$ and got a decent one. Any suggestions?

---

### Post by wbosher on 2012-04-11
Sorry to bump this one, but I need just a little more help on this.
 
As it turns out after some Googling, the **QinHeng Electronics HL-340 USB-Serial** adapter is a cheap peice of rubbish that no-one seems to be able to get working in Linux, even thouogh it works fine in Windows. :confused:
 
Anyway, can anyone recommend a good one that someone has used to console to a Cisco device successfully?

---

### Post by wbosher on 2012-05-11
A BIG BIG thanks to those who created 12.04. Finally it works! Still can't get it working in Putty which is a shame because I like Putty, but it work great in Minicom. :) I was soooo close to ditching Ubuntu and re-installing Windows, but not now.

I only have one more question, is there any way to get a desktop icon to launch Minicom?

I found something that says to right-click on the desktop and choose "Create launcher" but this option doesn't seem to be there in 12.04.

Thanks for all your help and patience...nearly there.

---

### Post by MattJones900 on 2012-09-01
> **wbosher said:**
> Sorry to bump this one, but I need just a little more help on this.
 
As it turns out after some Googling, the **QinHeng Electronics HL-340 USB-Serial** adapter is a cheap peice of rubbish that no-one seems to be able to get working in Linux, even thouogh it works fine in Windows. :confused:
 
Anyway, can anyone recommend a good one that someone has used to console to a Cisco device successfully?
 
I have been using the XS880 from US Converters successfully with several Cisco routers, you can read about it here:
[5 Steps for Choosing the Best USB to Serial adapter]("http://www.usconverters.com/index.php?main_page=page&id=62&chapter=0")
I have used it with Ubuntu and a friend of mine says it works with Fedora.

---

### Post by MattJones900 on 2012-09-28
Just wanted to add this link [USB to serial adapter wiki]("http://www.usb-serial-adapter.org/") where you can read all you ever need to know about usb serial adapters before you buy.

---

### Post by MattJones900 on 2012-09-28
> **wbosher said:**
> Sorry to bump this one, but I need just a little more help on this.
 
As it turns out after some Googling, the **QinHeng Electronics HL-340 USB-Serial** adapter is a cheap peice of rubbish that no-one seems to be able to get working in Linux, even thouogh it works fine in Windows. :confused:
 
Anyway, can anyone recommend a good one that someone has used to console to a Cisco device successfully?

Yes stay away from those cheap ebay usb serial adapter cables, I had several  of them, and I throw away all because they just didnt work. Take a look at this: [usb serial converters]("http://www.usconverters.com/index.php?main_page=page&id=62&chapter=0"), Im using the XS880, it costs a bit more but its well worth the money.

Regarding connecting a Cisco device it says on the manufacturers website that will work with Cisco Break sequence so I assume that it will work with Cisco devices. 

Here is also a [USB serial adapter]("http://www.usb-serial-adapter.org/") wiki which will explain you everything you ever need to know before buying an adapter.

---


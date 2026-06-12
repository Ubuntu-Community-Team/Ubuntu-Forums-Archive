---
title: "can´t activate 3g/umts modem on toshiba portege r500"
date: 2008-10-13
forum: Hardware
---

### Post by esplinter on 2008-10-13
Hi,

I have just installed kubuntu x86_64 on portege r500 but I cant turn on the umts/3g modem.

On WindowsXP I use Fn+F8 to activate it. When I use that key combination a new light starts blinking next to the wireless light, meaning 3g/umts is turned on but I can´t do this on linux.

I can´t activate it so even lspci can´t find the umts modem.

I tried an option on the bios saying "Device Config: All Devices /  Setup by OS" (tried first option, all devices) but I still cant find the umts modem under linux.

I also downloaded the toshet utility  [[http://www.schwieters.org/toshset/]](http://www.schwieters.org/toshset/]) but didn´t find any option related to 3g/umts modems.

¿any clue about how to activate it??

many thanks in advance.

---

### Post by esplinter on 2008-10-24
hi

finally I have upgrade to kubuntu 8.10 (intrepid) which is still a release candidate (kernel 2.6.27) and set on bios "Device Config: All Devices" and my 3g/umts modem is recognized.


root@leonardo:~$ lsusb
Bus 005 Device 004: ID 0930:0c05 Toshiba Corp.
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0930:1302 Toshiba Corp. Wireless Broadband (3G HSDPA) SM-Bus Minicard Status Port
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by amrs on 2009-05-16
> **esplinter said:**
> hi

finally I have upgrade to kubuntu 8.10 (intrepid) which is still a release candidate (kernel 2.6.27) and set on bios "Device Config: All Devices" and my 3g/umts modem is recognized.


root@leonardo:~$ lsusb
Bus 005 Device 004: ID 0930:0c05 Toshiba Corp.
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0930:1302 Toshiba Corp. Wireless Broadband (3G HSDPA) SM-Bus Minicard Status Port
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So, did you (or anyone) ever get the 3G actually working? I can talk to mine, but there's no connection. Tried usbserial and (modified) option drivers both, but it's the same thing. AT commands fine, but if I try to dial, the modem responds immediately with "connect edge" and that's all. In Windows it responds with "connect hsdpa 3.6" and works too.

I'm guessing at this point that since Toshiba provides a utility called "3G RF Power Control Utility" for Windows, something like this tool would be required for Linux as well... This is further supported by the mention somewhere that the at+csq command always returns 99,99 in Linux, which means signal quality is undetectable. In Windows I got for example 11,99 which means decent signal quality.

So, any help? The modem itself is a Novatel Expedite (or Expedition?EU870D, with modified vendor and product ID. Maybe I or someone should ask Novatel what it is that the thing needs to actually get going...

---

### Post by llelkes on 2009-07-23
hello, 
probably you already solved this problem...
if not pls install toshset 1.75 then 
toshset -3g on

good luck

---


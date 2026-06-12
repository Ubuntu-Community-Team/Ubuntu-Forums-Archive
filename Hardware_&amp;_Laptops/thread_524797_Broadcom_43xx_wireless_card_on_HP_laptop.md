---
title: "Broadcom 43xx wireless card on HP laptop"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by GandalfNK on 2007-08-13
Hi, I've been working on this for a week now and I just can't get that card to cooperate.

So far, I've found two ways people solved this kind of problem: By using ndiswrapper with appropriate Windows drivers or by using the native Ubuntu bcm43xx driver with firmware extracted from various other drivers.

Neither of these approaches has worked for me so far. I tried it under Feisty as well as Gutsy (Tribe 4).

Using ndiswrapper with drivers extracted from the file sp33008.exe (obtained from the HP website) and then loading ndiswrapper via modprobe had no effect whatsoever. No wireless interface showed up under iwconfig. Instead, dmesg showed the following cryptic messages:
> [ 174.331902] usbcore: deregistering interface driver ndiswrapper
[ 174.332531] ndiswrapper (ntoskernel_exit:2713): object
ffff81002f44dc30(2) was not freed, freeing it now
[ 174.899251] APIC error on CPU0: 40(40)
[ 176.004886] ndiswrapper version 1.45 loaded (smp=yes)
[ 176.021975] ndiswrapper (link_pe_images:577): fixing
KI_USER_SHARED_DATA address in the driver
[ 176.023486] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006,
4.40.19.0) loaded
[ 176.023819] ACPI: PCI Interrupt 0000:30:00.0[A] -> GSI 18 (level,
low) -> IRQ 18
[ 176.024045] PCI: Setting latency timer of device 0000:30:00.0 to 64
[ 176.026306] ndiswrapper (NdisWriteErrorLogEntry:192): log: C000138D,
count: 1, return_address: ffffffff8830664e
[ 176.026311] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x10e
[ 176.026318] ndiswrapper (mp_init:263): couldn't initialize device:
C0000001
[ 176.026323] ndiswrapper (pnp_start_device:440): Windows driver
couldn't initialize the device (C0000001)
[ 176.026332] ndiswrapper (mp_halt:305): device ffff81000a253780 is not
initialized - not halting
[ 176.027144] ndiswrapper: device eth%d removed
[ 176.027153] ACPI: PCI interrupt for device 0000:30:00.0 disabled
[ 176.027424] ndiswrapper: probe of 0000:30:00.0 failed with error -22
[ 176.028050] usbcore: registered new interface driver ndiswrapper

Using the native bcm43xx driver and extracted firmware, I managed to make the card show up under iwconfig, but I can't connect it to the network and sudo iwlist scan yields > Interface doesn't support scanning: No such device
I'm not sure, whether I'm extracting the firmware from the correct driver file, though. There seem to be lots of different ones around and I would be grateful if someone could point me the right version.
The card shows up as "Broadcom Corporation BCM4310 UART (rev 02)" under lspci, while iwconfig detects it as "Broadcom 4311" (using the native driver approach), so maybe that might be hinting towards the source of my problems.

I'm quite desperate already. I've tried lots of tutorials and read tons of forum threads, but somehow nothing seemed to help me, so I'd be really grateful if someone could help me solve this.

---

### Post by notoriousdbp on 2007-08-13
I use the ndiswrapper method.  Did you blacklist the bcm43xx driver before trying this method

---

### Post by GandalfNK on 2007-08-13
Yeah, I did. Forgot to mention that..

---

### Post by notoriousdbp on 2007-08-13
The files I use (I have a BCM4318 ) are in this ZIP file (hope I've not done anything illegal here - apologise to moderators if I have - Just trying to help:))

---

### Post by GandalfNK on 2007-08-13
Thanks for those files. I'm afraid, they didn't help me, though.
Sorry, I should have mentioned, that I'm using the 64bit kernel. ndiswrapper noticed that the .inf file, you used, is not a 64bit driver, so I suppose you're using 32bit Ubuntu, right?

I've tried the 32bit kernel as well, but with that my hard disk was dreadfully slow, which is probably completely unrelated to the WLAN problem.

Any other ideas, what I might try?

---

### Post by siralphred on 2007-08-13
this is the easiest method to get 43xx working  [http://ubuntuforums.org/showthread.php?t=405990&highlight=wireless](http://ubuntuforums.org/showthread.php?t=405990&highlight=wireless) i use hp dv6000 and it worked flawlessly

---

### Post by #Reistlehr- on 2007-08-13
I have the same exact card as you. I had a helluva time getting it to run. and even after all the trouble, it just doesnt wanna start on boot sometimes. 

User this driver with ndiswrapper
[ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe)
cabextract it then ndiswrapper -i

follow this guide if needed
[https://help.ubuntu.com/community/Wi...ndiswrapper%29](https://help.ubuntu.com/community/Wi...ndiswrapper%29)

substitute the 4318 with 4310

when you get to the 14E4:4324.5.conf  part, use: 14E4:4312.5.conf  (since it's the devid in LSPCI)

Edit: Some things that i had to do extra to the guide or that i didnt have to do: Network Manager was installed by default in Feisty, i didnt have to add WPA_supplicant already present, something is still fishy about wireless on boot. sometimes it works sometimes it doesnt. if it doesnt, run sudo depmod -a and sudo modprobe ndiswrapper

---

### Post by Jukka-Pekka on 2007-08-14
Sorry I can't remember the details, but this problem was solved for me when i started going through the configuration files.

The installation program&procedure  had somehow changed the wlan0 - lan0 - wlan1-lan1-eth0-eth1 texts so that they were not always referring to the correct cards!

So by going thorough those files and changing the name of the broadcom card to wlan0 everywhere made my connection work... felt like a miracle ;) after over two weeks of searching...

Sorry i cannot remember what those three or four files to be checked were called, I am not a great fan of the unintuitive "command line" interface.

(You have to run some reinstall/rebuild/recheck/reconfigure command after modifying those files!)

Best regards,
Jukka

---

### Post by GandalfNK on 2007-08-14
It works! Thank you so much for your hint, Reistlehr! I'm not sure what exactly did the trick, but it was either changing the driver (from sp33008.exe to sp34152.exe) or the tinkering with that .conf file.
Anyway, I'm really glad to finally have a connection.

Thanks, everybody, for your help!

---

### Post by #Reistlehr- on 2007-08-16
glad it helped.

---


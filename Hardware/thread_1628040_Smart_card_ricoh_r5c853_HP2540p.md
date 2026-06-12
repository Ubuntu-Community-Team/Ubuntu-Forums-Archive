---
title: "Smart card ricoh r5c853 HP2540p"
date: 2010-11-22
forum: Hardware
---

### Post by haggan on 2010-11-22
Hej

I have a HP2540p. I can't get the smart card reader to work
I have been told it is a Ricoh-R5C853/R5C803. 
Anyone know anything about it? Or if there is any support for the smart card reader?

Cheers

---

### Post by Fafler on 2010-11-22
Use
```
lspci | grep -i ricoh
```
to correctly identify the device.

It should be supported. Back in the day, with 9.10 i had to do some quirks similar to [http://pbs01.wikidot.com/ricoh-r5c592-card-reader-on-ubuntu](http://pbs01.wikidot.com/ricoh-r5c592-card-reader-on-ubuntu) to get it to work. With 10.04 and 10.10 it worked out of the box.

Which Ubuntu release are you using?

---

### Post by haggan on 2010-11-22
Here is the output

```
44:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
44:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
44:06.2 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev bb)

```

Everything seems to work except the "smart card" 
Running "pcsc_scan" for example dont find any card. I have tested with a USB card reader and it works.

---

### Post by Fafler on 2010-11-22
Now it occurs the to me that you actually mean smart card when you talk about smart cards. I thought you where talking about SD cards. It's handled by the same controller chip, but i have no experience with the smart card part of it.

---

### Post by haggan on 2010-12-03
I acutally got help from HP support Amazing. 

They suggest that the Smart card reader is a SCM device and that I can use their drivers. Unfortunatly I cant get it to complie under ubuntu 10.10 x86_64 but perhaps this will help someone else. 


> A workaround would be to download the driver from SCM website and do minor changes to the code:
 
Note: HP does not take any responsibility in doing the same. This would be at the customers own risk.
 
Step 1:
Run the command - lspcmcia -v and get:
Product Name:
Identification: manf_id:
 
Check for: prod_id(1):
 
Step 2:
Goto - [http://www.scmmicro.com/support/pc-security-support/downloads.html](http://www.scmmicro.com/support/pc-security-support/downloads.html)
Download the driver - SCR241 - Linux 32-bit (2.4.x) Driver
Extract the files, and find the file scr241_main.c
Search for the lines containing
```
PCMCIA_DEVICE_PROD_ID1("SCR243 PCMCIA",0x2054e8de),
PCMCIA_DEVICE_PROD_ID1("SCR24x PCMCIA",0x54a33665),

```
and add the line:
 
```
PCMCIA_DEVICE_PROD_ID1("HP", 0x53cb94f9),
```
 
Note: "HP", 0x53cb94f9 is the prod_id(1) what I have got in my unit - so this has to be changed with what the customer gets on his unit when he runs the lspcmci -v command
 
Use the script install to install the driver.
 
This should work.


My lspcmicia gives:
```
spcmcia -v 
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:44:06.2)
	Configuration:	state: on	ready: unknown
			Voltage: 3.3V Vcc: 3.3V Vpp: 0.0V
Socket 0 Device 0:	[pata_pcmcia]		(bus ID: 0.0)
	Configuration:	state: on
	Product Name:   RICOH Bay8Controller 
	Identification:	manf_id: 0x0000	card_id: 0x0000
			function: 254 (unknown)
			[COLOR="Red"]prod_id(1): "RICOH" (0xd9f522ed[/COLOR])
			prod_id(2): "Bay8Controller" (0xb8dd2c87)
			prod_id(3): --- (---)
			prod_id(4): --- (---)

```

I guess that it is the RICOH that is the right product ID for hp2540p

---

### Post by patchon on 2010-12-29
Hello !

I'm very interested in getting this smart card reader to work, unfortunatelly I think it's kinda impossible. I don't know if the guy at HP where right when he told you that the smart card readers are SCM devices, but I *really* hope he so, then it's just a matter of getting it to work with the driver he suggest. The thing that makes me suspicious is that he referrers to a device called "HP", and yes I know that he also says that the custemer should change it to whatever the customer gets from lspcmcia -v, but the thing is that he is talking about the id of the actual reader, the thing that you get on your model (and me) is the "RICOH" (0xd9f522ed), which I think is the adress to the chip that handles SD/MMC-cards (and also smart card accourding to this, [http://www.ricoh.com/LSI/product_pcif/pcc/5c821/index.html](http://www.ricoh.com/LSI/product_pcif/pcc/5c821/index.html)). But from what I understand, that's not a SCM device. 

To me it seems like the the RICOH chip is the one that handles the connection between SD/MMC/smart card-reader's to the PCI port on the laptop - But, I'm no expert in the area here, I'm just trying to draw some conclusions. So if that is the case, I wonder if the RICOH chip only connects the SCM-device (the smartcard-reader) to the pci port, or if the RICOH chip actually "is" the smartcard-reader too ? 

Anyway, I've built the driver as the HP-suport suggest, but I still can't get it to work. 

- I can build it successfully under RHEL 6 with kernel 2.6.32 (the reason btw. why it fails for you under Ubuntu 10.10 is because they made some changes in  kernel 2.34 and newer in the pcmcia part, and the driver you download from scm website is not compatible with those changes, if you use an older kernel it should work). 
- The installscript installs udev--rules and finishes correctly. 
- However nothing gets picked up by udev so I manually ran the command from the "udev-rule-file" (/etc/pcmcia/scr24x-node add), that script creates a /dev/dev/SCR24x0 with the majornumber accourding to /proc/devices. 
- pcscd -afd, gives this 
   00002120 readerfactory.c:1024:RFInitializeReader() Attempting startup of SCR24x Smart Card Reader 00 00 using /usr/local/scm/lib/libSCR24x.so 
   00000210 readerfactory.c:846:RFBindFunctions() Loading IFD Handler 2.0
   00008030 readerfactory.c:1050:RFInitializeReader() Open Port 0 Failed (/dev/SCR24x0)
   00000007 readerfactory.c:914:RFUnloadReader() Unloading reader driver.
   00000019 readerfactory.c:233:RFAddReader() SCR24x Smart Card Reader init failed.

Conclusions, 
- Can't get scm driver (with modifications as hp suggest) to work.  
- SCM driver must be bult with kernel <2.34 (or 35, I forgot), only works on 32 bit architectures to, I've mailed them about that. 

It would be really nice if somebody (from HP or wherever) could straighten this up. Maybe you can mail HP again and that friendly guy could clear things up ?

---

### Post by layr on 2011-01-19
> **haggan said:**
> 
```
spcmcia -v 
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:44:06.2)
    Configuration:    state: on    ready: unknown
            Voltage: 3.3V Vcc: 3.3V Vpp: 0.0V
Socket 0 Device 0:    [pata_pcmcia]        (bus ID: 0.0)
    Configuration:    state: on
    Product Name:   RICOH Bay8Controller 
    Identification:    manf_id: 0x0000    card_id: 0x0000
            function: 254 (unknown)
            [COLOR=Red]prod_id(1): "RICOH" (0xd9f522ed[/COLOR])
            prod_id(2): "Bay8Controller" (0xb8dd2c87)
            prod_id(3): --- (---)
            prod_id(4): --- (---)

```I guess that it is the RICOH that is the right product ID for hp2540p
Hey thanks for the info. I followed HP support's troubleshooting you gave here, but installing reported:
```
Kernel Headers located.
Kernel module has to be recompiled
pcsclite middleware is not installed.
```Checked synaptics, spcsclite should be installed.

---

### Post by Woutrrr on 2011-01-27
And? Did you made any progress? I'm very interested in installing a working driver, so I can use my smartcard reader.

---

### Post by haggan on 2011-01-28
Hej. I have contact HP support again by mail but I am unsure if they get it. I have not heard any more from them my self. No more progress for me any one else?

---

### Post by ppihus on 2011-05-16
Has anyone had any success with this? I'm on a 64bit HP 8440p with what seems to be the same smart card reader and no luck so far.

---

### Post by haggan on 2011-05-19
No I have not got it working and no update from my HP case.

Please report it to HP since they have listed support for Linux at least for my EliteBook 2540p. 

Cheers

---

### Post by ppihus on 2011-05-19
> **haggan said:**
> No I have not got it working and no update from my HP case.

Please report it to HP since they have listed support for Linux at least for my EliteBook 2540p. 

Cheers

Yeah, got no help from there. Told me to contact operating system manufacturer or install Windows. Not that I'd blame them.

---


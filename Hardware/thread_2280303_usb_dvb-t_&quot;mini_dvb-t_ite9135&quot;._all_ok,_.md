---
title: "usb dvb-t &quot;mini dvb-t ite9135&quot;. all ok, but doesn't works"
date: 2015-05-29
forum: Hardware
---

### Post by mattexxx on 2015-05-29
Recently I had need to buy a usb stick to view dvb-t tv. After a brief search  on [linuxtv.org]("http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices"), and seller sites, I've bought the following stick:
[TABLE="class: wikitable sortable, width: 100%"]
[TR]
[TD]vendor name[/TD]
[TD]supported[/TD]
[TD]usb id[/TD]
[TD]hardware[/TD]
[TD]firmware[/TD]
[TD]photo comments.[/TD]
[/TR]
[TR]
[TD]ITE Inc. Zolid Mini DVB-T Stick
Version 1[/TD]
[TD] [COLOR=green]&#10004; Yes[/COLOR], [COLOR=green]in kernel since 3.2[/COLOR]
Chip Version 1[/TD]
[TD] 048d:9135 USB2.0[/TD]
[TD] [IT9135]("http://www.linuxtv.org/wiki/index.php/ITE_IT9135")[/TD]
[TD] from 3.3
dvb-usb-it9135-01.fw
Kernel 3.2 uses
dvb-usb-it9137-01.fw[/TD]
[TD] Markings Mini DVB T [[IMG]http://www.linuxtv.org/wiki/images/thumb/4/46/Mini.jpg/120px-Mini.jpg[/IMG]]("http://www.linuxtv.org/wiki/index.php/File:Mini.jpg")[/TD]
[/TR]
[/TABLE]
 
Well, I've this device by some days, and I've tried to make it works with my lubuntu 14.04.2LTS.
My situation seems a bit strange (in particular after some reading about these topic on forum): in spite  **lsusb** and **dmesg** output (_see below_) would seem indicate a recognized hardware, and device is also recognized in kaffeine as "ite 9135 Generic_1", it doesn't works. Scanning the frequencies is at same time slow, and no one channel was found (I use home antenna, and I've tested connectivity of antenna's cable to stick, because it require a cable adapter).
[B]
some suggestion?[/B]



** lsusb**
```
Bus 001 Device 006: ID 048d:9135 Integrated Technology Express, Inc. Zolid Mini DVB-T Stick
```

**dmesg**:
```
[16989.220125] usb 1-1: new high-speed USB device number 6 using ehci-pci
[16989.354234] usb 1-1: New USB device found, idVendor=048d, idProduct=9135
[16989.354247] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[16989.357193] it913x: Chip Version=02 Chip Type=9135
[16989.358180] it913x: Dual mode=0 Tuner Type=38it913x: Unknown tuner ID applying default 0x60
[16989.359815] usb 1-1: dvb_usb_v2: found a 'ITE 9135 Generic' in cold state
[16989.359925] usb 1-1: dvb_usb_v2: downloading firmware from file 'dvb-usb-it9135-02.fw'
[16989.360693] it913x: FRM Starting Firmware Download
[16989.593274] it913x: FRM Firmware Download Completed - Resetting Deviceit913x: Chip Version=02 Chip Type=9135
[16989.629894] it913x: Firmware Version 52953344<6>[16989.700533] usb 1-1: dvb_usb_v2: found a 'ITE 9135 Generic' in warm state
[16989.700721] usb 1-1: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[16989.702946] DVB: registering new adapter (ITE 9135 Generic)
[16989.705288] it913x-fe: ADF table value    :00
[16989.709633] it913x-fe: Crystal Frequency :12000000 Adc Frequency :20250000 ADC X2: 01
[16989.746503] it913x-fe: Tuner LNA type :60
[16990.012979] usb 1-1: DVB: registering adapter 0 frontend 0 (ITE 9135 Generic_1)...
[16990.013277] Registered IR keymap rc-it913x-v1
[16990.013684] input: ITE 9135 Generic as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/rc/rc2/input17
[16990.014003] rc2: ITE 9135 Generic as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/rc/rc2
[16990.014028] usb 1-1: dvb_usb_v2: schedule remote query interval to 250 msecs
[16990.014049] usb 1-1: dvb_usb_v2: 'ITE 9135 Generic' successfully initialized and connected
```

---

### Post by blm-ubunet on 2015-05-29
I would use the cmd line tools from LinuxTV scan,dvbscan & tzap:
[http://www.linuxtv.org/wiki/index.php/Scan](http://www.linuxtv.org/wiki/index.php/Scan)
All those should be available as package in ubuntu "dvb-apps".

The other (very good) tool mentioned is "w_scan" but you need to compile from source.

Use "[dvb]scan" to generate "channels.conf" file that can then be used to "tzap" to a channel. Then you can "cat" the mpegts video stream to file.
[http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device](http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device)

Can use "femon -H" to display signal strength etc (with any other program using tuner).

---

### Post by mattexxx on 2015-05-30
> **blm-ubunet said:**
> I would use the cmd line tools from LinuxTV scan,dvbscan & tzap:   thanks for shorth and clean answer.
   I've partially solved. I think there were some hardware problem on the dvb-t pcb stick: 
-1- the IR receiver at device was in short circuit with other components on pcb, because to put all in its case it was bent.
 -2- similar problem with crystal oscillator. to put in the case,  its two pins were in short circuit.  

Well if anyone has issues (recognized, but doesn't works) checks first these two components (after some attempts I've removed the ir). 
  

Honestly I've also tried to renew the solders, I don't know if there was the need: the two situations described above were found (verified), but this process was made without evidence, I mention this because in two different attempts the stick had works only after I've repassed the solders . note: I've not the ideal tool to make this and have used a simple solder pen (with a tiny tips for smd) , and also I'm not so trained with soldering process, so If you arent' practiced I don't suggest this (is easy do damages).

p.s.
when tuning it has found _all_ channels. I think kaffeine data of signal snr and  power, aren't correct (often at 0), so I suggest to complete all the scan process without look these properties. note: Maybe in general the properties of this device aren't correct, because also via command line I obtain measures very low than those retrieved by set-top box for tv, in spite, the quality of this device is very very better.

---

### Post by blm-ubunet on 2015-05-30
Well there's no point repeating the good troubleshooting guide on LinuxTV.org.

So do you mean that the device was faulty as supplied?
Was the internal PCB bent to fit into the plastic housing?
Do you have a photo of the internals ?

Lots of the tuner devices do not return meaningful signal levels, "femon -H" can show you the bit error rate "ber" which should be mostly zero.

Good on you for repairing it, v.s. adding to landfill.
I work with micro-electronics & need to use a (bino) microscope to do stuff like that.

---


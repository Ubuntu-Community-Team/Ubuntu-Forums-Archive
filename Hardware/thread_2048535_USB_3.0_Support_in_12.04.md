---
title: "USB 3.0 Support in 12.04"
date: 2012-08-26
forum: Hardware
---

### Post by Jedcurtis on 2012-08-26
Hello everyone!
My laptop has 2 USB 3.0 slots.  When using a USB 2.0 cable on a USB 3.0 device it works great except I obviously don't get the speed of the USB 3.0 cable.  As a matter of fact, when using the USB 3.0 cable, the device (an external 500Gb sata hdd) is not recognized at all.
After perusing the forums for a couple of weeks now, I have not been able to find any info about USB 3.0.  Does Ubuntu 12.04 support USB 3.0?  Due to the vast increase of data transfer speeds with USB 3.0, I'd love to be able to utilize this drive to its' full potential via USB 3.0.
I'm probably just doing some simple thing wrong!  Anyone out there who could 'enlighten' me,  I'd be real grateful!
Just when you start considering yourself 'not a noob' something like this comes along to bring you down a notch!
Anyway, any advice will be greatly appreciated!
By-the-way, the cable that came with my external device is a USB 3.0 cable.
Thanks,
Jed

---

### Post by lakerssuperman on 2012-08-27
Is the a brand name or a no name?  Did it come as one unit or was it an external enclosure that was bought separately from the hard drive?

---

### Post by Jedcurtis on 2012-08-27
I should have posted this in the first post.  This is the result of lspci commad with the drive plugged in;

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev ff)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
06:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)

```This is the result of the lsusb command while the drive is plugged in;

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0c45:642a Microdia 
Bus 002 Device 003: ID 8086:0189 Intel Corp.

```

this is the dmesg | tail info;

```

[ 1292.506784] usb 3-2: new low-speed USB device number 2 using xhci_hcd
[ 1292.507713] usb 3-2: Device not responding to set address.
[ 1292.711398] usb 3-2: Device not responding to set address.
[ 1292.914138] usb 3-2: device not accepting address 2, error -71
[ 1292.970107] hub 3-0:1.0: unable to enumerate USB device on port 2

```

@lakerssuperman, it is a Western Digital Scorpio Blue 500Gb hdd.  It is a separate hdd enclosure I just purchased.  Not sure of the brand of the external enclosure I purchased... 

Any help, as I said is greatly appreciated...

Jed

---

### Post by lakerssuperman on 2012-08-27
I only ask about the enclosure because when I first got into USB 3.0 I bought a Western Digital Blue drive and Rosewill external enclosure.  I had problems with it to the point that my computers finally stopped recognizing it when plugged into the USB 3.0 ports.  It would be recognized by any of the USB 2.0 ports and transfer files as fast as those ports would allow.

I decided to get a different enclosure since I checked the ports with my USB 3.0 flash drive and it worked fine.  My new enclosure just arrived today and I'm testing it as we speak (type).  It was recognized no problem and I just transferred about 30 gigabytes at a sustained speed of 105-109 megabytes. 

It's possible that your enclosure could be the issue.  It seems some of these are crap with USB 3.0.

This is the one I just bought and it seems to be working well so far.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817707227](http://www.newegg.com/Product/Product.aspx?Item=N82E16817707227)

---

### Post by Jedcurtis on 2012-08-27
@lakerssuperman, thanks for the input, the enclosure I bought is for a laptop sized drive.  I had some 'ebay bucks' that I had to spend before they expired and I just bought a cheapie.  I've been unable to find a mfg name or number on it believe it or not!  (I suppose this goes to the cheapness of it)  Hopefully someone will recognize the issue.
Again, thanks for your input...  This is what is so great about Ubuntu, and the forums especially!  I've never 'asked' any question here that someone didn't do their best to help me with a solution, while bending over backwards to be nice about offering it!  Such a nice change from the treatment one gets when talking to a 'Windows Professional'!  I was in the computer industry for over 25 years and am always amazed that MS has such a commanding lead in the pc market when you consider their overt attempts at condescension!

Jed

---

### Post by kurt18947 on 2012-08-28
I'll agree with lakerssuperman about 'no-name' drive enclosures.  I bought a $5 'USB2' enclosure from Amazon about 6 months ago.  It connected at 12 MB./sec, i.e. USB 1.1.  I replaced the no-name with a drive enclosure from Vantec and installed the same HD.  Now it shows connected at 480 MB./sec.   I'm sure USB3 is even more hit & miss because USB3 is not near universal like USB2 yet.

---

### Post by michalt on 2012-09-09
I have same problem, though my USB 3.0 works after computer resume from suspend. This issue is reported and patch already submited: [https://www.google.cz/url?sa=t&rct=j&q=&esrc=s&source=web&cd=7&ved=0CGwQFjAG&url=https%3A%2F%2Fbugs.launchpad.net%2Fbugs%2F1000424&ei=vyRNULDiGovAswaw_YDYCg&usg=AFQjCNGILdNzlnl5ZgXPRu3gyb6kUMJIPQ&sig2=O7fT216Z9O3nJ72-6t9ePg&cad=rja](https://www.google.cz/url?sa=t&rct=j&q=&esrc=s&source=web&cd=7&ved=0CGwQFjAG&url=https%3A%2F%2Fbugs.launchpad.net%2Fbugs%2F1000424&ei=vyRNULDiGovAswaw_YDYCg&usg=AFQjCNGILdNzlnl5ZgXPRu3gyb6kUMJIPQ&sig2=O7fT216Z9O3nJ72-6t9ePg&cad=rja)

---

### Post by Flaggmann on 2012-11-29
> **michalt said:**
> I have same problem, though my USB 3.0 works after computer resume from suspend. This issue is reported and patch already submited: [https://www.google.cz/url?sa=t&rct=j&q=&esrc=s&source=web&cd=7&ved=0CGwQFjAG&url=https%3A%2F%2Fbugs.launchpad.net%2Fbugs%2F1000424&ei=vyRNULDiGovAswaw_YDYCg&usg=AFQjCNGILdNzlnl5ZgXPRu3gyb6kUMJIPQ&sig2=O7fT216Z9O3nJ72-6t9ePg&cad=rja]("https://www.google.cz/url?sa=t&rct=j&q=&esrc=s&source=web&cd=7&ved=0CGwQFjAG&url=https%3A%2F%2Fbugs.launchpad.net%2Fbugs%2F1000424&ei=vyRNULDiGovAswaw_YDYCg&usg=AFQjCNGILdNzlnl5ZgXPRu3gyb6kUMJIPQ&sig2=O7fT216Z9O3nJ72-6t9ePg&cad=rja")


I have same problem today. I am able to view and mout a 3TB Seagate ext USB3.0 drive by plugging into a USB 2.0 port no problem but pci express usb 3.0 card not mounting it. lspci shows card hub there ok and recognized as does lsusb but usb-devices doesn't show the drive at all, nor does it show an normal 8GB usb 2.0 drive in backward compatibility mode. I used it once when I first bought it 3-4 weeks back to partition the ext drive and it worked. The only thing that gets done with the pc is login check and do updates , check and do clamav scans & upd's and logout.  NOTHING else; it is a pc set up for someone else and I am just keeping it up to date while I wait for them to pick it up. SURPRISE SURPRISE USB 3 not working; starnge when the only thing done is the updates.

---

### Post by Flaggmann on 2012-11-29
> **Flaggmann said:**
> I have same problem today. I am able to view and mout a 3TB Seagate ext USB3.0 drive by plugging into a USB 2.0 port no problem but pci express usb 3.0 card not mounting it. lspci shows card hub there ok and recognized as does lsusb but usb-devices doesn't show the drive at all, nor does it show an normal 8GB usb 2.0 drive in backward compatibility mode. I used it once when I first bought it 3-4 weeks back to partition the ext drive and it worked. The only thing that gets done with the pc is login check and do updates , check and do clamav scans & upd's and logout.  NOTHING else; it is a pc set up for someone else and I am just keeping it up to date while I wait for them to pick it up. SURPRISE SURPRISE USB 3 not working; starnge when the only thing done is the updates.
SOLVED

Dlink i/f card for PCIe and Star Link card for PCI USB 3.0 required 4 pin molex nylon power connectors to be connected internally otherwise external devices apparently not serviced. Wording on boxes mislead me into beleiving power connection only required if external devices like ipods required to have batts recharged using the ports. Appears also required to service ext devs. explains why bus side of card showed Ok to linux lspci and lsusb yet no devices showing.

---


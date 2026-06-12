---
title: "External usb DVD burners"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by Nonno Bassotto on 2006-06-30
Since my laptop's internal dvd drive doesn't work anymore, I need to buy an external one. Before actually buying I'm trying to do some research for compatibility with linux/ubuntu.

I just wanted to know if usb burners are something I can expect just to plugin and they will work (like pen-drives) or something I will have to struggle for (like scanners). Some research on this forum makes me think it is the first case, but I just wanted to be sure.

In the second case, can anybdy report any of the following (or similar) as working or not working?

LG GSA-2164D
LG GSA-2166D
Benq EW164B
Samsung Writemaster

---

### Post by Bafflerog Rumplewhisker on 2006-09-10
I'm sorry if this answer comes too late, but it's just now that I've stumbled upon this question.

The LG GSA-2166D works like a charm for me. No problems with it. 

I did read a post about someone getting choppy DVD playback on it ( doesn't happen to me though ), can't remember where ... people replying to him said something about not being able to set DMA on USB drives.

Take care.

---

### Post by Nonno Bassotto on 2006-09-10
Thank you for your reply. I was first at a one month conference and then on holydays, so I thought I could wait and buy the drive when I was back. So I think I'll buy it one of these days, and your advice comes in time. :)

---

### Post by Anduu on 2006-09-10
I recently bought a LiteOn 16X Dual Layer USB drive.Just plugged it in and I was off to the races.

---

### Post by wsj-m on 2006-09-10
External DVD burners are easy with [X]ubuntu ... I use a Lite-On 16x also, though mine was purchased as an internal model and I acquired a seperate 5 1/4" case.

After the drive is connected to your USB port, your system should assign it to correspond to /dev/sr0.  If you want to be sure, run *dmesg* in a terminal window.  In the output, you will see where your system recognized the DVD burner, and what association the file has (sr0, etc).

Good Luck ... :D

---

### Post by barranco on 2006-09-13
I have a Lite-On 16x too, the only problem I have is that I can't burn faster than 6x DVDs

any thoughts?

```

alex@valentina:~$ hdparm /dev/scd0

/dev/scd0:
readonly     =  0 (off)
readahead    = 256 (on)
HDIO_GETGEO failed: Invalid argument

```

I can't see if DMA is enabled

---

### Post by Valencik on 2006-09-13
I plan to buy a Comstar 16X Double Layer External DVD+/-RW Rewriter from future shop today, i'll let you know how it works out. Any one use a comstar DVD burner with Ubuntu before? It better be compatible. [http://www.futureshop.ca/catalog/proddetail.asp?sku_id=0665000FS10067120&catid=23794&logon=&langid=EN](http://www.futureshop.ca/catalog/proddetail.asp?sku_id=0665000FS10067120&catid=23794&logon=&langid=EN)

---

### Post by Anduu on 2006-09-13
> **barranco said:**
> I have a Lite-On 16x too, the only problem I have is that I can't burn faster than 6x DVDs

any thoughts?

```

alex@valentina:~$ hdparm /dev/scd0

/dev/scd0:
readonly     =  0 (off)
readahead    = 256 (on)
HDIO_GETGEO failed: Invalid argument

```

I can't see if DMA is enabled

I may be wrong but I don't think DMA applies for usb drives.Mine doesn't show anything either.

As for not being able to burn faster than 6x i am not sure as I haven't had the opprotunity to burn any yet...i'll have to check it out.

---

### Post by maestrobwh1 on 2007-07-28
I use kubuntu and my USB burner works fine with k3b in Feisty but not in Gutsy.

I have a TSSTCorp TS-H552B external cd/dvd writer.

All other applications work with it in Gutsy... i.e. Gnomebaker, k9copy, my installed players like mplayer.

It is at /dev/sr0

k3b hangs and will not load, however; if I shut off the burner, k3b will then just pop up.  If I turn it back on, k3b locks up until I shut it off again.

If I launch it from terminal, I get no errors... it just "stops" and the read light comes on with the burner and stays on.

It works with my internal CD burner.

Here is a result for dmesg for that device.  It does flag something in the middle, and I put it in bold.  I assume these "rejecting" things are because there are other devices at those "locations" No other program seems affected other than k3b.  The ID ends up being 4,0,0 in working applications.

[  118.914987] usb 3-1: new high speed USB device using ehci_hcd and address 2
[  119.215989] usb 3-1: configuration #1 chosen from 1 choice
[  119.307979] usbcore: registered new interface driver libusual
[  119.339519] Initializing USB Mass Storage driver...
[  119.339687] scsi2 : SCSI emulation for USB Mass Storage devices
[  119.339811] usb-storage: device found at 2
[  119.339814] usb-storage: waiting for device to settle before scanning
[  119.339953] usbcore: registered new interface driver usb-storage
[  119.340029] USB Mass Storage support registered.
[  124.330258] usb-storage: device scan complete
[  124.331058] scsi 2:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552B TS05 PQ: 0 ANSI: 0
[  124.331533] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[  124.363050] sr0: scsi3-mmc drive: 1x/48x writer cd/rw xa/form2 cdda tray
[  124.363552] sr 2:0:0:0: Attached scsi CD-ROM sr0
[B][  149.225249] usb 3-1: USB disconnect, address 2
[  149.230484] scsi 2:0:0:0: rejecting I/O to dead device
[  149.230498] scsi 2:0:0:0: rejecting I/O to dead device[/B]
[  163.769327] usb 3-1: new high speed USB device using ehci_hcd and address 3
[  164.066392] usb 3-1: configuration #1 chosen from 1 choice
[  164.066637] scsi3 : SCSI emulation for USB Mass Storage devices
[  164.066784] usb-storage: device found at 3
[  164.066786] usb-storage: waiting for device to settle before scanning
[  169.056803] usb-storage: device scan complete
[  169.057547] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552B TS05 PQ: 0 ANSI: 0
[  169.065637] sr0: scsi3-mmc drive: 1x/48x writer cd/rw xa/form2 cdda tray
[  169.065704] sr 3:0:0:0: Attached scsi CD-ROM sr0
[  169.065746] sr 3:0:0:0: Attached scsi generic sg1 type 5
[  179.439590] usb 3-1: reset high speed USB device using ehci_hcd and address 3
[B][  186.348269] usb 3-1: USB disconnect, address 3
[  186.348695] scsi 3:0:0:0: scsi: Device offlined - not ready after error recovery
[  186.354038] scsi 3:0:0:0: rejecting I/O to dead device
[  186.354134] scsi 3:0:0:0: rejecting I/O to dead device[/B]
[  208.168425] usb 3-1: new high speed USB device using ehci_hcd and address 4
[  208.465528] usb 3-1: configuration #1 chosen from 1 choice
[  208.465764] scsi4 : SCSI emulation for USB Mass Storage devices
[  208.465905] usb-storage: device found at 4
[  208.465907] usb-storage: waiting for device to settle before scanning
[  213.455952] usb-storage: device scan complete
[  213.456697] scsi 4:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552B TS05 PQ: 0 ANSI: 0
[  213.465034] sr0: scsi3-mmc drive: 1x/48x writer cd/rw xa/form2 cdda tray
[  213.465089] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  213.465136] sr 4:0:0:0: Attached scsi generic sg1 type 5



HELP???

---


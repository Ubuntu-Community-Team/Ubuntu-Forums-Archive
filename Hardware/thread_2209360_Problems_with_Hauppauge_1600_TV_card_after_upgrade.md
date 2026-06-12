---
title: "Problems with Hauppauge 1600 TV card after upgrade to 13.10"
date: 2014-03-05
forum: Hardware
---

### Post by Phiwum on 2014-03-05
Hello.

I just upgraded from 12.10 to 13.10.  I have a Hauppauge 1600 TV card (cx18 driver) that I've used for years, with both S-video and cable inputs (hooked up to a satellite dish box and a pair of rabbit ears, resp.).  

After the upgrade, the picture and sound quality of the S-video is seriously degraded.  Both are full of static, as if I'm not quite tuned in to the channel.  The other input works beautifully.  I'm at a loss as to how to diagnose the problem.  (For what it's worth, I reset the satellite box, and during the reboot process, I saw that the image was still full of static, so the problem does not seem to be the reception between the box and the satellite.)

Output of lspci:

01:07.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
        Subsystem: Hauppauge computer works Inc. WinTV HVR-1600
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (500ns min, 50000ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at f8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [44] Vital Product Data
pcilib: sysfs_read_vpd: read failed: Connection timed out
                Not readable
        Capabilities: [4c] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: cx18

---

### Post by Phiwum on 2014-03-06
Well, I didn't learn too much but I fixed the problem.

I deleted both cards from mythtv and added them afresh.  For whatever reason, this fixed the problem.  

What is particularly odd is that, prior to doing this, I had a static image even when I cat'ed /dev/video0 to a file (and you'd think that the mythtv database was irrelevant for that operation), and now the image is good.  I suspect that myth initializes the card properly once I re-added it to the database, so that this fixed the static even when I wasn't using myth.

So, I guess I'm good, but I wish I had learned more.  Deleting and re-adding capture card is not very illuminating.

---


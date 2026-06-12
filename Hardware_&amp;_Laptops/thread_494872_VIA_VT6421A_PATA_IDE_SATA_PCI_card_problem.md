---
title: "VIA VT6421A PATA IDE SATA PCI card problem"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by BornToBeGeek on 2007-07-07
Hi,

I'm building a server with a Celeron 677MHz processor sitting in a Cognac microATX motherboard with 128Mb RAM and a 4.3Gb HDD that has Kubuntu 6.06 on it (runs just fine for a server :D). Because the mobo has the old 130Gb IDE limitation, I bought a VIA VT6421A based PCI IDE/SATA controller card so I can connect my 200Gb Seagate IDE HDD. Problem is, Kubuntu sees the card but not the HDD:

lspci -vvv
---snip---
0000:01:0e.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
        Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 3
        Region 0: I/O ports at 34d0 [size=16]
        Region 1: I/O ports at 34c0 [size=16]
        Region 2: I/O ports at 34b0 [size=16]
        Region 3: I/O ports at 34a0 [size=16]
        Region 4: I/O ports at 3480 [size=32]
        Region 5: I/O ports at 3000 [size=256]
        Expansion ROM at 20020000 [disabled] [size=64K]
        Capabilities: [e0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

My other server (a more modern PC, also using Kubuntu 6.06) sees the HDD just fine,

The card itself doesn't seem to have any setup, it doesn't give you any options after POST.

It might be a trivial problem, I'm not sure, if anybody can give me some pointers I would be very happy :)

Cheers,
Monica

---

### Post by kgodoy on 2007-12-17
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/16636](https://answers.launchpad.net/ubuntu/+question/16636) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had the same problem with an IBM NetVista A40 PIII1G 256M/30G/48x. I bought a generic VT6421A based board and plugged in my 400GB Seagate PATA 100 hard drive and it just hangs with Ubuntu 7.10 (spewing out errors). Disconnecting the hard drive allows the computer to boot and the VT6421A board is detected just fine. Yes... I [Googled it]("http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=God&q=Ubuntu+7.10+VT6421a&btnG=Search") and I also checked the [ViaArena Forums]("http://forums.viaarena.com/messageview.aspx?catid=20&threadid=80430&highlight_key=y&keyword1=Ubuntu") and found very little in terms of solutions. The only way I eventually got it to work was to revert to Ubuntu 7.04. This tells me that there must be something wrong with the driver that comes with Ubuntu 7.10. Under 7.04 my hard drive is read perfectly even though it's NTFS formatted (I migrated from XP). I guess I'll just keep Feisty Fawn installed and upgrade to Gutsy once I know it was solved. Please let me know if someone else has a solution to this. The ViaArena site only has[ instructions for Feisty Fawn]("http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3270&SubCatID=117") which works fine for me without doing anything extra. Any suggestions for us?! :confused:

I'm a recent adopter of Linux through Ubuntu and I have to say that I really like it. But when I run into things like this I get a little disappointed. I hope that once I learn how to program I can help and contribute instead of just report problems.

Thanks in advanced!

-KGodoy

P.S. Please follow this post with the link to the [LaunchPad]("https://answers.launchpad.net/ubuntu/+question/16636") site where a user already reported this. Unfortunately, people there got into a spat over Open Source and it doesn't look like anybody is going to do anything about the issues with the VT6421a under Ubuntu 7.10 that people are encountering. :neutral:

---


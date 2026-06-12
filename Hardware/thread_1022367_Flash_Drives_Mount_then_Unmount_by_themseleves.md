---
title: "Flash Drives Mount then Unmount by themseleves"
date: 2008-12-26
forum: Hardware
---

### Post by Lifes_Reject on 2008-12-26
Hi Everyone:  i'm running 8.10 Intrepid on my Vostro 1000 Lappy.
And I've got an Express Card plugged into my Laptop which has my Flash Drives on it.

They'll Mount during Startup and remain on the Screen for a while then for No reason just up an Vanish, and when I go to mount them again they say Can't Mount Volume.

It tells me something to effect that this is probably because HAL didn't mount them.
Any Ideas?

If I have them plugged into a Hub running off my Keyboard they don't have this problem.
Or if they are plugged into my Lappy this doesn't happen...

Here's my lspi results if that helps.


rickity@daddysdell:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
rickity@daddysdell:~$ 

Thanks.... 

Well I went back and restarted copied my files unto my Desktop figuring if I formatted it that might work?
Well it didn't after that when I went to format my Flash Drive it unmounted Both of them leaving them inaccessible without a restart and It didn't even Format the one I was trying to.

Here's the gparted error report:   GParted 0.3.8

Libparted 1.8.9

Format /dev/sdc1 as ext3  00:00:54    ( ERROR )
     	
calibrate /dev/sdc1  00:00:54    ( ERROR )
libparted messages    ( INFO )
     	
Error opening /dev/sdc: No such device or address

Went back and tried to Mount the other stick and it told me It couldn't mount because it was an "INVALID Block Device".

Help I'm going Crazy with these things, I use them a lot and this having to restart every time I breath is getting QUITE Annoying. 

I could understand it if they didn't Mount During Boot, but they do and then Just decide to quit working....

       :popcorn: :KS :guitar: :popcorn: :guitar: :KS :guitar:  

After beating my head against the ](*,) for the past week or so, Posting on a number of Forums which got me little or no Help.
I decided to take my sanity in my own hands.

I started to fiddle with /etc/fstab editing the files that didn't work.
I tried another's suggestion to Copy my files onto my desktop and then Format them on Gpart, Guess what it was worse "NO MATTER" how much I restarted they wouldn't mount.

So I went back to /etc/fstab put it back to the way it was and rebooted, Still the same nothing Couldn't get them to mount no matter what...

I got to Thinking that I had one formatted to ntfs, and the other to Fat32.
I know what does that have to do with it???????????????????

Well I went back into my Wimdoze partition Formatted them to both Fat32 rebooted back into Intrepid.

Mounted like there was "NO PROBLEM"....  

Copied all my files back on them, restarted, Mounted Flawless, I unmounted and remounted several times just to be sure.

My desktop has been up now going on 4 hours now and No Problem, I've been in and out of programs and before by now they would've died.
Even been in them a number of times.

So I'd say their fixed.

Why 2 different file systems would matter I have no idea, but I guess they did???

I'm just glad they Work.

But the sad side of it is.
I couldn't fix the problem while in Linux, but instead had to use Wimdoze to solve it for me... 

So my Simple question is this.
I was planning on ditching my Wimdoze partition soon.
But how can I when I might need it to help me Fix something on my Laptop as simple as Flash Drives?

Am I saying Linux is flawed?
NO!!!!!!!!
Not near as much as Wimdoze, But when something like this is still there it's just enough to keep a possible Convert from leaving Wimdoze and coming to Linux permanently...

Unless they are as Hard Headed as the rest of us....

---


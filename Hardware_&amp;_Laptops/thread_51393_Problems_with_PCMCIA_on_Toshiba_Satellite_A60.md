---
title: "Problems with PCMCIA on Toshiba Satellite A60"
date: 2005-07-23
forum: Hardware &amp; Laptops
---

### Post by CTM on 2005-07-23
Hi :)

I've just switched to Ubuntu from Fedora Core, upon the recommendation of a couple of Ubuntu users; however I'm having trouble getting my wireless network card (Linksys WPC54G) working. Whenever I insert the card the power light is solid green, but when I remove it I get the kernel error:

PCMCIA: socket c913fc2c: *** DANGER *** unable to remove socket power

I've read up about this error and apparently it was resolved in the 2.6.11 kernel, but I'm using 2.6.11-1 and the problem persists. I'm using a Toshiba Satellite A60 laptop, if that's of any help too. If further details would be useful, please let me know what else I need to include.

Any help or advice at all would really be appreciated, because I feel like I'm going around in circles trying to solve this.

Thanks! :)

---

### Post by Declan on 2005-07-23
I don't know, but I've got the same laptop, and the same network card, which doesn't work for me either.  
When I type lspci it doesn't mention the card at all.  
Does your lspci mention it?

I began to believe that it was the computer that had a hardware difficulty,  But just to test it I formatted the disk and reinstalled a dual-boot system with Windows XP.
Since I discovered that it works on Windows XP, I can now safely conclude that it is not a hardware problem.

Does lspci pick the card up for you?
Did it work for you under Fedora?  Core 3? Core 4?

Thanks,

Declan

---

### Post by CTM on 2005-07-24
The same card didn't work for me under FC either, which led me to think that it was a  problem with the PCMCIA port. It works under WinXP though, as you said, so now I'm totally confused...

My lspci output (with the card plugged in) is:

> 
root@laptop:~ # lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device cab3 (rev 05)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4345 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 434d (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4437
0000:02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)


---


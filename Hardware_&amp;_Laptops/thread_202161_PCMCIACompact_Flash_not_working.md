---
title: "PCMCIA/Compact Flash not working"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by cyboreal on 2006-06-22
I have a Thinkpad X30 with a PCMCIA slot and a Compact Flash cardbus slot.  Both of these devices as well as the FireWire port are controlled by the Ricoh R5C552 (see here for more: [http://www.thinkwiki.org/wiki/Ricoh_R5C522](http://www.thinkwiki.org/wiki/Ricoh_R5C522)) which apparently emulates the RL5c476 (?).  lspci says this:
```
0000:01:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
0000:01:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
0000:01:00.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller
```
Firewire works - a firewire hard drive plugged in is automatically mounted.  Neither the PCMCIA nor CF slot automount a CF card (ext2) when inserted.  The output in /var/log/messages is:
```
(Insert CF card/adapter into PCMCIA slot)
pccard: PCMCIA card inserted into slot 0
cs: memory probe 0xf0000000-0xf80fffff: excluding 0xf0000000-0xf87fffff
(Remove)
pccard: card ejected from slot 0

(Insert CF card into CF slot)
pccard: PCMCIA card inserted into slot 1
(Remove)
pccard: card ejected from slot 1
```
When inserted, there are no new devices that show up under /dev (e.g. /dev/hdb1) and the device is not mounted.
```
lsmod | grep pcmcia shows:
pcmcia                 40508  0
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
```
Any idea what is missing for the PCMCIA subsystem to automatically handle CF cards and PCMCIA devices?

---

### Post by cyboreal on 2006-06-26
Still no luck troubleshooting the PCMCIA problem in Kubuntu 6.06.  I think the 
problem comes down to the transition from pcmcia-cs to pcmciautils as of 
kernel 2.6.13-rc1.  Kubuntu 6.06 has kernel 2.6.15 but both pcmcia-cs and 
pcmciautils are installed by default.  I upgraded to the latest pcmcia-cs in 
the Dapper repositories but my PC cards are still not recognized.

I tried starting cardmgr and got the following:
```
tajore@kubuntu:~$ sudo cardmgr
cardmgr[7071]: could not adjust resource: IO ports 0x100-0x3af: Function not 
implemented
cardmgr[7071]: could not adjust resource: IO ports 0x3e0-0x4ff: Function not 
implemented
cardmgr[7071]: could not adjust resource: IO ports 0x820-0x8ff: Function not 
implemented
cardmgr[7071]: could not adjust resource: IO ports 0xc00-0xcf7: Function not 
implemented
cardmgr[7071]: could not adjust resource: memory 0xc0000-0xfffff: Function not 
implemented
cardmgr[7071]: could not adjust resource: memory 0xa0000000-0xa0ffffff: 
Function not implemented
cardmgr[7071]: could not adjust resource: memory 0x60000000-0x60ffffff: 
Function not implemented
cardmgr[7071]: could not adjust resource: IO ports 0xa00-0xaff: Function not 
implemented
```
Now when I plug in a USB 2.0 PCMCIA card, the kernel recognizes it, and 
automatically mounts a USB flash drive plugged into it.  But when I plug in a CF card (ext2) 
syslog says:
```
2.6. kernels use pcmciamtd instead of memory_cs.c and do not require special 
MTD handling any more.
```
So I modprobed pcmciamtd and tried again, still no luck.  It seems that the 
pcmcia subsystem is able to handle other things, just not storage devices.  
Where do I look to get this working?  Is there a module that needs to be 
loaded or a script that is not running?

---

### Post by dankwizard on 2006-06-27
I have also received "function not implemented" when starting cardmgr with my Compaq W110 wireless PCMCIA card. After this occurs, my entire system locks. I do receive one quick message about a CPU soft loop though.

I'm running Debian with the 2.6.17 kernel. I also have both pcmcia-cs and pcmciautils installed. I'm pretty much clueless, but the problem doesn't seem to be directly related to storage.

I had the same problem with Ubuntu.

---

### Post by george_apan on 2006-06-30
Similar problems here with a PCMCIA USB Controller. I cannot mount any usb HD or DVD there. lspci gives: ```
0000:00:03.0 CardBus bridge: O2 Micro, Inc. OZ6812 Cardbus Controller (rev 05)
0000:02:00.0 USB Controller: NEC Corporation USB (rev 43)
0000:02:00.1 USB Controller: NEC Corporation USB (rev 43)
0000:02:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
```
At first I thought it was a generic usb mounting issue but the onboard usb port works OK. I reverted back to breezy because of this... Sorry I can't provide any help. Has anyone filed a bug report?

---

### Post by oceanhippie on 2007-02-22
My x30 doesn't recognize any PCMCIA cards it does recognise an Atheros Cardbus card however if you remove it the computer crashes.

I've got Orinocos, prism2, cisco. CF-PCMCIA adapater. nowt works.

This is a real problem. Can anyone tell me more infor on how the new PCMCIA system actually works so I can poke it with a stick..

Tom

---


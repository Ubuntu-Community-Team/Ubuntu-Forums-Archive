---
title: "Another DVD-RW DMA Problem"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by kommissar on 2005-04-26
I have a Plextor DVD-RW drive that know supports DMA (see the hdparm output below).  Unfortunately, doing hdparm -v /dev/hda reveals that it is not running in DMA mode.  Here is that information:

```
chris@praetorian:~$ sudo hdparm -v /dev/hda
Password:

/dev/hda:
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

To remedy this problem, I tried to edit my hdparm.conf and added in the following:
/dev/hda {
        dma = on
        io32_support = 3
}
However, this enables IO_support (seen above) but not DMA.  I even changed the name of the file from /etc/rcS.d/S07hdparm to ...S99hdparm so the devices would be initialized already on boot and it didn't work.

What can I do to get DMA enabled?  People on the forums I've read about always get it working with that command line option.


 Here is the output of hdparm -I /dev/hda
```
chris@praetorian:~$ sudo hdparm -I /dev/hda

/dev/hda:

ATAPI CD-ROM, with removable media
        Model Number:       PLEXTOR DVDR   PX-712A
        Serial Number:      ########
        Firmware Revision:  1.05
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(can be disabled)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns

```

---

### Post by hobnob on 2005-04-26
What happens when you type "sudo hdparm -d 1 /dev/hda"? Notice the "udma2*" under the "DMA capabilities"? The asterisk means that UltraDMA mode 2 is currently active.

---

### Post by kommissar on 2005-04-26
[QUOTE=hobnob]What happens when you type "sudo hdparm -d 1 /dev/hda"? Notice the "udma2*" under the "DMA capabilities"? The asterisk means that UltraDMA mode 2 is currently active.[/QUOTE]
I attempted this operation earlier.  It does not work, here is what happens:
```
chris@praetorian:~$ sudo hdparm -d 1 /dev/hda
Password:

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
chris@praetorian:~$
```

---

### Post by hobnob on 2005-04-27
Okay. Well that's a very common problem on the boards right now. The fix with the hightest rate of success is to load your specific chipset module before the more generic IDE ones. You can do this by placing it at the top of /etc/modules. So for example, mine reads:```
via82cxxx
ide-cd
ide-disk
ide-generic
lp
...
```You will have to use the correct module for your chipset, but as a starting point, you need

i) via82cxxx for a VIA chipset
ii) amd74xx for an nForce chipset

Let me know if you have any success,

---

### Post by kommissar on 2005-04-27
[QUOTE=hobnob]You will have to use the correct module for your chipset, but as a starting point, you need

i) via82cxxx for a VIA chipset
ii) amd74xx for an nForce chipset

Let me know if you have any success,[/QUOTE]

You're right, right now I am using only generic modules.  Do you happen to know which module I would use for the Intel 875P chipset?  I can't seem to find this information.

---

### Post by hobnob on 2005-04-27
Try 'piix'. Some people have had success by also shifting the ide* modules further down the list.

---

### Post by kommissar on 2005-04-27
[QUOTE=hobnob]Try 'piix'. Some people have had success by also shifting the ide* modules further down the list.[/QUOTE]
Putting piix at the top of my /etc/modules did the trick!  Thanks so much for your help; let this be a less to all with DMA problems.

---

### Post by hobnob on 2005-04-27
No problem, that's great news. : )

---

### Post by jnk on 2005-04-27
Thanks!!! :-D 

Looking for a way to solve this problem for some time now.
Adding amd74xx to /etc/modules did the trick.!!!   :mrgreen:

---

### Post by mrtaber on 2005-04-30
Just wanted to say thanks to all you, and all the other contributors in other threads.  Thanks to you, I have DMA on my combo drive :)

Thanks again,
Mark Taber

---

### Post by denzilla on 2005-04-30
[QUOTE=hobnob]What happens when you type "sudo hdparm -d 1 /dev/hda"? Notice the "udma2*" under the "DMA capabilities"? The asterisk means that UltraDMA mode 2 is currently active.[/QUOTE]

I don't believe the "*" really means thats the mode active because I was having the same issue and hdparm /dev/drivename always said DMA was off. I think it just states the max DMA mode possible.

---

### Post by hobnob on 2005-04-30
You can think of the active mode as the "type" of DMA that is available. Whether it is enabled or not is left up to the "using_dma" flag, set with "hdparm -d..."

---

### Post by amagee on 2006-04-23
Can anyone clarify how I find out what my 'chipset' is for these purposes?

---


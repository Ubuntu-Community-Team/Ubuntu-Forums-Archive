---
title: "Corsair Neutron SSD locking up machine since Ubuntu 18.04 upgrade"
date: 2018-10-04
forum: Hardware
---

### Post by Robvdl on 2018-10-04
I recently upgraded my PC from Kubuntu 16.04 to 18.04, everything is working really well but occasionally my root partition SSD (Corsair Neutron GTX) has started locking up the machine. It seems to throw the filesystem in readonly mode, here is what I get in the syslog about it:

```
Oct  4 00:25:01 rob-desktop kernel: [21333.225702] ata5.00: exception Emask 0x0 SAct 0x10 SErr 0x0 action 0x0                                                                             
Oct  4 00:25:01 rob-desktop kernel: [21333.225710] ata5.00: irq_stat 0x40000008                                                                                                           
Oct  4 00:25:01 rob-desktop kernel: [21333.225717] ata5.00: failed command: WRITE FPDMA QUEUED                                                                                            
Oct  4 00:25:01 rob-desktop kernel: [21333.225732] ata5.00: cmd 61/08:20:00:b8:07/00:00:05:00:00/40 tag 4 ncq dma 4096 out                                                                
Oct  4 00:25:01 rob-desktop kernel: [21333.225732]          res 61/04:00:00:b8:07/00:00:05:00:00/00 Emask 0x401 (device error) <F>                                                        
Oct  4 00:25:01 rob-desktop kernel: [21333.225738] ata5.00: status: { DRDY DF ERR }                                                                                                       
Oct  4 00:25:01 rob-desktop kernel: [21333.225743] ata5.00: error: { ABRT }                                                                                                               
Oct  4 00:25:01 rob-desktop kernel: [21333.226343] ata5.00: configured for UDMA/133                                                                                                       
Oct  4 00:25:01 rob-desktop kernel: [21333.226355] ata5: EH complete
```

It's only a 120gb drive, so I could replace it with something more common like a 250gb Samsung EVO, but I was just wondering why it's only happening since 18.04

This seems to be a bug, is there any recommendations people have to go about fixing this?

---

### Post by Robvdl on 2018-10-04
I could be running into something like this, though it's an older bug report.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1499726](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1499726)

---

### Post by Robvdl on 2018-10-06
I think this drive was simply dying due to old age.

The Neutron and Neutron GTX did not have a Sandforce controller, that was only the Force series, not the Neutron series.

I think the Ubuntu upgrade simply did enough writes to tip it over the edge, the drive was getting very old anyway. It came with a 5 year warranty, but it's already over that I'm sure.

Luckily I remembered I had a 256gb Samsung 860 Pro in another machine I could grab and replace later, I copied the root file system over, re-installed Grub using a live CD and it's all up and running again now.

No errors since switching to the 860 Pro, I'm pretty sure the Neutron GTX was dying and simply switching to 18.04 did enough writes to trigger it.

---

### Post by linux4me on 2018-10-06
I've been using a Corsair Neutron GTX 120 GB with 18.04 without any issues, so I suspect you may be correct that it was just a bad drive. It would be nice to see what the Disks utility reported when checking the drive's SMART data.

---

### Post by Robvdl on 2018-10-06
I still have the disk connected to my workshop machine, I can do a smart dump later on today and post it here.

---

### Post by linux4me on 2018-10-06
> **Robvdl said:**
> I still have the disk connected to my workshop machine, I can do a smart dump later on today and post it here.

Here's a screenshot of my working drive's SMART self-test to compare to:

---


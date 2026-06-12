---
title: "SATA PCI Card VT6421 hangs on boot when HD attached"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by JohnDear on 2007-08-16
Hello,

I'll just start my post like everyone else, first post, Linux newbie :-)
I have a problem getting an SATA PCI card to work. I ordered this card (for the added benefit of the IDE port): [http://www.newegg.com/product/product.asp?item=N82E16815280001](http://www.newegg.com/product/product.asp?item=N82E16815280001)
It says in the description: ALI M5283 SATALink PCI Host Controller 

So I looked it up, and here ([http://linuxmafia.com/faq/Hardware/sata.html#uli](http://linuxmafia.com/faq/Hardware/sata.html#uli)) it said:
> ULi Electronics, Inc. (formerly ALi) M1573 South Bridge and M5285, M5283, and M5281 SATA-I bridge chips  &#8212; fakeraid. libata driver "sata_uli". Driver is now production quality.
Hey, sounds good, cheap and works with Linux. Nice...

Now the card arrived and I looked on the board and the chip has "VT6421" printed on it. Ouch, now what? That doesn't look like the ALi chipset but like ViA. Now here ([http://linuxmafia.com/faq/Hardware/sata.html#via6421](http://linuxmafia.com/faq/Hardware/sata.html#via6421)) it says:
VIA Technologies, Inc. VT6421 and VT6421L PCI chips &#8212; fakeraid. A libata-dev patch was posted on 2005-02-06. 
(there is a link to [http://lwn.net/Articles/122290/](http://lwn.net/Articles/122290/))
Now, what does that mean for me?

If I install a drive on the controller, it hangs at the ubuntu screen with the progress bar. I don't know how I can show the log why it hangs or post a device log? I see a SCSI Host Adapter with the key info.linux.driver and value sata_via - sounds like it is found properly but still hangs during boot.

```
lshw output is:
           *-storage
                description: RAID bus controller
                product: VT6421 IDE RAID Controller
                vendor: VIA Technologies, Inc.
                physical id: 6
                bus info: pci@01:06.0
                logical name: scsi1
                logical name: scsi2
                logical name: scsi3
                version: 50
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list scsi-host
                configuration: driver=sata_via latency=64
                resources: ioport:dfa0-dfaf ioport:df90-df9f ioport:df80-df8f ioport:df60-df6f ioport:df40-df5f ioport:d800-d8ff irq:18
```

Does anyone know what I can do?

Thanks
John

---

### Post by JohnDear on 2007-08-17
Well, I figured it out myself - at least more or less. I connected the hard drive to the other SATA connector on the card and everything is fine.
So, the card is probaqbly bad, which sucks but at least I know I can get it to work...

---


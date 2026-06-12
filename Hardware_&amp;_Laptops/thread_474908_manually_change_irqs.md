---
title: "manually change irqs"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by rotalever on 2007-06-15
Well, how can I change/set the IRQs manually? Why? Because I get IRQ problems with my USB 2.0 PCI card and my grapics card. There are enough free IRQs but the kernel (?) always shares them...
```

0:    3026360    XT-PIC-XT        timer
  1:       4766    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  8:          3    XT-PIC-XT        rtc
  9:          1    XT-PIC-XT        acpi
 10:     522338    XT-PIC-XT        uhci_hcd:usb2, eth0, CMI8738-MC6
 11:    1864570    XT-PIC-XT        uhci_hcd:usb1, ehci_hcd:usb3, nvidia
 12:     659791    XT-PIC-XT        i8042
 14:      62244    XT-PIC-XT        ide0
 15:     294504    XT-PIC-XT        ide1


```

(free irqs: 3,4,5,6,7,13)

---

### Post by CrispyFried on 2007-06-15
3,4,7,and 12 may be reserved via the bios. go into the bios and if you dont use then disable serial ports 1 and 2, the parallel port and the ps/2 port. those may be whats on 3,4,7 and 12.

while in the bios also look for  "legacy ISA devices" (set to "no") or "reserve ints for non pnp devices" (set to "no"). you can also try changing "pnp os installed" to the other value, but try the other stuff 1st.

you can also (in the bios) change (to a point) what ints are assigned to what card slots, but that can be hit or miss.

---

### Post by rotalever on 2007-06-15
No, both serial ports and parallel port and onboard usb and all other onboard features I dont need are disabled. I think I have tested every little bios option, there is no way. I must set the irqs manually.

---

### Post by CrispyFried on 2007-06-15
can you change in ints assigned to the card slots? the vid cards int will probably still get shared but maybe with a more friendly device.

how about moving the usb card (if its an add in card)?

---

### Post by rotalever on 2007-06-15
> **CrispyFried said:**
> can you change in ints assigned to the card slots? the vid cards int will probably still get shared but maybe with a more friendly device.

Sorry, but I do not understand what you mean by this.
> **CrispyFried said:**
> 
how about moving the usb card (if its an add in card)?
Does not work, it is a question of the OS. It has nothing to do with the BIOS. For example, in Windows, if the EHCI driver is not installed, everything is fine. But if I install the EHCI, which is needed, EHCI gets an IRQ shared with the graphics card. Similar on linux.

---

### Post by CrispyFried on 2007-06-15
if your usb 2.0 adapter is a pci add on card, move it to different slots, the slots can use different irqs. 

in the bios you can usually change which irq is assigned to each slot. it will be something like "slot 1 - irq A" .. change the "a" to "b" etc.

for instance many times agp and the nearest slot share the same irq.

linux should read the bios for lots of info concerning irqs when setting up what uses what.

---

### Post by rotalever on 2007-06-15
> **CrispyFried said:**
> if your usb 2.0 adapter is a pci add on card, move it to different slots, the slots can use different irqs. 

in the bios you can usually change which irq is assigned to each slot. it will be something like "slot 1 - irq A" .. change the "a" to "b" etc.

for instance many times agp and the nearest slot share the same irq.

linux should read the bios for lots of info concerning irqs when setting up what uses what.

Well, in theory this can be true, but we are talking about the real world ;)
Moving to different slot DOES NOT WORK, as I said before, I've tried it.
Setting IRQ in the BIOS for the card DOES NOT WORK, because the card has 3 IRQs: uhci usb1+usb2 and ehci and in addition, the OS does NOT care about BIOS settings.
And it has nothing to do with my PCI card, because I tried another one before with a different chip.

Isnt there a way to change IRQs manually?

---

### Post by CrispyFried on 2007-06-15
> **rotalever said:**
> 
Isnt there a way to change IRQs manually?

not that I can see, at least in general. some device drivers can but its driver dependent.

thats why Ive been focusing on the bios ;) its always been able to change irq assignments for me before.  

you can give booting with "noacpi" or "noprobe" a shot. never tried though.

---

### Post by rotalever on 2007-06-15
> **CrispyFried said:**
> 
you can give booting with "noacpi" or "noprobe" a shot. never tried though.
Thanks, sounds good. I will give it a try tomorrow. Automatic shutdown etc. will not work then, but if everything else is fine, that would be good.

---

### Post by rotalever on 2007-06-16
I tried pci=noacpi: Every IRQ is still the same, except for the graphic card, it has got no IRQ  :-(
I tried noprobe: No effect.

The options were tried with Plug & Play OS disabled in BIOS.

---

### Post by CrispyFried on 2007-06-16
drag..

ok couple more things to try..

I know I sound like a broken record but I still think the bios is the key. I went through more or less what you have (shared irq with video) a couple years ago and playing with the bios did it.

set p&p os to "yes" that should tell the bios to let linux set most irqs etc. some bios still set some things though.

also in the bios reset the escd, thats where the bios stores p&p settings for reuse on boots, it will force the bios to go through all p&p devices again and possibly do them different.

you could try the "nousb" boot option, it would obviously not load the usb support but by loading it manually or via script after it fully boots and everything else has been assigned may force it to use different irqs. not sure how to do that though.

done some looking and I cant find anyway to force linux to use particular irqs. that seems to be via the drivers, so if they dont offer the option, youre sol. kinda be nice as I tend to runs lots of add in cards and will probably run it this problem again myself.

EDIT: found an interesting command: setpci .. seems to allow you to change stuff like irqs. looks pretty hardcore though.

---

### Post by rotalever on 2007-06-16
> **CrispyFried said:**
> 
EDIT: found an interesting command: setpci .. seems to allow you to change stuff like irqs. looks pretty hardcore though.

Hmm, but how does it work, I know my device ID and then? How to change IRQ settings with it?

---

### Post by CrispyFried on 2007-06-16
that command is way way beyond me.. its programming down to the metal.

what does "sudo lspci -b -vv | grep Interrupt" show? heres mine

```
dave@M2010:~$ sudo lspci -b -vv |grep Interrupt
        Interrupt: pin A routed to IRQ 10
        Interrupt: pin A routed to IRQ 10
        Interrupt: pin B routed to IRQ 3
        Interrupt: pin C routed to IRQ 4
        Interrupt: pin D routed to IRQ 3
        Interrupt: pin A routed to IRQ 255
        Interrupt: pin B routed to IRQ 5
        Interrupt: pin B routed to IRQ 5
        Interrupt: pin B routed to IRQ 5
        Interrupt: pin A routed to IRQ 10
        Interrupt: pin A routed to IRQ 4
        Interrupt: pin A routed to IRQ 255
        Interrupt: pin C routed to IRQ 4
dave@M2010:~$              
```

I ask because my notebook just loves irqs 3,4 and 5 which are listed as unused on yours. so it seems linux has no problem using them. not sure why yours are being ignored. my network, audio, usb (my usb is on 3,4 and 10) and a bunch of other junk is hanging on those irqs.

the 255 irq is from an unknown device which gave garbage.

---

### Post by rotalever on 2007-06-16
Hmm, this is something I've never thought of...
```

cat /proc/interrupts 
           CPU0       
  0:    9288556    XT-PIC-XT        timer
  1:      16755    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  8:          3    XT-PIC-XT        rtc
  9:          1    XT-PIC-XT        acpi
 10:    1210119    XT-PIC-XT        uhci_hcd:usb2, eth0, CMI8738-MC6
 11:    3002797    XT-PIC-XT        uhci_hcd:usb1, ehci_hcd:usb3, nvidia
 12:    1746063    XT-PIC-XT        i8042
 14:     317905    XT-PIC-XT        ide0
 15:     649884    XT-PIC-XT        ide1
NMI:          0 
LOC:          0 
ERR:         53
MIS:          0

lspci -b -vv | grep Interrupt
        Interrupt: pin A routed to IRQ 255
        Interrupt: pin A routed to IRQ 11
        Interrupt: pin B routed to IRQ 10
        Interrupt: pin C routed to IRQ 255
        Interrupt: pin A routed to IRQ 10
        Interrupt: pin A routed to IRQ 255


```

edit: As far as I remember serial ports etc. used the 3,4,5 IRQs before I disabled them in BIOS. But on Windows, the graphics card and the USB 2.0 PCI thing are assigned to IRQ 4 and 5 (same problem as in linux, but with different IRQs..). With this, I mean, those IRQs arent blocked by the BIOS or so.

---

### Post by IntuitiveNipple on 2007-06-16
**CrispyFried** is absolutely correct in saying that the slot the PCI cards are plugged into will affect which IRQ's are used by each card. 

Your motherboard manual should have information on which slots use/share which PCI IRQs. Very often the AGP slot shares with PCI slot 3. I had a very similar issue with an Asus A7M266-D where every slot had a card in it. Eventually by studying the information in the manual I was able to work out an arrangement whereby the cards that caused IRQ sharing conflicts were on separate PCI IRQ pins.

That was a Windows server set-up with RAID controller. Later Windows was replaced by GNU/Linux,

The default IRQ assignments are read from the DSDT table in the BIOS each time the PC starts. Linux, and Ubuntu in particular, make it extremely easy to install a custom DSDT. There is a section of the DSDT (_PRT I seem to recall) that describes the IRQ assignments. The ESCD saved in non-volatile RAM is also read to find out how the BIOS has assigned resources for devices not being handled by the OS Plug-and-Play discovery.

You could check the ACPI specification v3.0 and compare it against the (decompiled) DSDT of your PC. It *may* be possible to adjust the IRQ assignments by editing the DSDT.dsl and then recompiling and installing it.

For an example of how that was done to correct a BIOS DSDT battery bug, see my recent post [ACPI: battery-technology reported as non-rechargable](http://ubuntuforums.org/showthread.php?t=475801). Scroll to the end of the article for the information of manipulating the DSDT.

---

### Post by CrispyFried on 2007-06-16
> **IntuitiveNipple said:**
> [b]
The default IRQ assignments are read from the DSDT table in the BIOS each time the PC starts. Linux, and Ubuntu in particular, make it extremely easy to install a custom DSDT. There is a section of the DSDT (_PRT I seem to recall) that describes the IRQ assignments. The ESCD saved in non-volatile RAM is also read to find out how the BIOS has assigned resources for devices not being handled by the OS Plug-and-Play discovery.

You could check the ACPI specification v3.0 and compare it against the (decompiled) DSDT of your PC. It *may* be possible to adjust the IRQ assignments by editing the DSDT.dsl and then recompiling and installing it.


very interesting. I looked at mine and at the IPRA-IPRH list those irqs that lspci gave me were there. several were duplicated (irq 3 was uses 3 times, irq 4 was used twice etc). might be possible to replace the duplicated ones with unused irqs.

@rotalever:

your lspci output seems to indicate that PCI bus irq "D" is not used.. did you try the usb card in **every** slot?

---

### Post by rotalever on 2007-06-17
> **CrispyFried said:**
> your lspci output seems to indicate that PCI bus irq "D" is not used.. did you try the usb card in **every** slot?
No, this is not possible, because My graphics card is very big...

---

### Post by rotalever on 2007-06-17
I looked as the DSDT thing... The decompiled DSDT.dsl contains someting like this
```

          Name (PICM, Package (0x1E)
            {
                Package (0x04)
                {
                    0x0005FFFF, 
                    0x00, 
                    \_SB.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0005FFFF, 
                    0x01, 
                    \_SB.LNKC, 
                    0x00
                }, 

[...]

```
I think this has something to do with IRQs?I think is has something to do with it, because of
```

Method (_PRT, 0, NotSerialized)
            {
                Return (PICM)
            }

```

But now, what can I do? For me this is very complicated.

---

### Post by CrispyFried on 2007-06-17
back to the bios then :)

you should be able to change what PCI irq (A,B,C or D) is assigned to what slot in the bios.  you need to get D on the slot your usb card uses. this is how I fixed my similar problem as I also had cards that need to be in particular slots due to cabling and size, by moving irqs around to various slots. takes time as there are a ton of combinations.

---

### Post by CrispyFried on 2007-06-17
> **rotalever said:**
> I looked as the DSDT thing... The decompiled DSDT.dsl contains someting like this


search for "IPRA", that will put you near the beginning of the area where the irqs are listed. its a list of the irqs that are assigned to the pci bus. this is where I think the irq value would be changed. you still cant manually assign an irq to a particular device, its a pool  that linux can draw from to assign the device an irq on its own. but by changing some of the duplicates to your unused irqs it may use them and not double and triple up on the 2 irqs irqs its  got now.

heres mine

```

                Name (IPRA, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {10}
                })
                Name (IPRB, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {5}
                })
                Name (IPRC, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {4}
                })
                Name (IPRD, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {3}
                })
                Name (IPRE, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {11}
                })
                Name (IPRF, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {3}
                })
                Name (IPRG, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {4}
                })
                Name (IPRH, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {3}
                })
    
                    }
```

Im sure that giving a wrong or used irq is a sure fire way to stop the kernal dead in its tracks when booting so be careful. when I get more time Ill have to experiment by dropping an irq and see if it doesnt use it.

---

### Post by IntuitiveNipple on 2007-06-17
A note of caution. Although the DSDT can give you some insights I'd not recommend changing anything unless you are 100% sure the DSDT *has a bug in it* related to the IRQs.

Don't play around with it unless you fully understand what you are doing and what the potential knock-on effects might be - I don't recommend this as a solution unless you're a skilled engineer.

Also, the names used in the decompiled DSDT are mostly arbitrary and specific to each manufacturer. Some names beginning with an underscore are defined in the ACPI specification.

---

### Post by CrispyFried on 2007-06-17
I just went to my bios under "PnP PCI configuration" and under PIRQ0-PIRQ3 (I called it A-D before) I can manually assign what irq to use. see if you can select 3,4,5 etc there. its probably worded a bit different in your bios though. my choices were 3,4,5,7,9,10,11. these are what the PCI cards can chose from. 

that is with an asus mobo with award bios but cant remember the model.

---

### Post by rotalever on 2007-06-17
Thanks for the warnings ;)
"IPRA" does not exist in the whole document, but I have found those device sections:
Device (PCI0)
Device (PCI1)
Device (IDE0)
Device (PS2K)
...

There are two PCI devices, PCI0 and PCI1. For me, it looks like if PCI1 is only linked to LNKA and LNKB
```

Name (PICM, Package (0x02)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        \_SB.LNKA, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        \_SB.LNKB, 
                        0x00
                    }
                })
                Method (_PRT, 0, NotSerialized)
                {
                    Return (PICM)
                }

```
But PCI0 is linked to A,B,C and D and is also somewhat more complicated. I dont know if this is the key but maybe you know...

```

Device (PCI0)
        {
            Name (_HID, EisaId ("PNP0A03"))
            Name (_ADR, 0x00)
            Name (CRES, ResourceTemplate ()
            {
                WordBusNumber (ResourceProducer, MinFixed, MaxFixed, PosDecode,
                    0x0000,             // Granularity
                    0x0000,             // Range Minimum
                    0x00FF,             // Range Maximum
                    0x0000,             // Translation Offset
                    0x0100,             // Length
                    ,, )
                IO (Decode16,
                    0x0CF8,             // Range Minimum
                    0x0CF8,             // Range Maximum
                    0x01,               // Alignment
                    0x08,               // Length
                    )
                WordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                    0x0000,             // Granularity
                    0x0000,             // Range Minimum
                    0x0CF7,             // Range Maximum
                    0x0000,             // Translation Offset
                    0x0CF8,             // Length
                    ,, , TypeStatic)
                WordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                    0x0000,             // Granularity
                    0x0D00,             // Range Minimum
                    0xFFFF,             // Range Maximum
                    0x0000,             // Translation Offset
                    0xF300,             // Length
                    ,, , TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000A0000,         // Range Minimum
                    0x000BFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00020000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C8000,         // Range Minimum
                    0x000DFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00018000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x00100000,         // Range Minimum
                    0xFFBFFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0xFFF00000,         // Length
                    ,, _Y05, AddressRangeMemory, TypeStatic)
            })
            Method (_CRS, 0, NotSerialized)
            {
                CreateDWordField (CRES, \_SB.PCI0._Y05._MIN, RAMT)
                CreateDWordField (CRES, \_SB.PCI0._Y05._LEN, RAMR)
                Store (MEMS (), RAMT)
                ShiftLeft (RAMT, 0x14, RAMT)
                Subtract (0xFFBFFFFF, RAMT, RAMR)
                Increment (RAMR)
                Return (CRES)
            }

            Device (NB)
            {
                Name (_ADR, 0x00)
                OperationRegion (S2K, PCI_Config, 0x92, 0x01)
                Field (S2K, ByteAcc, NoLock, Preserve)
                {
                        ,   7, 
                    STPG,   1
                }
            }

            Name (PICM, Package (0x1E)
            {
                Package (0x04)
                {
                    0x0005FFFF, 
                    0x00, 
                    \_SB.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0005FFFF, 
                    0x01, 
                    \_SB.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000CFFFF, 
                    0x00, 
                    \_SB.LNKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000CFFFF, 
                    0x01, 
                    \_SB.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000CFFFF, 
                    0x02, 
                    \_SB.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000CFFFF, 
                    0x03, 
                    \_SB.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000DFFFF, 
                    0x00, 
                    \_SB.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000DFFFF, 
                    0x01, 
                    \_SB.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000DFFFF, 
                    0x02, 
                    \_SB.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000DFFFF, 
                    0x03, 
                    \_SB.LNKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000EFFFF, 
                    0x00, 
                    \_SB.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000EFFFF, 
                    0x01, 
                    \_SB.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000EFFFF, 
                    0x02, 
                    \_SB.LNKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000EFFFF, 
                    0x03, 
                    \_SB.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000FFFFF, 
                    0x00, 
                    \_SB.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000FFFFF, 
                    0x01, 
                    \_SB.LNKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000FFFFF, 
                    0x02, 
                    \_SB.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x000FFFFF, 
                    0x03, 
                    \_SB.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0010FFFF, 
                    0x00, 
                    \_SB.LNKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0010FFFF, 
                    0x01, 
                    \_SB.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0010FFFF, 
                    0x02, 
                    \_SB.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0010FFFF, 
                    0x03, 
                    \_SB.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0011FFFF, 
                    0x00, 
                    \_SB.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0011FFFF, 
                    0x01, 
                    \_SB.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0011FFFF, 
                    0x02, 
                    \_SB.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0011FFFF, 
                    0x03, 
                    \_SB.LNKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0012FFFF, 
                    0x00, 
                    \_SB.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0012FFFF, 
                    0x01, 
                    \_SB.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0012FFFF, 
                    0x02, 
                    \_SB.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0012FFFF, 
                    0x03, 
                    \_SB.LNKD, 
                    0x00
                }
            })
            Method (_PRT, 0, NotSerialized)
            {
                Return (PICM)
            }

            Device (PCI1)
            {
                Name (_ADR, 0x00010000)
                Method (_S1D, 0, NotSerialized)
                {
                    Return (0x01)
                }

                Method (_PRW, 0, NotSerialized)
                {
                    Return (SPRW (0x0B))
                }

                Name (PICM, Package (0x02)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        \_SB.LNKA, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        \_SB.LNKB, 
                        0x00
                    }
                })
                Method (_PRT, 0, NotSerialized)
                {
                    Return (PICM)
                }
            }

```

---

### Post by CrispyFried on 2007-06-17
> **IntuitiveNipple said:**
> A note of caution. Although the DSDT can give you some insights I'd not recommend changing anything unless you are 100% sure the DSDT *has a bug in it* related to the IRQs.

Don't play around with it unless you fully understand what you are doing and what the potential knock-on effects might be - I don't recommend this as a solution unless you're a skilled engineer.



and you have a live boot cd to fix it when the kernal blows up, heh. Im the curious sort so Im sure Ill play with it when I get some free time (and Im overconfident about my ability to fix it after - good combo eh?). your battery post was most informative. I run lots of add in cards so Im sure whatever I learn will serve me well down the road.

I too would rather find out why those free irqs arent being used, I think the bios is the key.

---

### Post by CrispyFried on 2007-06-17
I dont think the dsdt is the real problem. as IntuitiveNipple said, unless its broke its very dangerous to play with. 

something is preventing linux (and/or dsdt) from seeing your unused irqs. much better to find out why.

can you choose irqs 3,4,5 etc from your "PnP PCI configuration" in the bios (see my other post when I actually went into my bios)? what choices are there?

---

### Post by IntuitiveNipple on 2007-06-17
From the ACPI specification V3.0:
> 6.2.11 _PRT (PCI Routing Table)
PCI interrupts are inherently non-hierarchical. PCI interrupt pins are wired to interrupt inputs of the interrupt controllers. The _PRT object provides a mapping from PCI interrupt pins to the interrupt inputs of the interrupt controllers. The _PRT object is required under all PCI root bridges. _PRT evaluates to a package that contains a list of packages, each of which describes the mapping of a PCI interrupt pin.
Note: The PCI function number in the Address field of the _PRT packages must be 0xFFFF, indicating “any” function number or “all functions”.
The _PRT mapping packages have the fields listed in Table 6-12.

It goes on for a couple of pages so I'd suggest you download and digest at least that section if not considerable chunks of the introduction and explanation sections so you understand what is going on.

You can get it from the [Advanced Configuration & Power Interface](http://www.acpi.info/) web-site.

---

### Post by IntuitiveNipple on 2007-06-17
I thought it would be a good idea to refocus on the original report:
> **rotalever said:**
> Well, how can I change/set the IRQs manually? Why? Because I get IRQ problems with my USB 2.0 PCI card and my grapics card. There are enough free IRQs but the kernel (?) always shares them..
From that it is clear the issue here is ***not*** OS allocated IRQs in the APIC (Advanced Programmable Interrupt Controller).

The issue is the hard-wired routing of the INTerrupt pins on the motherboard, something I doubt even messing with the DSDT will address.

This goes back to the points **CrispyFried** and I made about slots. 
 You really need to get hold of the details of how your motherboard has allocated the sharing of the hard-wired PCI INTerrupts. What motherboard and revision is it? Precisely what cards have you got in which slots (slot numbering starts from the AGP slot) ?

Here's the notes of the issue I had:
> [quote]The 33 MHz, 32 bit PCI slots on any AMD dually, suffer from a latency issue, which throttles their effective bandwidth to about 40 MB/s (should be about 133 MB/s.) For most peripherals, this doesn't matter, because they never need that much bandwidth, but disk controllers really will use that much bandwidth and their performance will suffer, if put in a 33 MHz, 32 bit PCI slot. If you leave it in a 66 MHz, 64 bit slot (even if it actually runs at 33 MHz, 32 bit), then it won't be strangled by the chipset's latency issue and will get its entire 133 MB/s bandwidth, there.

This solved my stuttering audio and video problems on an Asus A7M266D that is fully populated with PCI cards, with Windows 2003 Server Enterprise Edition, Service Pack 1. 

It has dual Athlon MP 2000 CPUs, 2GB RAM, onboard CMI-8738 audio plus:
AGP Matrox Millenium G450 Dual-Head 
PCI slot 1: 32-bit 66MHz Promise Fastrak TX2000 RAID 0/1
PCI slot 2: 64-bit 66MHz Intel Pro/100S Dual Port Ethernet
PCI slot 3: 32-bit 33MHz Asus USB 2 Host
PCI slot 4: 32-bit 33Mhz Firewire (IEEE1394) Host
PCI slot 5: 32-bit 33Mhz Hauppauge WinTV 878/9

This is the final working solution. Before this, I had the Fastrak RAID controller (with 4x 60GB disk to form a stripped/mirrored 120GB array) in slot 5, and later slot 4. 

I was experiencing a lot of PCI latency popping & stuttering with audio and with the WinTV card (from an external camera on the composite input) when the disks were being used hard (such as an anti-virus scan).

I had been trying many PCI latency settings using the freeware PCI Latency Tool 3 but couldn't completely solve the problems. Then I found the quoted paragraph about the PCI 32-bit bus being throttled. 

I moved the Intel Pro dual-port from slot 2 to 3 (shares resources with the AGP slot), moved the Fastrak from slot 4 (which doesn't share its INT-C interrupt) to slot 1, and moved the Firewire host to slot 4. 

After restarting the first thing I noticed was the Windows start-up sound was perfect (previously it was hidiously stuttering). I then started a manual anti-virus scan and then started MusicMatch jukebox.
Its start-up sound used to be badly broken, but now it was perfect. 
Playing audio tracks whilst the a/v scan is going is now perfect, and at the same time I am transmitting the composite video camera signal from the WinTV card out to a streaming server on the Internet. 

Everything appears to be perfect - no stuttering of any kind. 

I'm running the system with the PCI Latency values I had set previously, which I found gave the best results. They are: all devices set to 160 except the PCI bridges (set to 0), the AGP card set to 128, and the CMI audio set to 248. 

After this soak test I shall not use the latency settings, allowing all devices to take the default set by the BIOS (32).[/quote]

---

### Post by rotalever on 2007-06-17
My motherboard is the old ASUS A7V266. I remember its revision as 1.06 but I am not sure.
It has got 1x AGP, 5xPCI, 1xACR
AGP: Nvidia GF6800GS
PCI1-3: Hidden by the cooler of the graphics card
PCI4: USB 2.0
PCI5: Ethernet 100MBit Intel

edit: I use onboard Sound. Mouse and keyboard is PS/2. Parallel port and serial ports are disabled. Onboard USB is disabled to free even more IRQs. Both IDE ports are used. The processor is AMD XP2200+.

I am not sure, but I think this mainboard does not have an APIC.

I looked into the BIOS once again, there is no way to change something like "PIRQ". I can assign IRQs to the PCI slots: 1/5 , 2, 3, 4. For each of them I can choose one IRQ or "AUTO" or "NA". 2,3 are set to NA because they are empty and 1/5 and 4 are set to AUTO.

---

### Post by IntuitiveNipple on 2007-06-17
If it were me I'd toss the graphics card away! Any card that is so inconsiderate as to obstruct more than 50% of the slots in a system is not something I'd want around :)

---

### Post by rotalever on 2007-06-17
> **IntuitiveNipple said:**
> If it were me I'd toss the graphics card away! Any card that is so inconsiderate as to obstruct more than 50% of the slots in a system is not something I'd want around :)
Well, the original cooler is over one PCI slot. But I constructed my own cooler with an 80mm fan...

---

### Post by IntuitiveNipple on 2007-06-17
In that case I suspect  you would make better progress by rethinking the cooling option so you can free up those additional 2 slots rather than trying to mess about with the PCI interrupts. I doubt even I would make progress in changing things around at the software end.

---

### Post by rotalever on 2007-06-17
No I need a silent system. But before, where the new cooler was not applied, I tried the card in different slots and nothing changed, as I said some posts before. So it wouldnt help to change the graphics card etc.

---

### Post by CrispyFried on 2007-06-17
> **rotalever said:**
> 
AGP: Nvidia GF6800GS
PCI1-3: Hidden by the cooler of the graphics card
PCI4: USB 2.0
PCI5: Ethernet 100MBit Intel

I looked into the BIOS once again, there is no way to change something like "PIRQ". I can assign IRQs to the PCI slots: 1/5 , 2, 3, 4. For each of them I can choose one IRQ or "AUTO" or "NA". 2,3 are set to NA because they are empty and 1/5 and 4 are set to AUTO.

what choice of irqs does it give? just one? my bios gave me a ton, especially after disabling serial, parallel etc ports as those irqs were then able to be used in the pci slots. why yours dont is a mystery and probably part of the problem - they should be. you definately want to take it off "auto" and mess around with the values, even the ones that you set to "NA".. try giving them irqs as it may shuffle things around.

edit: I grabbed the manual for your mobo. in the section on pci slots it has the table as to what irqs (A-D) goes to what slot, and it list a whole pile of irqs available for each pci slot, not just one. also, is the acr riser disabled(it shares its irq with the agp slot)? there is also a jumper on the mobo that disables an onboard usb port.. maybe its grabbing something.

heres your layout. it looks like slots 4 and 5 should be ok **if **you can give all the slots unique irqs. 

```
                          INT-A  INT-B  INT-C INT-D
PCI slot 1                 —      —      —    sharedf
PCI slot 2               shared   —      —     —
PCI slot 3                 —    shared   —     —
PCI slot 4                 —      —     used   —
PCI slot 5                 —      —      —   shared
AGPPro slot              shared shared   —     —
ACR slot                 shared   —      —     —
Onboard audio controller   —    shared   —     —
Onboard USB controller     —      —      —   shared

```



whats in the Resource Exclusion section? anything reserved there?

---

### Post by rotalever on 2007-06-18
> **CrispyFried said:**
> 
whats in the Resource Exclusion section? anything reserved there?
I think they mean the ISA section(my Mobo has no ISA... weird). However, nothing is reserved. But why does this card want to have more than one IRQ?

---

### Post by CrispyFried on 2007-06-18
each device on a card can ask for its own irq, so the 3 usb controllers on your usb card each get one. 

if you change the slots that are NA to AUTO does anything change irq wise?

---

### Post by rotalever on 2007-06-18
I tried setting IRQs manually again..
PCI 1/5 - #10
PCI 2 - #4
PCI 3 - #5
PCI 4 - #7 and #11 give same results

It is a bit better, but the EHCI driver always has the same IRQ as the graphics card:
```

cat /proc/interrupts 
           CPU0       
  0:      19515    XT-PIC-XT        timer
  1:         69    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  4:       4092    XT-PIC-XT        ehci_hcd:usb3, nvidia
  5:        812    XT-PIC-XT        CMI8738-MC6
  8:          3    XT-PIC-XT        rtc
  9:          1    XT-PIC-XT        acpi
 10:        164    XT-PIC-XT        uhci_hcd:usb2, eth0
 11:          0    XT-PIC-XT        uhci_hcd:usb1
 12:        471    XT-PIC-XT        i8042
 14:       8171    XT-PIC-XT        ide0
 15:        993    XT-PIC-XT        ide1

```
I will try other combinations later..

---

### Post by rotalever on 2007-06-18
Ok, whatever I do the ehci driver always shares an IRQ with the graphics card. It is the same on windows.

---

### Post by IntuitiveNipple on 2007-06-18
> **CrispyFried said:**
> 
```
                          INT-A  INT-B  INT-C INT-D
PCI slot 1                 &#8212;      &#8212;      &#8212;    sharedf
PCI slot 2               shared   &#8212;      &#8212;     &#8212;
PCI slot 3                 &#8212;    shared   &#8212;     &#8212;
PCI slot 4                 &#8212;      &#8212;     used   &#8212;
PCI slot 5                 &#8212;      &#8212;      &#8212;   shared
AGPPro slot              shared shared   &#8212;     &#8212;
ACR slot                 shared   &#8212;      &#8212;     &#8212;
Onboard audio controller   &#8212;    shared   &#8212;     &#8212;
Onboard USB controller     &#8212;      &#8212;      &#8212;   shared

```
You know what? From your experience and the table above I think the slots are numbered in reverse!

You are finding that AGP and slot 4 (counting from the AGP end) are sharing. The table above says AGP and slot-2 share an interrupt.

For some reason the table seems to have its slot-numbering inverted.

Try this revised table:
```
                          INT-A  INT-B  INT-C INT-D
AGPPro slot              shared shared   &#8212;     &#8212;        AGP Video
PCI slot 1                 &#8212;      &#8212;      &#8212;   shared     *covered*
PCI slot 2                 &#8212;      &#8212;     used   &#8212;        *covered*
PCI slot 3                 &#8212;    shared   &#8212;     &#8212;        *covered*
PCI slot 4               shared   &#8212;      &#8212;     &#8212;
PCI slot 5                 &#8212;      &#8212;      &#8212;   shared
ACR slot                 shared   &#8212;      &#8212;     &#8212;
Onboard audio controller   &#8212;    shared   &#8212;     &#8212;
Onboard USB controller     &#8212;      &#8212;      &#8212;   shared

```
According to this table your USB 2.0 adapter in slot-4 is sharing an interrupt with AGP which matches everything you've experienced.

---


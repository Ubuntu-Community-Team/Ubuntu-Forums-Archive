---
title: "How much memory can my PC take?"
date: 2010-12-08
forum: Hardware
---

### Post by DrPL on 2010-12-08
Hi,
I bought a reconditioned PC with 1/2 GB of memory; however, this does not seem to be enough and very soon my PC is grinding to a standstill. I am looking to upgrade but have run into a problem. Although I know the make of my PC, when I checked the memory as is against what the original specs were, it is clear that the PC's motherboard has been upgraded. I have looked at the motherboard to see if it has any markings but I think they are all underneath the board, which makes it difficult to know what the serial number is without taking the CPU, fan assembly off too.
I was wondering if there was an application that could tell me how much memory the board could accommodate (I think there are applications for windows).

I borrowed 1 GB of memory from a friend - the pin number, speed etc all seemed to match what was on the memory in my PC, so I installed it, with 1/4 GB DIMM and 1 GB DIMM.
When I went to boot up, nothing appeared on the screen, but I got a two-tone siren, repeated a few times which I found out means that the CMOS needs updating.

At this point, I reverted to 2x1/4 GB DIMM as I am straying into unknown territory. Can someone suggest how to proceed?

Best wishes

Paul

---

### Post by Fafler on 2010-12-09
The bootup screen, before Ubuntu loads, should tell you what board you have. How many memory sockets does it have? And what kind of memory does it use?

If you can't figure out what board you have, you can identify the chipset with this command:
```
lspci | grep Host
```

Post the output here.

---

### Post by mastablasta on 2010-12-09
> **DrPL said:**
> When I went to boot up, nothing appeared on the screen, but I got a two-tone siren, repeated a few times which I found out means that the CMOS needs updating. 

 
also this could mean that bios update might solve your issues.

---

### Post by mick222 on 2010-12-09
Can you get into the bios usually press del or f2 at post this will let you know what bios you have. 
  The beeps can mean different things with different bioses so check against this table. [http://www.biosflash.com/e/bios-beeps.htm](http://www.biosflash.com/e/bios-beeps.htm)
  Sounds like it could be a problem with the memory or i have heard of some usb devices causing this.
 Could also be the cmos battery you could try replacing that.
Just noticed you should only use memory sticks of the same type and size so remove the 256 mb stick and try with the 1gb only.

---

### Post by DrPL on 2010-12-09
> **Fafler said:**
> The bootup screen, before Ubuntu loads, should tell you what board you have. How many memory sockets does it have? And what kind of memory does it use?

If you can't figure out what board you have, you can identify the chipset with this command:
```
lspci | grep Host
```Post the output here.


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)

It uses 128 pin DDR, 333 MHz chipset memory boards.

---

### Post by coffeecat on 2010-12-09
> **DrPL said:**
> I have looked at the motherboard to see if it has any markings but I think they are all underneath the board, which makes it difficult to know what the serial number is without taking the CPU, fan assembly off too.

Run this from a terminal:

```
sudo lshw > Desktop/lshw.txt
```A file called lshw.txt will appear on your desktop. Open it in a text editor and near the beginning you should see a section with both the make and model of the motherboard. Mine says:

>  *-core
       description: Motherboard
       product: GF8100VM-M5
       vendor: ECS
       physical id: 0
       version: 1.0With that you should be able to google the specifications of your motherboard and find out exactly how much memory and what type it will take.

---

### Post by Fafler on 2010-12-09
[FONT=Tahoma][SIZE=2]I'm pretty sure the 845 series only support up to 512 mb modules. You should get two of those.

Did you try the 1 gb module alone?
[/SIZE][/FONT]

---

### Post by DrPL on 2010-12-09
Hi,
Yes I tried the 1GB module but got the two tone siren.

I ran the instruction you suggested and got   

*-core
       description: Motherboard
       product: 02X378
       vendor: Dell Computer Corp.
       physical id: 0
       serial: ..CN13740342012M.

---

### Post by DrPL on 2010-12-09
[http://en.community.dell.com/support-forums/desktop/f/3514/t/17496927.aspx](http://en.community.dell.com/support-forums/desktop/f/3514/t/17496927.aspx)

- just found the above link. There could be a problem with incompatible memory. Darn!

---


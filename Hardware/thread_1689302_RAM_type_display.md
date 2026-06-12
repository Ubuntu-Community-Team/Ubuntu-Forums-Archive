---
title: "RAM type display ?"
date: 2011-02-16
forum: Hardware
---

### Post by Veren on 2011-02-16
Hello, I've run into a bit of a problem today.
I was thinking about buying a new RAM for my Asus EEE 1015PD, so I checked "sudo lshw" and it said under physical memory this:

     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1

Now, I am confused. The procossor runs at 1.66 GHz and I though the DDR3 RAMs were coming out at 1066, 1366 and 1800 MHz. I don't know what does the number 667 mean. Could you please tell me what type of RAM should I get ? Thanks ):P

---

### Post by cascade9 on 2011-02-17
DDR3 has 800-1600+ ratings offically (according to JEDEC). 

[http://en.wikipedia.org/wiki/DDR3_SDRAM](http://en.wikipedia.org/wiki/DDR3_SDRAM)

Maybe its giving a the non-clock doubled rate (1333 becomes 667 then) or maybe its just using 'slow' DDR3. I think that its more likely that its just using slow DDR3 than lshw reporting the non clock-doubled speed. 

Anyway, that computer uses 204 pin DDR3 SO-DIMM. 

BTW, there is only one memory slot (so you will need to totally remove the current 1GB stick) and there is a 2GB limit according to asus.

---

### Post by Veren on 2011-02-18
> **cascade9 said:**
> DDR3 has 800-1600+ ratings offically (according to JEDEC). 

[http://en.wikipedia.org/wiki/DDR3_SDRAM](http://en.wikipedia.org/wiki/DDR3_SDRAM)

Maybe its giving a the non-clock doubled rate (1333 becomes 667 then) or maybe its just using 'slow' DDR3. I think that its more likely that its just using slow DDR3 than lshw reporting the non clock-doubled speed. 

Anyway, that computer uses 204 pin DDR3 SO-DIMM. 

BTW, there is only one memory slot (so you will need to totally remove the current 1GB stick) and there is a 2GB limit according to asus.

Thanks, but why should there be just one slot, since lshw clearly says there is one empty ?

And also, the 2GB limit is tied to Windows 7 Starter ;)

---

### Post by cascade9 on 2011-02-19
Could be that the chipset is capable of having 2 slots, but there is only one slot soldered into the motherboard. Or there might actually be 2 slots, you'd only need to pop the panel open to check. 

I tried figurign out what cipset its using, but I couldnt find out easily. Some of the chipsets used with atoms are limited to 2GB. 

BTW, crucial (who are normally pretty good on things like this) also say that the Asus EEE 1015PD has 1 RAM slot and a 2GB limit as well. Because of that, I dont think its a win7 starter limit.

---

### Post by jounkarry on 2011-02-19
[SIZE=2]Most EEE PCs use 533/667 MHzDDR2RAM via a standard SO-DIMM module, which can be swapped out. The 700 and 701SDX have RAM soldered to the motherboard.[/SIZE]
 [SIZE=2]The black model EEEPC 4G SURF (4GS-PK008), and newer white models  (4GS-W010) have a removable panel on their underside that allows the  user to change the RAM without fully disassembling the system. The older  white models (4GS-W010) lack this access panel, and require some  disassembly in order to access the RAM.[]("http://en.wikipedia.org/wiki/Asus_Eee_PC#cite_note-9")[/SIZE]
 [SIZE=2]The hardware supports up to 4 GB (2 GB for the 1000 series, and some of the 900 series),[/SIZE] but the preinstalled Xandros kernel of the 700 series only supports up to 1 GB.

---


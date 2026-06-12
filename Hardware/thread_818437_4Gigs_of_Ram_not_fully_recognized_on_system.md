---
title: "4Gigs of Ram not fully recognized on system"
date: 2008-06-04
forum: Hardware
---

### Post by pupEOkami on 2008-06-04
hey guys , so im using 8.4 hardy LTS .
on a T61 thinkpad and a ThinkCentre tower 
when i load up hardware information for the RAM 
on the laptop that can take up to 3.0 gB ram displays 2.96gB Ram
on the tower that handles 4.0Gb ram displays 3.76gB ram 
is there a reason for this cause i have noticed this problem on windowsXP and Vista , 

do any of you guys know a way to fix this so it uses the entire supplied ammount of memory ?:confused:
or is this a cause from the RAM modules?

thanks

---

### Post by Kevbert on 2008-06-04
Are you using 32 bit or 64 bit Hardy ?  If it's only 32 bit then the maximum you're likely to see is 3.2Gb.  If it's 64 bit and the PC is 64 bit you can see more by activating the memory hole in bios.
To see how much memory Ubuntu can see use
```
free -m
```
in terminal.  The tower memory size is about right as any additional memory is probably used by other system devices.

---

### Post by stchman on 2008-06-04
> **pupEOkami said:**
> hey guys , so im using 8.4 hardy LTS .
on a T61 thinkpad and a ThinkCentre tower 
when i load up hardware information for the RAM 
on the laptop that can take up to 3.0 gB ram displays 2.96gB Ram
on the tower that handles 4.0Gb ram displays 3.76gB ram 
is there a reason for this cause i have noticed this problem on windowsXP and Vista , 

do any of you guys know a way to fix this so it uses the entire supplied ammount of memory ?:confused:
or is this a cause from the RAM modules?

thanks
Yes a 32 bit OS can handle a MAX of 2^32 bytes or 4GB RAM.  It usually works out to about 3.5GB RAM.

64 bit Ubuntu can handle 2^64 bytes or 16384 PB or 16 EB of RAM.

---

### Post by BlueSkyNIS on 2008-06-04
> **stchman said:**
> Yes a 32 bit OS can handle a MAX of 2^32 bytes or 4GB RAM.  It usually works out to about 3.5GB RAM.

64 bit Ubuntu can handle 2^64 bytes or 184467PB RAM.

Are those Peta bytes? WOW :shock: that's practically unlimited!

---

### Post by ljonesj on 2008-06-04
well if u run windows vista with sp1 it actually shows 4gb of ram were without it its shows 3.5 i think there was a update in ubuntu 32 that lets u see 4gb but i think that was fiesty that had to have it but i am not sure about hardy

---

### Post by KingTermite on 2008-06-04
> **BlueSkyNIS said:**
> Are those Peta bytes? WOW :shock: that's practically unlimited!

Just wait a few years....that will be min requirements for whatever Windows OS is current then.

---

### Post by Unix_Slayer on 2008-06-05
Even with 8 gigs of ram, my swap file never gets used in Hardy. That's pretty funny, because Vista sucks it all out with 8 gigs.

---

### Post by sdennie on 2008-06-05
pupEOkami: The 2.96G on the laptop seems perfectly normal to me.  3G isn't always exactly 3G on any machine but 2.96G is close enough that it's probably not something to worry about.  The 3.76G on the server can probably be increased a bit by installing 64bit Ubuntu or by installing the 32-bit server kernel:

```

sudo apt-get install linux-server linux-headers-server linux-restricted-modules-server

```

I don't know if that will be auto-selected at boot time so, you may have to hit escape when grub comes up and select the server kernel.

---


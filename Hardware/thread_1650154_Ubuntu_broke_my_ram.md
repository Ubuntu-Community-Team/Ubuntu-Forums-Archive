---
title: "Ubuntu broke my ram?"
date: 2010-12-21
forum: Hardware
---

### Post by Gp. on 2010-12-21
After recently trying to rediscover Ubuntu (see my other thread), one of my RAM sticks died shortly after.

After playing around with Ubuntu, I started receiving a lot of blue screens from Windows. I had no idea why until I ran two different memory test programs including Memtest86.

Memtest86 reported many problems and I narrowed it down to one of my ram modules, the other 3 are fine (I have 4gb.)

Is there anyway mucking around with Ubuntu and the live CD could of corrupted the module and is there anyway to repair it if so?

---

### Post by mickwombat on 2010-12-21
Hi

> Is there anyway mucking around with Ubuntu and the live CD could of corrupted the module and is there anyway to repair it if so? 

I very much doubt it.  It was probably already on it's way out.

---

### Post by Wobblybob on 2010-12-21
in short no and no, the RAM was probabley on it's way out as it was and once dead they need to be replaced.

---

### Post by Gp. on 2010-12-21
I was upgrading and downgrading the BIOS also to see if Ubuntu would boot in regards to my other post. Could this have caused the RAM module to fault?

Is there some way to clear out the ram module of from sort of cache or refresh it someway?

---

### Post by sourchier on 2010-12-21
You could try the ram module in another computer. But I think it may be a lost cause. There is also a "bad ram" patch that you could try. See here:
[http://ubuntuforums.org/archive/index.php/t-102254.html]("http://ubuntuforums.org/archive/index.php/t-102254.html")

---

### Post by cascade9 on 2010-12-21
> **Gp. said:**
> I was upgrading and downgrading the BIOS also to see if Ubuntu would boot in regards to my other post. Could this have caused the RAM module to fault?

Is there some way to clear out the ram module of from sort of cache or refresh it someway?

Very, very unlikely that doing that to your BIOS did anything to your RAM. 

You can (sometimes) get RAM thats failing memtest to work by either bumping the voltage going to the RAM, or underclocking the RAM. Either, or a combonation of both, can sometimes work

---

### Post by IcarusR on 2010-12-21
> Is there some way to clear out the ram module of from sort of cache or refresh it someway?

RAM = random access memory it is volatile memory ie it only reteins information as long as it has power.
So switch off the box it is installed in will remove power from ram & it will no longer retain info.
In short every time you switch your box off ram is cleared/wiped.

As others have said your ram was probably failing before you tried Ubuntu. OS can not 'break' ram.

Replace ram & move on.

---

### Post by efflandt on 2010-12-23
If you drop back to 2 sticks and test cleanly, do you only get a bad test when the stick you think is bad is one of the pair (and likewise when just using the other 2 slots)?  That could isolate if it is a bad stick or a problem with a slot, or the motherboard or possibly marginal power supply.

I have only run across RAM issues twice.  When I first upgraded PC3200 RAM 2x512 MB on an early Athlon64 from 2004 it apparently was not quite compatible and memtest86+ showed errors.  But OCZ swapped that out for RAM that they guaranteed would work, and it did.  More recently an upgrade with PNY PC3200 RAM 2x1 GB had no issues.  In both cases RAM was completely changed because that PC only has 2 RAM slots.

In another case a P4 2 GHz at work was upgraded from 256 MB to single 512 MB with RAM that Crucial said would work for that model (I forget if PC2100 or PC2700).  But it occasionally blue screened WinXP, and I did not get around to memtest86+ until we were retiring it.  The 512 RAM that tested bad in that PC lives on in another PC where it tests fine with no errors.  The original 256 MB tests fine in the old PC, but that is not even enough to run WinXP.

So testing RAM on just one computer may not really tell if the RAM or some other hardware or compatibility is the issue.

You have not said if you are just running regular 32-bit (which cannot even use 4 GB), or a pae or 64-bit kernel that can use all of it.

---

### Post by I'mGeorge on 2010-12-23
> **Gp. said:**
> After recently trying to rediscover Ubuntu (see my other thread), one of my RAM sticks died shortly after.

After playing around with Ubuntu, I started receiving a lot of blue screens from Windows. I had no idea why until I ran two different memory test programs including Memtest86.

Memtest86 reported many problems and I narrowed it down to one of my ram modules, the other 3 are fine (I have 4gb.)

Is there anyway mucking around with Ubuntu and the live CD could of corrupted the module and is there anyway to repair it if so?

If ubuntu it's not a high tech OS (which I'm pretty sure it is) it's still one of the most well developed OS around so this could never had happened because of it. Anyway test your memory on other computers to see how it goes. maybe you've messed up your BIOS somehow.

---

### Post by Gp. on 2010-12-26
> **I'mGeorge said:**
> If ubuntu it's not a high tech OS (which I'm pretty sure it is) it's still one of the most well developed OS around so this could never had happened because of it. Anyway test your memory on other computers to see how it goes. maybe you've messed up your BIOS somehow.


I think the RAM was just due to die, but I wasn't sure cause it all happened shortly after ubuntu.

---

### Post by Peanuts123 on 2010-12-26
NO goofiest post I've seen all day

---

### Post by Gp. on 2010-12-26
> **Peanuts123 said:**
> NO goofiest post I've seen all day

Oh wow, get over it not everybody is the expert.

---


---
title: "Memory help"
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by bingouk on 2008-04-11
Hi I've got a question about hardware itself but can't think of anywhere else to post it!

Anyway I had 2 512MB DIMM slots in my PC giving 1Gb memory. I decided to upgrade so bought 2 1GB memory chips to put in. I'm no expert but got the right memory from crucial using their service. Anyway I've put the 2 1GB chips in but only 1 is recognised in the BIOS. The other says not installed. I've tried both memory chips in the working slot and they both work. So I'm thinking I must have damaged the other slot whilst trying to install the new memory as it was working before. 

So questions:
 
Is it easy to damage the DIMM slots themselves? Can you do anything to fix them?

Is having 1 1GB stick working the same as 2 512MB sticks working  in terms of performance (if so I figure I've not lost out as I've the same memory as before)?

---

### Post by logos34 on 2008-04-11
> **bingouk said:**
> Hi I've got a question about hardware itself but can't think of anywhere else to post it!

Anyway I had 2 512MB DIMM slots in my PC giving 1Gb memory. I decided to upgrade so bought 2 1GB memory chips to put in. I'm no expert but got the right memory from crucial using their service. Anyway I've put the 2 1GB chips in but only 1 is recognised in the BIOS. The other says not installed. I've tried both memory chips in the working slot and they both work. So I'm thinking I must have damaged the other slot whilst trying to install the new memory as it was working before. 

So questions:
 
Is it easy to damage the DIMM slots themselves? Can you do anything to fix them?

Check that the stick is seated properly (that's usually the problem).  It can be a bitch to get working.

> Is having 1 1GB stick working the same as 2 512MB sticks working  in terms of performance (if so I figure I've not lost out as I've the same memory as before)?

Not if you have dual-channel memory, in which case the slots have to be paired/balanced (otherwise it runs in single-channel mode).  But the performance difference is not much, and frankly I don't think you'll notice unless you do any gaming.

---

### Post by bingouk on 2008-04-11
I thought that but I've tried putting the stick in loads of times now and it just won't work so I'm wondering if it's possible to damage the slot itself? Maybe I'll give it a few more goes!!

---

### Post by bradwilliamson on 2008-04-11
Take out the RAM completely 
put one stick of RAM back in slot 1/A/First whatever, make sure it's seated
boot the system up with an installer disk with memtest86+ on it and let it run the memory test

if it succeeds, shut it down, put the other stick in slot 1/A/First whatever and do it again.
if it succeeds, shut it down, put the first stick in slot 2/B/Second whatever and do it again.
if it succeeds, shut it down, put the second stick in slot 2/B/Second whatever and do it again.

If it fails bad on either stick, the memory is probably bad, it happens. But keep track of the failures to see if they follow the RAM or the slot. 

It is possible that it won't boot at all with only the second slot populated, try both sticks to be sure but don't write that off as a failure if neither boots.

If the tests pass on both, try it again with both sticks in the machine

If it passes again, reverse them and try it again.

Memtest will tell you at every step of this how much memory it sees. We just sent back a 1GB that would only show up as 512MB no matter what.

It's also possible that a BIOS update would fix this as well, assuming that Crucial sold you the correct memory for that computer.

If you're *still* stuck, try 1.5GB and see if it works. If it does, I would suspect a memory controller or BIOS issue.

Good luck.

---

### Post by bradwilliamson on 2008-04-11
Also, it **is** possible to break a SIMM slot, but only with a fair amount of force. 

Typically the little divider piece that divides the slot gets broken off and gets jammed into the slot.

Less typically, one 'finger' gets bent down and smashed into the bottom of the slot, ruining that contact and not letting it seat properly either.

My money's still on the BIOS or one stick is bad.

Hope that helps,
Brad

---

### Post by bingouk on 2008-04-11
ok thanks for the advice. I'll have another go!

---

### Post by bingouk on 2008-04-11
the divider is present intact. It's not that.

> one 'finger' gets bent down and smashed into the bottom of the slot, ruining that contact and not >letting it seat properly either.

Well I can't tell but it could be this as it won't recognise any of the new 1 GB sticks or the old 512MB sticks.

I've tried searching for a bios update (Intel Bios CF94510J.15A.0028.2006.1213.1629) but no joy.

I suspect I've bust the slot. Oh well :(  Guess I'll cope with a single 1 GB rather than the dual 512s. Shame though. I'll leave the hardware alone in future!!

---

### Post by bingouk on 2008-04-11
Oh and I should say that's my Windows machine I need the RAM for as I've been informed I need 2GB of memory to run Vista!! What I can tell you is my Ubuntu machine [http://www.ebuyer.com/product/133576](http://www.ebuyer.com/product/133576) was so cheap and is actually very good (came with dapper and would not boot as CMOS battery was set to past - but running cool under Gutsy)  after I installed a graphics card - though that was a scary moment -hardware is scary - hence this thread. But the shock and pleasure my girlfriend seen as the cube spun on a sub 200 quid desktop was really priceless!

And in Ubuntu I've managed to run some work (statistical models) that just wouldn't run in Windows due to the memory leaks. 

All hail Ubuntu!!!

---


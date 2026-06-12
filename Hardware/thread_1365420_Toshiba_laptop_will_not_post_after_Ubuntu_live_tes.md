---
title: "Toshiba laptop will not post after Ubuntu live test"
date: 2009-12-27
forum: Hardware
---

### Post by TerryT on 2009-12-27
I was testing Ubuntu 9.10 in live mode on an old Toshiba Satellite A20 laptop and everything was working fine. The last thing I did was to see if it would suspend to ram, which did not work.  I ended up with a blinking cursor near the middle of the screen.

Problem is, from that point onwards, the laptop will not power up, or even post. Power is available (fans and lights come on) but I'm stuck at a blank screen. I've tried all the obvious things such as removing the battery to clear the state of the machine.

My question is, is there anything that Ubuntu could have done that would affect the ability of the laptop to power up, i.e., writing something to the cmos memory for example? Or is this just a coincidence that a hardware problem appeared at that exact instant? There are loads of online postings about Toshiba laptops "stuck in suspend mode" but I would have thought that removing power would have cleared anything like that.

The only thing that we haven't tried is to clear the cmos memory, although I'm not sure how to do that on this laptop.

Thanks,
Terry

---

### Post by MeanEYE on 2009-12-27
Ubuntu shouldn't write anything to CMOS. Though Toshiba laptops tend to freeze when setting them to sleep mode due to lack of hardware support.

So your laptop after manually shutting it down (holding power button for at least 4 seconds) can't be turned on?

---

### Post by adam814 on 2009-12-27
I've actually known some machines to use so little power in sleep mode that even disconnecting them from power doesn't work for a while (i.e. battery out and right back in won't help).

---

### Post by TerryT on 2009-12-29
> **MeanEYE said:**
> Ubuntu shouldn't write anything to CMOS. Though Toshiba laptops tend to freeze when setting them to sleep mode due to lack of hardware support.

So your laptop after manually shutting it down (holding power button for at least 4 seconds) can't be turned on?

Yes, that is correct. When we try to turn it on, the power lights and fans come on but the screen is blank and it never even posts. It is consistent with it unsucessfully trying to resume from a suspend, but this can't be the case since we've removed the battery and power for long time periods. So assuming that Ubuntu did not set something permanently, a hardware fault must have occurred at the exact instant that I tried to suspend the laptop. It is an odd coincidence, for sure.

---


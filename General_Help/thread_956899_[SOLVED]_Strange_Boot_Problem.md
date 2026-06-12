---
title: "[SOLVED] Strange Boot Problem"
date: 2008-10-23
forum: General Help
---

### Post by Krydahl on 2008-10-23
OK, I don't think this is a Linux/Ubuntu problem at all, I think it's my hardware, but I'd be grateful for any thoughts.

I'm trying to get my desktop (see sig for hardware) running with dual monitors. I've basically sorted it, but I've found that when I try to restart the machine with both monitors plugged in (one in the the VGA output of the onboard graphics card, one in the digital) the whole machine won't boot. It doesn't seem to make it into the bios, never mind to grub, just hangs with a (two actually) blank screen.

Once the machine is up, I can plug in the second monitor, restart X and everything's fine.

I tried leaving the second monitor turned off while booting, that didn't help. I looked in the bios, but couldn't see anything obvious. Any suggestions?

---

### Post by Pro-reason on 2008-10-23
That should never happen.  Is the graphics card still under warranty?

---

### Post by Krydahl on 2008-10-23
No, the mobo must be 3 years old at least. Never given me any trouble though.

---

### Post by Pro-reason on 2008-10-23
Had you previously tried connecting two monitors?

You're right that this isn't an OS problem.  It must be physical damage, bad motherboard design, or bad firmware.  You can only fix the last of those.  Try downloading the latest BIOS firmware for your motherboard, and install it.

---

### Post by Krydahl on 2008-10-23
This gets weirder. I've now found that if I turn it off and then manually start it, it boots ok. It's just selecting restart that causes a problem.

This makes it a much less serious problem, I guess. Still strange though.

---

### Post by Crossyboi on 2008-10-23
> **Krydahl said:**
> This gets weirder. I've now found that if I turn it off and then manually start it, it boots ok. It's just selecting restart that causes a problem.

This makes it a much less serious problem, I guess. Still strange though.


I don't think this is a serious problem either, sounds to me that your computer cant decide what monitor to 'Initialise' which is why it boots fine with just one monitor. Im not sure of a fix to this, is it that much hassle to replug in a monitor each time you use your computer?

---

### Post by Krydahl on 2008-10-23
It's a bit of a drag - the cable round the back of the PC isn't too easy to reach, but if it carries on working fine from a cold boot then it's not much of a problem, true.

---

### Post by TeXtonyx on 2008-10-23
A shutdown is not like a restart in terms of clearing ram or cache,
I think the difference is. I know there's a difference because
when an install gets frozen, I've seen instructions insisting that
you shutdown the computer, then reboot, rather than restarting. 
Maybe that memory was of Partition Magic and moving a partition.

It is rather odd and I don't think software as a cause is eliminated.
If it works with Windows then it is a software problem. I fixed a
problem with dual monitors once by changing where I stuck the plug
in on the underside of the monitor chassis. I'm thinking both monitors
on one channel... anyway switching to the other port worked. I was
desperate and it was the last thing I thought of to try.

---

### Post by Krydahl on 2008-10-24
Funny what fixes things sometimes.

I've no idea if this works under windows - I don't have it installed on the machine. However, I think I'm going to mark this thread as solved. Now I've found I can just turn the machine off and on again, it's not a big deal.

Thanks for your thoughts.

---


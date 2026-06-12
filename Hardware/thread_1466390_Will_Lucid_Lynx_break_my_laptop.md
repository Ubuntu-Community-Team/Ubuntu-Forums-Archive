---
title: "Will Lucid Lynx break my laptop?"
date: 2010-04-30
forum: Hardware
---

### Post by whitefort on 2010-04-30
First of all, I LOVE Lucid so far.

But this is causing me some concern.  When I shut down my laptop, it always ends with that 'popping' sound of a hard-drive that hasn't been shut down properly.

Anyone else getting this?

More to the point, I've heard that this will eventually kill the hard-drive, and I'm a bit worried about that.

IS this a genuine cause for concern, or am I worrying about nothing?

I posted this as a bug, but was told that it was a kernel issue and not a Lynx problem...  but it seems to me that if Lynx is using a kernel that can damage computers, that's kinda a problem for Ubuntu users too.

---

### Post by TBABill on 2010-04-30
Whitefort, not sure if the problem can cause actual damage, but a hard drive should never make mechanical noise beyond the normal noises it makes during operation. If it were mine I think I would download another distro that is non-Ubuntu and just run it live through the same routine you have seen this happen under Ubuntu. If you don't get the same results there could be cause for concern. I just lost a hard drive on a Windows machine due to sudden failure with no prior indication of a problem, so maybe you can head yours off before a failure. I would definitely do a backup of your important data regardless of failure at this point because you have identified some sort of problem not previously identified with the drive.
 
I would think a known hardware conflict that can cause damage to hardware would be a top priority for a fix, but it would be tough to subject a machine to potential failure until a fix was found. Do you have another drive to swap into it to verify it's the distro and not the drive just starting to fail? Or another partition to run Windows or another distro on to confirm?

---

### Post by whitefort on 2010-04-30
Thanks for the reply.

No, this is definitely unique to Lynx.  I don't have any non-Ubuntu disks handy, but I've put Koala on again, then (just for the heck of it) Ibex, and neither give the shutdown problem.

Then I put on Lynx again, and the hard-drive 'pop' is back.

If this is really a kernel issue then presumably all the other new distros will be hit by it too - in which case I suppose there'll be a fix fairly quickly, as I don't think people will stand for Linux hurting their laptops.

I might just go back to Koala on my laptop, and try Lynx again in a couple of months to see if the problem is sorted.

Thanks again.

---

### Post by cookdav on 2010-05-01
> **whitefort said:**
> First of all, I LOVE Lucid so far.

But this is causing me some concern.  When I shut down my laptop, it always ends with that 'popping' sound of a hard-drive that hasn't been shut down properly.

Anyone else getting this?

More to the point, I've heard that this will eventually kill the hard-drive, and I'm a bit worried about that.

IS this a genuine cause for concern, or am I worrying about nothing?

I posted this as a bug, but was told that it was a kernel issue and not a Lynx problem...  but it seems to me that if Lynx is using a kernel that can damage computers, that's kinda a problem for Ubuntu users too.

When you have hardware issues, you need to post a FULL
spec of your machine. :evil:

Do you have Intel graphics card?  (I'm guessing yes.)

---

### Post by whitefort on 2010-05-01
Yes, I have an intel graphics card (actually I have what seems to be the worst intel graphics card of all time - that GMA500 poulsbo thingie).

The computer is an acer aspire 751h.

I've gone back to Koala on this computer.  Lynx is fine on my main laptop and on all my desktops.

---

### Post by cookdav on 2010-05-01
> **whitefort said:**
> Yes, I have an intel graphics card (actually I have what seems to be the worst intel graphics card of all time - that GMA500 poulsbo thingie).

The computer is an acer aspire 751h.

I've gone back to Koala on this computer.  Lynx is fine on my main laptop and on all my desktops.

I'm reasonably sure that your 'pop' comes from the Intel sound-system, as
MEPIS had this during early beta, but it got fixed.

Ubuntu seems to have 'buried' the problem in 10.04, but if you google
snd-hda-intel power_save
you'll see the problem/solution for earlier/other distros.

---

### Post by MeanEYE on 2010-05-01
> **whitefort said:**
> First of all, I LOVE Lucid so far.

But this is causing me some concern.  When I shut down my laptop, it always ends with that 'popping' sound of a hard-drive that hasn't been shut down properly.

Anyone else getting this?

More to the point, I've heard that this will eventually kill the hard-drive, and I'm a bit worried about that.

IS this a genuine cause for concern, or am I worrying about nothing?

I posted this as a bug, but was told that it was a kernel issue and not a Lynx problem...  but it seems to me that if Lynx is using a kernel that can damage computers, that's kinda a problem for Ubuntu users too.

I don't think Ubuntu it self will break your laptop. Hard drives move reading heads to a specific position to prevent damage during transport. The sound you are hearing is just the process of fixing that head (head is fixed using magnets). All hard drives make that sound when you turn them of. The question is, how loud is that sound?

My laptop is well build and isolated so noise is minimum.

Edit: Or as cookdav said, it could be sound from your speakers :D...

---


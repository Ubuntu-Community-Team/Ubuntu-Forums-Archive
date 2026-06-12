---
title: "Clean Install Question?"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2009-05-13
I recently installed 9.04 online from 8.10 on my 12 yr old Gateway Pent 2 and it was flawless. 9.04 runs pretty good on that old PC, in fact it runs better than 8.10 did on it.

Then I installed 64bit 9.04 on my newer Toshiba AMD laptop which was running 32bit 8.10 very well. I am so far underwhelmed with how the 64bit version runs....it's slower than 8.10 was. 8.10 ran better on the laptop than 64bit 9.04 is. I installed 64bit 9.04 with the CD I created after downloading the 9.04 ISO....installation took 15 minutes. 

Question is, is this considered a 'clean install' since it was done with a CD and not online?

The reason I ask is I'm thinking of replacing this 64bit version with the 32bit version of 9.04 by just putting in the 32bit install CD I just got from ShipIt and telling it to install. I assume this will overwrite the 64bit version with the 32 bit version of 9.04.

Is this correct?

---

### Post by Therion on 2009-05-13
> **cybrsaylr said:**
> Is this correct?
Yes.

---

### Post by Wa1k3rTXRang3r on 2009-05-13
yes it is considered a clean install as long as you completely erased your old os with this new one.

and yes you are correct. the 32bit will replace the 64bit unless you set it up to have 2 partitions

---

### Post by cybrsaylr on 2009-05-13
I have 2 partitions to run Vista/Ubuntu.

I had just put 64b 9.04 in the same partition as 32b 8.10 was and did not put a checkmark in the 'format' box when installing.

Is it necessary to checkmark the 'format' box when going from 64b to 32b 9.04?

If I check that format box will I lose all my previous setting ?

---

### Post by logos34 on 2009-05-13
> **cybrsaylr said:**
> I have 2 partitions to run Vista/Ubuntu.

I had just put 64b 9.04 in the same partition as 32b 8.10 was and did not put a checkmark in the 'format' box when installing.

Is it necessary to checkmark the 'format' box when going from 64b to 32b 9.04?

If I check that format box will I lose all my previous setting ?

You overwrote 8.10, which means it was formatted.  As soon as you point it to the target / partition, it checks format automatically, I believe (to see what I mean, when you install 32-bit you'll notice when you get to that step that the box is checked and grayed-out.  IIRC from last time I installed)

You'll lose your settings.  The whole previous setup. Poof. gone. replaced by 32-bit.

One way to save them is to transfer /home to a separate partition beforehand.  Or maybe just /home cp -a and copy it back.  But you're switching architectures, so not sure if that's wise

---

### Post by cybrsaylr on 2009-05-13
Thought so.
Thanks for the help guys.

---


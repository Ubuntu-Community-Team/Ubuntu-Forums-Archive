---
title: "&quot;Ubuntu detected an error on the root partition&quot;..."
date: 2008-06-23
forum: Hardware
---

### Post by BigSilly on 2008-06-23
What does this mean? Is it a sign there's an issue with the hard drive?

It's the missus' laptop. She's just booted it up, whereupon it's performed it's routine FSCK check, and popped up with this message. It said it had detected the fault, and fixed it. Is there anything else we can do to check the integrity of the HDD?

It's a Dell 1525 Inspiron, running Ubuntu Gutsy. Thanks all.

---

### Post by Odrodzona-Sarmacja on 2008-06-23
fsck is not like scandisk.
Never, never and never use it on root partition, unless during bootup linux will ask you do so explicitly.

---

### Post by ajgreeny on 2008-06-23
There are a number of diagnostic utilities that can be used to check such things, but you will need to search google to find out what is available and free for use.  I think you probably do not need to worry too much unless this happens fairly often, but you could force another check at next boot by typing ```
sudo touch /forcefsck
``` in terminal before you shutdown or restart.  If that check is OK, it was probably a one off problem, perhaps related to a bad shutdown at some time or something similar.  If you do see the same message when fsck runs, then you may be getting to the end of the disk's useful life.  Back up (which you should do anyway) and investigate the possibilities of a new drive, should yours fail completely.

---

### Post by konungursvia on 2008-06-23
Drives do come up with magnetic domain flipping errors and these are corrected by check routines. If your computer still runs well, I would assume the error found was a simple domain flip which has been corrected by check bits and is now just dandy.

---

### Post by BigSilly on 2008-06-23
> **Odrodzona-Sarmacja said:**
> fsck is not like scandisk.
Never, never and never use it on root partition, unless during bootup linux will ask you do so explicitly.

Really? Why not? I thought it was just a simple check utility. As I say, it was during boot-up that the error message popped up anyway.

@ajgreeny - thanks I'll try that.

EDIT: Just done that, and it didn't report any errors this time. It's a very new laptop (only bought from Dell in April), so I thought it odd that the hard drive should be faulty. Still, it does happen doesn't it?

Thanks all.

---

### Post by Odrodzona-Sarmacja on 2008-06-23
> **BigSilly said:**
> Really? Why not? I thought it was just a simple check utility. As I say, it was during boot-up that the error message popped up anyway.

Fsck is not a simple check utility. Simple utilities do not cut your hard drive's files and directories into small tiny packets and then put them under random alphanumeric names in lost&found directory. Fsck is a dangerous tool, which is OFFICIALLY not advised to be used to check on root partitions.

---

### Post by BigSilly on 2008-06-23
> **Odrodzona-Sarmacja said:**
> Fsck is not a simple check utility. Simple utilities do not cut your hard drive's files and directories into small tiny packets and then put them under random alphanumeric names in lost&found directory. Fsck is a dangerous tool, which is OFFICIALLY not advised to be used to check on root partitions.

Thanks for the advice. Why did Ubuntu use FSCK to check the root partition then, if it's not safe to do so? If it has harmed something, are we talking about software or hardware damage? FSCK can't actually damage a HDD can it?

---

### Post by Odrodzona-Sarmacja on 2008-06-23
> **BigSilly said:**
> Thanks for the advice. Why did Ubuntu use FSCK to check the root partition then, if it's not safe to do so? If it has harmed something, are we talking about software or hardware damage? FSCK can't actually damage a HDD can it?

Ubuntu does lock all system files on root partition as "read-only" before letting fsck loose on it.

---

### Post by BigSilly on 2008-06-23
> **Odrodzona-Sarmacja said:**
> Ubuntu does lock all system files on root partition as "read-only" before letting fsck loose on it.

I've got you. Please forgive me, I was confusing root with boot! 

Of course I understand what you are saying. Thanks for your replies.

---


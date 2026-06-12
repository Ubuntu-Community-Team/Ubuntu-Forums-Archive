---
title: "[SOLVED] Can't boot my X60 even in recovery mode"
date: 2008-09-18
forum: Hardware
---

### Post by dash86no on 2008-09-18
chaps,

My X60 has died on me and would appreciate a little help:

I was on the train about 20 mins ago reading an ebook on my laptop when I got the "Battery critically low! warning. I immediately shut down my system.

Now when I try to boot I get the following error message:

ata1.00: status {DRDY ERR }
ata1.00 error {UNC}
ata1.00: configured for UMDA/100
ata1: EH complete

this message is just repeating and repeating with other messages such as:

[sda] Sense key: medium error
end_request I/O error

etc. etc.

I am duel booting hardy 8.04 and windows xp on a lenovo x60.

cheers

---

### Post by dash86no on 2008-09-19
Bump

Any ideas on this on chaps? I am currently forced into the ignominy of running win XP (which is running fine, so im guessing the inode table or something else important is whacked on my Ubuntu partition. )

I plan to maybe try some desperate file system recovery procedures with a live CD sometime this evening. Has any one got any tips on the best way to go about this?

As this is the third major problem i've had running my X60 with Ubuntu, i have a sneaking suspicion that the OS just isn't behaving well with the core 2 duo or some other part of the hardware of this newish machine (I have never had any problems running ubuntu on older machines)

I read a while back about thinkpad users suffering broken HDDs when running ubuntu due to excessive touching of the disks/IOs etc. Could this be the case here?

Cheers,

---

### Post by dash86no on 2008-10-14
> **dash86no said:**
> Bump

Any ideas on this on chaps? I am currently forced into the ignominy of running win XP (which is running fine, so im guessing the inode table or something else important is whacked on my Ubuntu partition. )

I plan to maybe try some desperate file system recovery procedures with a live CD sometime this evening. Has any one got any tips on the best way to go about this?

As this is the third major problem i've had running my X60 with Ubuntu, i have a sneaking suspicion that the OS just isn't behaving well with the core 2 duo or some other part of the hardware of this newish machine (I have never had any problems running ubuntu on older machines)

I read a while back about thinkpad users suffering broken HDDs when running ubuntu due to excessive touching of the disks/IOs etc. Could this be the case here?

Cheers,


Hi all,

I believe I have a resolution of sorts here.

After my laptop finally died (Stopped booting) I ran spinrite on the hard disk. It was running for over 500 hours but still only got 65% through the disk.

Basically the laptop was a year old when I got my hands on it and it seems the hard disk was broken from the beginning.

I have a new hard disk now and am actually giving Mandriva 2009 a spin. It's pretty awesome, even winning over a die hard Ubuntu fan like me. I was only putting it on to learn RPM for my LPICs but I've fallen in love with KDE. It looks like an upgrade to Kubuntu 8.10 for my home systems at the end of the month.....

Cheers

---


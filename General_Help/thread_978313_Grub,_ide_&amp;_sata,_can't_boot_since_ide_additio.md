---
title: "Grub, ide &amp; sata, can't boot since ide addition"
date: 2008-11-11
forum: General Help
---

### Post by glave on 2008-11-11
My system was using sata drives exclusively and I was successfully dual booting hardy and xp for quite some time. Recently, I added a large ide drive into the mix, and now I can't get grub to boot anymore. I gave up for a bit and used xp's recovery console to get xp going again, but I want my dual booting back.

sda is a 200g drive with XP and two additonal ntfs partitions (sata)
sdb is a 80g drive with Hardy, swap, and a home partition (3 partitions) (sata)
sdc is a 320g drive with a ntfs storage partition only. (ide)

/boot/grub/stage1 is being located on (hd1,0).

Bios is set to boot sata drives as primary, not ide.

I have tried every combination I can think of over the weekend, but no luck. Most recently I did:

root (hd1,0)
setup (hd0)

This resulted in a repeating GRUB GRUB GRUB GRUB.


Can any grub gurus point me in the right direction?

---

### Post by mdurham on 2008-11-11
what happens when in Grub you type:> find /boot/grub/stage1?

---

### Post by glave on 2008-11-11
It finds it on hd1,0

---

### Post by mdurham on 2008-11-11
I've seen people recommend the Supergrub disc for things like this. Maybe it would show up something about the problem you have. Sorry I can't be of more help than that.
Cheers, Mike

---

### Post by caljohnsmith on 2008-11-11
I've read that a repeating "GRUB" printout on your screen at start up is often caused by having your HDD misconfigured in your BIOS. If you can, try changing the BIOS settings for that HDD to "auto-detect" or similar, and see if that helps. If not, try changing any other HDD related settings you have in BIOS for that drive. Let me know how that goes.

---

### Post by rbmorse on 2008-11-11
Under system defaults, your BIOS is enumerating and loading the IDE/ATA drive (connected with the 80 conductor ribbon) **before** it does the SATA drives (connected with the 8 (16?) conductor wire), so which ever drive is attached to the IDE ribbon is going to be (hd0) to the BIOS, even though Linux sees it as hdc. 

So, try this setup:

root (hd1,0)      <--- this is the same you've been using
setup (hd2)       <--- this should write the MBR of the IDE drive
quit
exit

restart the machine

---

### Post by psusi on 2008-11-11
> **rbmorse said:**
> Under system defaults, your BIOS is enumerating and loading the IDE/ATA drive (connected with the 80 conductor ribbon) **before** it does the SATA drives (connected with the 8 (16?) conductor wire), so which ever drive is attached to the IDE ribbon is going to be (hd0) to the BIOS, even though Linux sees it as hdc. 

So, try this setup:

root (hd1,0)      <--- this is the same you've been using
setup (hd2)       <--- this should write the MBR of the IDE drive
quit
exit

restart the machine

He already said his bios is set to boot from the sata drive rather than the ide, which would make the sata drive hd0.  The question is, which sata drive, since there are two?  It could be that the bios is trying to boot from sdb instead of sda.

---

### Post by rbmorse on 2008-11-11
> **psusi said:**
> He already said his bios is set to boot from the sata drive rather than the ide, which would make the sata drive hd0.  The question is, which sata drive, since there are two?  It could be that the bios is trying to boot from sdb instead of sda.

He said that, but I don't think whatever he did actually made the change...i.e., if it had, it would have worked.

---


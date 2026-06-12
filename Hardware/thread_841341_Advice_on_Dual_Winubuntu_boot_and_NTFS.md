---
title: "Advice on Dual Win/ubuntu boot and NTFS"
date: 2008-06-26
forum: Hardware
---

### Post by sadams on 2008-06-26
Hi all,

I already think I know what I'm (going to be) doing on this however it will be interesting to get validation/feedback here.. and may be of interest to others.

1) Intro:
I'm sourcing a new laptop for my dad. He's in his 70s and a long term PC user.. having used Windows since 3.x way back - yet he is not very techy and uses his PC these days for mostly "civilian" purposes (email, web, some officey-stuff). he also has a Palm pilot that he syncs to desktop (mostly to "backup" rather than to utilise the data on the PC).
I also have and use my palm on ubuntu and know the options/requirements.

He is no fan of windows and is already picked up that Vista is a crock of bloatware and to be avoided.
He is open to being switched to Linux and i intend to get him set up on Hardy.

2) The Laptop:
I became converted to the way of the Thinkpad a few years ago and I am recommending an R61 model for dad.
I have done some initial digging/checking and it seems this is a decent choice for relatively sane and happy ubuntu'ing.
 
  **Anyone with specific warnings and horror stories regarding ubuntu/hardy on a Thinkpad R61 please shout now!

I will buy one with WinXP but intend to leave it on but ignore it... leaving it as an option should dad reject ubuntu (as if!)
I will install, configure, tailor and deliver the system to dad and conduct "handover training" :-)

*Note: the intention is not to regularly dual boot - Win XP is there only as insurance if it turns out dad doesn't like ubuntu.. or some hardware or s/w really necessitates it in the future (both unlikely).

3) Filesystems and dual booting.
So.. the thing will have a 160GB drive.
I intend to partition it as..:
 *examples assume a disk labeled hda - even if you know better and that it would really be an sda please just play along and imagine it were called this!

hda1 - WinXP factory install resized down to say 20GB (or so)
hda2 - ubuntu hardy - say 20GB
hda3 - SWAP - 2GB (2 x RAM) - overkill but caters for upgrades in the future :-)
hda4 - "Home/General" files - the "rest of the disk"
hda5 - Thinkpad "hidden" recovery partition (assuming there is one, usually at the end of the disk)

I am intending to make the Home partition as an NTFS system "just in case" the data needs to be accessible from windows.

This is on the assumption that:
 i) Mounting an ext2/3 filesystem in WinXP requires extra software to manage and creates work and a techy on hand to do it.
ii) Despite reservations about NTFS (and the bad taste it creates on a lovely shiny ubuntu system) it will have no material difference on a "general purpose" laptop.
  i.e. 
    - any fragmentation issues can be lived/dealt with when the time comes
    - no material performance issues reading/writing to the drive

So... any comments/suggestions/improvements?

Regards,
   Steve.

---


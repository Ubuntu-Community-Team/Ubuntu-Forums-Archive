---
title: "SD Card won't read, won't let me initialze it"
date: 2009-05-31
forum: Hardware
---

### Post by rockmanac on 2009-05-31
I have 2 SD cards.  Both worked in this netbook (Acer Aspire One) when I had Windows on it, now, only the 1GB card will work, the 8GB card won't recognize at all.

Output of 'tail /var/log/kern.log -f'

```
May 31 11:37:02 kaylee kernel: [  164.095116] mmc0: error -84 whilst initialising SD card
```

That is the error I get when I insert the 8GB SDHC card.  Again, this card worked prior to me installing UNR.  I've tried it in the netbook with an external reader with no results either.

I'm thinking Acer did something to it to lock it to the Windows install (won't mount on my iMac either.)

```
May 31 11:37:25 kaylee kernel: [  187.383598] mmc0: new SD card at address 9ffc
May 31 11:37:25 kaylee kernel: [  187.404249] mmcblk0: mmc0:9ffc SU01G 968 MiB 
May 31 11:37:25 kaylee kernel: [  187.404436]  mmcblk0: p1

```

Just to prove the reader is working, that's what happens when I insert a 1GB card into the slot.

Anyone else run into this issue?  I've done some searching and have tried a few things but with no luck.  I'm stumped because I can't see the card to even wipe and reformat it.  Part of me is tempted to just take it to work and run it through the bulk eraser (does that even work for flash cards?)  I mean, there's no valuable data on the card (I was installing Windows programs to it), I just want to be able to use it as storage.

Any help would be appreciated!

-Adam

---


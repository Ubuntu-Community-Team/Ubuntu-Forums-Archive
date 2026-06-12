---
title: "using a pc cd on a note book"
date: 2010-02-22
forum: Hardware
---

### Post by Garthhh on 2010-02-22
I'm trying to install an operating system [9.04] on a 04 gateway notebook
the bios doesn't support boot from usb
the cd is bad,
I would like to use a cd/dvd from a pc
that makes it a 40 pin ide to 50 pin ide adapter?
I can find plenty to use a mini on a fullsized
the hole in the notebook is very deep, so it has to have a card extender too

---

### Post by Garthhh on 2010-02-22
the HDD is stuck in the middle of a XP restore
so there is no way that I can update the bio to allow me to boot from usb

the notebook is a Gateway gz 7330
Info on parts:
    cd = H-L data storage
    model gca-4080n ( AGYB23 )
    serial 505zj039899
    HDD = Hitachi travelstar
    model C25N080ATMR04-0
    P/N 08k0635
    ata ide 80g


bios
American mega trends v02.57

---

### Post by Garthhh on 2010-02-22
network boot is supported, but I can't get past the setting up of the static IP address
modem
ZyXel Prestige 660HW61

---

### Post by Rhubarb on 2010-02-22
It's a little tricky, and unfortunately I can't go into the details of exactly how to do it (as it's quite late, and I should be asleep).

It's possible to take the hard drive out of your laptop, put the hard drive into a cheap 2.5" HDD to 3.5" HDD converter, and plug that into a regular desktop computer.
Install Ubuntu to the HDD (it's probably best to make sure the desktop's HDDs are completely removed, to prevent accidental erasure of them).
Then put it back into the laptop, and it should all work!  :D

I do this for my old laptop, that can't boot from USB, that has no optical drive, has no functioning screen, and is unable to boot the Ubuntu Server kernel (even though I install Ubuntu server on it - the trick is to install the regular Ubuntu kernel as well).

These converters are usually quite cheap, can be found for about €10 at some computer / electronics stores.

---

### Post by Garthhh on 2010-02-22
I've gotten conflicting advice on that,
I actually set this pc's HDD up on a different donor& went back to this as it's not a dell with all that attendant weirdness.
I was just hoping for a way to be able to occasionally use a cd
I had just been emailing files or whatever to get around the lack of a CD on the notebook.
I guess it won't matter, since there is a bios update available, to allow boot from usb.

---


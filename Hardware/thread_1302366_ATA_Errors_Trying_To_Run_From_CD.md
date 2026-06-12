---
title: "ATA Errors Trying To Run From CD"
date: 2009-10-27
forum: Hardware
---

### Post by esoterica on 2009-10-27
Someone brought me a hosed laptop to see if I could get it running for them. I have no idea what the history is behind it other than it would not boot past the BIOS.

It's a Dell Inspiron B130 Laptop. I did take it apart and cleaned a ton of dust out of it. Noticed at one point a orange liquid had been spilled into the keyboard, it was well dried though. Owner said that happened a very long time ago and had been working fine 1 year after.

At this point I'm trying to determine if it's the IDE controller or the hard drive at blame. Trying to boot it to an UBUNTU 8 DVD I had laying around. First time I tried it ends up displaying countless ata01 errors and never loads the OS. I did manage to get it as far as running a memory test on it and it passed.

As long as the hard drive is installed it will not boot from the Ubuntu DVD. If I pull out the hard drive it boots into UBUNTU just fine.

This is confusing me because I was always in the belief that when you run UBUNTU from just the DVD it never touches the hard drive?

With that thought it has me wondering if this is the IDE (PATA) controller causing the errors, or just a bad hard drive. Obviously don't want the person to spend money on a new Hard Drive if its the controller at fault.

Any ideas or useful suggestions much appreciated.

---

### Post by Dark_Stang on 2009-10-27
A bad drive can cause a machine to lockup at, or immediately after, the POST screen. Hook another hard drive up to it and see if it keeps doing it. If it keeps locking up with a new hard drive then you know it's the motherboard. If it works fine then you know it's the hard drive. If it doesn't work out return the hard drive and buy a new laptop.

---

### Post by esoterica on 2009-10-27
Thanks, I don't have another drive around that old that will work in it, all mine are SATA. My point was to try and avoid swapping parts till it worked to figure out where the problem was, waiting for parts to come, then dealing with returning them.

Maybe someone can help with my thinking, if it was the controller wouldn't the DVD drive not work either? I guess whats confusing me is why does UBUNTU even care if a bad hard drive is in it, it sure doesn't care when there's no hard drive at all in it. I think if I can solve that mystery then I'd be comfortable just condemning the drive.

Not helping matters its a dam Toshiba drive so there aren't even any hard drive utilities I can boot to for it. I would never buy a Toshiba drive just for that ignorant on their part reason.

---

### Post by esoterica on 2009-10-27
No one else has any ideas on how to actually test an IDE controller or if it was bad would this also show up in the DVD drive as a problem?

---

### Post by Iowan on 2009-10-27
I presume you've checked BIOS for boot order? If it's set to try HD first...

---

### Post by esoterica on 2009-10-27
Boot order is set for DVD drive to boot first, then the HDD just because it was easier while trying to get Ubuntu to run when the HDD was still in it. Just to recap, when the hard drive is installed, Ubuntu looks like its going to load all the way and run, but just before it does it goes into screens full of assorted ata01 XXXX errors. I did run a full memory test from the Ubuntu disc, then got it to boot all the way into Ubuntu for about 5 minutes before locking up. Rebooting brought back the original problem. Searching found nothing burried in all the clutter that seems relavent.

Ubuntu loads and runs just fine from the DVD if the hard drive is physically removed, without fail.

Wish I could get it to run long enough with the hard drive in there so I could try

```
dd if=/dev/zero of=/dev/hda bs=1M
```

on it and possibly salvage the drive.

Also worth mention I suppose. I've seen bad hard drives before, usualy associated with the grind of death noise. This one makes no noise and seems to be spinning just fine.

---

### Post by Dark_Stang on 2009-10-27
A hard drive, even if it isn't clicking, grinding, or vibrating, can still be bad. Also, bad drives can cause machines not to pass POST. Optical drives, hard drives, and even floppy drives can do this. I'm sorry but at this point your only option is to put another hard drive into the machine and see if it works with that.

---


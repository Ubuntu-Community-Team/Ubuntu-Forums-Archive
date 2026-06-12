---
title: "USB Drive for FTP server"
date: 2012-02-21
forum: Hardware
---

### Post by enzobrands on 2012-02-21
Hi

I've recently put up an FTP server at home on an old pentium 3 PC. It's running Xubuntu 11.10. The PC only has about 50 GB of internal storage, so i attached a 500GB USB hard drive to it.

Now my question is if the drive would be OK to be running 24/7?

I've searched a lot on the internet but found either posts saying it would be no problem, or saying they will overheat or fail after a while...

In Windows the drive would shut itself down when youre not using it for a while, but in Xubuntu it does not do that. It's mounted via terminal in the FTP users map.

The case itself is made of plastic but the top is aluminium(i've read that it helps cooling). The aluminium's temperature is only about 30° degrees constant. The drive itself (Seagate's Barracuda 7200.10) is designed to operate between 0-60°C so that seems pretty reasonable.

I'm searching for users who had similar experiences with this...

Thanks in advance!

---

### Post by roelforg on 2012-02-21
Once had mine on for 1 week straight, shouldn't be a problem.
Those things are generally better cooled then internal hd's.
And, yes the hd will be powered down after a while, but when needed it'll be powered up which takes about 5s so don't worry.

Been there, done it.

---

### Post by WasMeHere on 2012-02-21
Welcome to the Ubuntu Forums enzobrands,

I have experience of similar setups, when the hardware in the case failed but the HDD was still good. It was a built-in ready-made for USB, so my colleague had to break the box to take out the disk. He put it in an empty USB box with good cooling. This same thing actually happened twice, and after that we buy separate boxes and HDD.

What about your old PC? If it is a desktop or tower with a good fan, maybe it would be a good idea to put the HDD inside (I guess there is only an IDE interface, no SATA). This would give you higher read and write speed than USB 2.0, but if the speed is OK, try it. If it works for a month, it will probably work for a year or two.

Finally, remember to take regular backups ;-)

Have fun finding out about Xubuntu
Olle

---

### Post by roelforg on 2012-02-21
> **Olle Wiklund said:**
> Welcome to the Ubuntu Forums enzobrands,

I have experience of similar setups, when the hardware in the case failed but the HDD was still good. It was a built-in ready-made for USB, so my colleague had to break the box to take out the disk. He put it in an empty USB box with good cooling. This same thing actually happened twice, and after that we buy separate boxes and HDD.

What about your old PC? If it is a desktop or tower with a good fan, maybe it would be a good idea to put the HDD inside (I guess there is only an IDE interface, no SATA). This would give you higher read and write speed than USB 2.0, but if the speed is OK, try it. If it works for a month, it will probably work for a year or two.

Finally, remember to take regular backups ;-)

Have fun finding out about Xubuntu
Olle

Just out of curiosity, did you place the hd at a well cooled area? Mine works fine, it may be because it's below a window...

---

### Post by enzobrands on 2012-02-21
> **Olle Wiklund said:**
> Welcome to the Ubuntu Forums enzobrands,

I have experience of similar setups, when the hardware in the case failed but the HDD was still good. It was a built-in ready-made for USB, so my colleague had to break the box to take out the disk. He put it in an empty USB box with good cooling. This same thing actually happened twice, and after that we buy separate boxes and HDD.

What about your old PC? If it is a desktop or tower with a good fan, maybe it would be a good idea to put the HDD inside (I guess there is only an IDE interface, no SATA). This would give you higher read and write speed than USB 2.0, but if the speed is OK, try it. If it works for a month, it will probably work for a year or two.

Finally, remember to take regular backups ;-)

Have fun finding out about Xubuntu
Olle

Yes i was thinking the same about the case, luckely i have two.

About inserting it in the PC, their are 2 connected HDDs, One with the OS (8GB) and another for extra data (40GB). Those are connected via PCI (it's a very old pc), I don't have a PCI to SATA and the speeds are OK (i don't heavily use it).

> **roelforg said:**
> Just out of curiosity, did you place the hd at a well cooled area? Mine works fine, it may be because it's below a window...

It's about 20 degrees max.



Anyway i guess i'm just going to keep it on, if it fails i'll post it here!

Thanks!

---

### Post by WasMeHere on 2012-02-21
> **roelforg said:**
> Just out of curiosity, did you place the hd at a well cooled area? Mine works fine, it may be because it's below a window... It was in an office in an industrial production building, ambient temperature, reasonably well air-conditioned.

---

### Post by WasMeHere on 2012-02-21
> **enzobrands said:**
> Yes i was thinking the same about the case, luckely i have two.

About inserting it in the PC, their are 2 connected HDDs, One with the OS (8GB) and another for extra data (40GB). Those are connected via PCI (it's a very old pc), I don't have a PCI to SATA and the speeds are OK (i don't heavily use it).



It's about 20 degrees max.



Anyway i guess i'm just going to keep it on, if it fails i'll post it here!

Thanks!
Yes, I keep suggesting that you try with your USB solution. If it doesn't fail within a month it will probably run for years.

---


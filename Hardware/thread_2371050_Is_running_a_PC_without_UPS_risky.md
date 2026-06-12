---
title: "Is running a PC without UPS risky ?"
date: 2017-09-10
forum: Hardware
---

### Post by linuxyogi on 2017-09-10
Hi,
My UPS is failing. When I connect my PC to the UPS the PC shuts within a second or two. When I connect it directly (without the UPS) it runs fine.

I dont have the cash right now to buy a new UPS.

We almost never face power failures here.

So my question is, is it safe tor run the PC without a UPS ?

---

### Post by jeremy31 on 2017-09-10
Can you change the setting so the computer doesn't shut down when the battery is depleted or just unplug the USB cable that connects the computer to the UPS?  I would think you just need a new battery if it is easy to replace

---

### Post by linuxyogi on 2017-09-10
> **jeremy31 said:**
> Can you change the setting so the computer doesn't shut down when the battery is depleted or just unplug the USB cable that connects the computer to the UPS?  I would think you just need a new battery if it is easy to replace

This UPS has no USB interface. The PC is shutting down even on AC power.

---

### Post by jeremy31 on 2017-09-10
Is this UPS in the computer case?  I am a bit confused because you stated
> When I connect it directly (without the UPS) it runs fine.
Now it shuts down when connected to AC?

I am used to these [img]https://images10.newegg.com/NeweggImage/ProductImage/42-101-311-14.jpg[/img]

---

### Post by linuxyogi on 2017-09-10
> **jeremy31 said:**
> Is this UPS in the computer case?  I am a bit confused because you stated

Now it shuts down when connected to AC?

I am used to these [IMG]https://images10.newegg.com/NeweggImage/ProductImage/42-101-311-14.jpg[/IMG]

It looks similar to this model 

[ATTACH=CONFIG]276677[/ATTACH]

I cant find the exact model. I purchased it on 2003. What I meant was its shutting down even when the main power is present (no battery involved).

---

### Post by jeremy31 on 2017-09-10
Are all the outlets on the UPS for backup power?  The ones I have used have outlets that just provide surge protection along with outlets for power backup.
Most contain a small 12V battery inside and they will fail to stay charged after a while.  I would just use a surge protector until you can replace or fix the UPS

---

### Post by efflandt on 2017-09-10
While you could possibly get drive corruption by shutting down while something is writing to the drive, or lose something in the delayed write cache that was not saved yet, I have never had a drive get corrupted due to power failure or forced manual power off if something hangs. So about all you might normally lose is something that had not written to disk yet. File systems like ext3 and ext4 have a journal file system that logs what it is going to do before it does it, to make recovery easier. But I was using ext2, which did not have a journal, since before Win95 and sometimes still use ext2 when installing Linux to SD/microSD or USB memory stick, and I cannot think of that ever being corrupted by unplanned power down. But I usually use a UPS on my main PC anyway, and a headless PC I have been running in my basement as an experiment almost non-stop 24/7 since 2003 (SuSE 8.2 on Celeron 333 MHz with 158 MB RAM).

I have had drives rarely fail, but that is usually gradual when they run out of reserve space to automatically remap into bad sectors regardless of OS. It was not due to power failure or forced power off. My last drive failure was when the Seagate drive on my PC from 2010 was 3 years old. I had a Linux partition at the far end of the drive which started getting corrupted when I got into Linux Steam and started filling up the end of the drive with games where physically smaller sectors at the center of the platters are trying to hold the same amount of data as physically larger sectors farther out. When replacing the drive I used Windows Disk Management to first shrink Windows to make more room for Linux before imaging that to the new drive, then reinstalled Ubuntu and copied over my home directory. Only a few game files had gotten corrupted (missing textures) and Steam was able to replace the corrupted game files.

You never know exactly how long a UPS is going to work. Cheap ones may constantly trickle charge the battery so the battery may not last that long before it needs replacement. Smarter ones tend the battery better and test themselves on battery backup power occasionally to warn you when the battery(s) need replacement. I have had the UPS in my basement on that old headless PC and my Internet gateway for very many years and only replaced its 2 batteries once. But I have had other UPS units fail before their 1 year warranty was up and warranty replacements lasted barely a year.

---

### Post by linuxyogi on 2017-09-10
> **jeremy31 said:**
> Are all the outlets on the UPS for backup power?  The ones I have used have outlets that just provide surge protection along with outlets for power backup.
Most contain a small 12V battery inside and they will fail to stay charged after a while.  I would just use a surge protector until you can replace or fix the UPS

Yes all (3) the outlets are for backup power.  

Looks like i need to buy a surge protector.

Thanks a lot to both for your replies.

---

### Post by kurt18947 on 2017-09-10
> **linuxyogi said:**
> It looks similar to this model 

[ATTACH=CONFIG]276677[/ATTACH]

I cant find the exact model. I purchased it on 2003. What I meant was its shutting down even when the main power is present (no battery involved).

I had an APC do the same thing; shut down even with no interruption of AC power. I wouldn't think a failing battery would cause that though I suppose it's possible. I replaced the APC with a different brand and so far so good.

---

### Post by SeijiSensei on 2017-09-10
The only UPS I have is connected to my server.  (I like APC products, which are well-supported in Linux using the apcupsd package.)  I've lost power to client machines on a number of occasions with few ill effects.  As others have said, the only issue concerns writing to the storage devices.  If the power goes out during a write, the data will be lost.  On my client machines I'm usually writing files to the server which is backed up.

---

### Post by linuxyogi on 2017-09-10
> **kurt18947 said:**
> I had an APC do the same thing; shut down even with no interruption of AC power. I wouldn't think a failing battery would cause that though I suppose it's possible. I replaced the APC with a different brand and so far so good.

Yes, thats exactly what is happening here. Unfortunately this malfunction has damaged my PSU and 1 ram module. I have purchased a new PSU but I am left with only 2GB of ram.

---

### Post by lammert-nijhof on 2017-09-10
I live in the Dominican Republic, now it is better, but the previous years we had a few power breaks per day. In the beginning I used a UPS, but the battery always did give problems after some months. I only use a surge protector now, one that handles 1200 Watt loads. I also disabled write caching in Linux using the Disks Utility. I never have problems with the disk contents. In the past with the UPS I did sometimes loose a number of desktop power supplies and motherboards and it is always the Small Form Factors power supply that died. 
Living in Europe I never used surge protection, since power breaks only occurred once in N years. But everywhere you have to make regular back-ups, never save on back-up space.

---


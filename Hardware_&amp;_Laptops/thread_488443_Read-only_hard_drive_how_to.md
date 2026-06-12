---
title: "Read-only hard drive? how to"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by longlegs on 2007-06-30
Hi ,
I'd like to write the 'live cd' to a hard drive so that it would run from the hdd as if it were still on cd, ie, no writing to the hdd allowed. THEN I want to do something in HARDWARE so that the hdd is read-only. Maybe a toggle switch or push-button disabling the write signal by shorting it to ground or something. I would use a second hdd (writeable) for data and swap files. Any hardware techs/engineers out there in Ubuntu land?
TIA
longlegs

---

### Post by GeeZor on 2007-06-30
harly think it CAN be done the way you are suggesting..

did you consider the software -way asin using the fstab file to mount the drive readonly?

example /etc/fstab:
```

# Device                Mountpoint      FStype  Options         Dump    Pass#
/dev/ad0s1a             /               ufs     ro              1       1

```

i realy hope you accomplish your goal since it has great potential....

---

### Post by longlegs on 2007-06-30
Hi GeeZor,
Negative on that software read-only. If software can turn off the write ability, then another software can turn it on, so it would not really be read only. On the other hand if a switch in the 'write enable' wire to the hdd is in the dis-able position, then only the physical operator at the computer can change it. If a virus cannot write to any system file, then it is virus proof.
Also, If I make a typo on a command line, I can't blow my install by accident.

Thanks for the reply!
longlegs

---

### Post by GeeZor on 2007-06-30
i totaly agree with you but you should consider the following:

Since you boot from a disk which is readonly, not even a virus is able to change anything in your /etc/fstab file.. (since it too is on the read-only disk).
the only way to change that is to mount the disk in a read mode, now how exactly would that happen while the system is running... 

only hole i am not sure of is wheter it is possible to mount the drive in read mode while it already is mounted as readonly but i dont that is possible.. 

When you find out how to hardware disable the writeability PLEEEAAASSSE let me know..
i just love things like that..

---

### Post by longlegs on 2007-06-30
Hi,
I'm not sure about this but I think that a 'virus like' program can do any thing to the system that can be done with the keyboard. This implies that it could dismount the system drive and remount it as RW?
BTW all my drives are eide, no sata's.
TIA
longlegs

---

### Post by GeeZor on 2007-06-30
please remember that on a linux system files you download are never exectable on your system. You have to change permissions to make it executable, one of the reasons virusses dont really do well on linux machine. 

But if you are in to experimenting, try unmounting the device that holds your primary filesystem (/etc, /usr/ etc.etc.) or try mounting the device whill it is mounted already ... see what happens

But i still get your worries from a security point of view. I realy hope that you find what you are looking for..

---

### Post by mcginnnc on 2007-07-01
[QUOTE=longlegs;2939204]Hi ,
I'd like to write the 'live cd' to a hard drive so that it would run from the hdd as if it were still on cd ...

Comment,
G'day from Oz. I agree, I use Ubuntu vr 7 Fiesty and would like to see a hard drive marketed that, like the old 3.5 floppy discs, you could flick a switch on the outside of your OS hard drive - and, viola, it would become read-only - just like a live CD. This hard drive would only need to be a 20mb job. Then you would have your main, say, 200gb hard drive with all your documents on - which you would back up all the time.
It would be virtually - virus-proof.
How about it, Seagate?
Cheers,
Neil.

---

### Post by longlegs on 2007-07-03
Hi mcginnnc ,
Since Seagate bought Conner, I prefer Fujitsu. But you have the Idea. Even better would be a drive with an odometer-like dial so you could 'set' the size of the (contiguous) initial block that was protected.

I still need a way to write protect a normal eide drive ( with hardware, not software) tho. 
Any help, anyone?
longlegs

---

### Post by longlegs on 2007-07-28
bump?

---


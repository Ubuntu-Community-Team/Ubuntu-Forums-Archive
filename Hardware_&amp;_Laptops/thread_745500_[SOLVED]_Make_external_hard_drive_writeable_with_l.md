---
title: "[SOLVED] Make external hard drive writeable with live CD."
date: 2008-04-04
forum: Hardware &amp; Laptops
---

### Post by Dzenhax on 2008-04-04
Help me Obi Wan Ubuntu, You're my only hope.

Okay, I'm not some cute hologram gal (c'mon, I'd just turn out to be your sister later if I was) but I need the help anyway.  And there *IS* a chick involved.

So this chick gives me her laptop and windows is dead.  I know, you're shocked.  I boot with a live windows cd and it finds nothing.  But, viola, Ubuntu live see her data.  Half done.

I plug in the external usb hard disk I brought for the occasion and it mounts read only.  I tried chmod 777 xhd, But it stays read only and I can't copy the data before I fry the existing partition.

What do I need to do to get her stuff off the diseased drive?

Many thanks, you guys always come through!

---

### Post by Rocket2DMn on 2008-04-04
If the external hard drive is ntfs, you need to enable writing for ntfs from Applications->System Tools->NTFS Configuration Tool.
Then you can mount the drive with
```
mkdir /media/external
mount -t ntfs-3g /dev/sdb1 /media/external
```
Change /dev/sdb1 to the appropriate device as listed in
```
fdisk -l
```
Then when you are finished with the drive, unmount it
```
umount /media/external
```
Normally all those commands require sudo, but I don't think it is needed from the LiveCD (I could be wrong though).

---

### Post by Dzenhax on 2008-04-04
Rocket2DMn

     The live CD didn't have the NTFS configuration tool.  I hooked the laptop with live cd into the network and installed it, and ntfs-3g.  That was all I had to do.  After that, and running the ntfs config I was able to write to either drive.  I chose to disable writing to the original and recursively copied the laptop's HD.  The data is happily being saved now.

     Still, the commands were good to have and I'll keep them in mind if the next crisis doesn't go so smooth.  Thanks for the lesson jedi master.  I couldn't have gotten started without your input.

     Great Avatar by the way.  I'd love to steal it, but that isn't nice, so I'll just have to be jealous.

     Oh, and lastly, we do need sudo, even with live.

---

### Post by Rocket2DMn on 2008-04-04
> **Dzenhax said:**
> Rocket2DMn
Still, the commands were good to have and I'll keep them in mind if the next crisis doesn't go so smooth.  Thanks for the lesson jedi master.  I couldn't have gotten started without your input.

Great Avatar by the way.  I'd love to steal it, but that isn't nice, so I'll just have to be jealous.

Oh, and lastly, we do need sudo, even with live.

Hehe, you can get avatars at [http://tux.crystalxp.net/](http://tux.crystalxp.net/) - they got some great ones.

Thanks for the info on sudo with the LiveCD, that's rather useful for the future, as well.  Good luck.

---


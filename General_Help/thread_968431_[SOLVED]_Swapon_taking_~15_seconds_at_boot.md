---
title: "[SOLVED] Swapon taking ~15 seconds at boot"
date: 2008-11-02
forum: General Help
---

### Post by CrucifiedEgo on 2008-11-02
I have a fresh install of wubi over a fresh install of vista on my Sony laptop(VGN-NR260E).  Everything works great, except that the boot process was fairly slow.  I ran a bootchart, and it seems that for some reason, swapon is pegging one of my CPU cores for a good 20 seconds with no real reason that I can see. Here's the relevant few lines in dmesg (the last thing that happens before swapon is ndiswrapper is loaded from /etc/modules.)

```
[   16.693814] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2
PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   16.693952] usbcore: registered new interface driver ndiswrapper
[   17.434721] EXT3 FS on loop0, internal journal
[   31.319538] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k

```

/etc/fstab:
```
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```
And here's a bootchart from the same boot:
[http://stash.jamesandportia.com/images/intrepid-20081102-3.png]("http://stash.jamesandportia.com/images/intrepid-20081102-3.png")
You can see there that what's actually taking up the CPU time is mount.ntfs, which is why i'm posting this in the wubi forum (move if needed).

Anyone ever seen this, or any hints as to how i might lower this time down?

---

### Post by ago on 2008-11-03
That is because it is probably very fragmented
You can turn it off completely by simply renaming the swap.disk file

---

### Post by CrucifiedEgo on 2008-11-03
I checked -- of course, this is a brand new vista install, but I did a defrag anyway, and that's not an issue.

---

### Post by ago on 2008-11-03
Remove the file then create a new one (doesn't need to be big)

dd if=/dev/zero of=/host/ubuntu/disks/swap.disk bs=1M count=100
sudo mkswap /ubuntu/disks/swap.disk

---

### Post by CrucifiedEgo on 2008-11-03
d'oh!  that seems so simple now that you say it.  I'll give it a try once I can wrestle the laptop away from my wife (she's digging ubuntu after finally getting fed up with windows!)

---

### Post by CrucifiedEgo on 2008-11-04
This fixed it.  Not sure what was wrong with the first one, but thanks for the tip.

---

### Post by carljmoss on 2008-11-05
I know this has been marked as solved, but quite a few people - myself included - have hit the same problem with Intrepid. In my case mount.ntfs was taking almost 20 minutes to complete!

Defragging the hard drive helped for me, as further did creating a new swapfile once inside Ubuntu. There's still an appreciable delay in mount.ntfs, although now I measure it in seconds not minutes.

Has anyone reported this as a bug?

---


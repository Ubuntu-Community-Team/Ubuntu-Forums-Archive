---
title: "[SOLVED] how long should dd take to clone a 250 GB drive?"
date: 2008-09-08
forum: General Help
---

### Post by Krusty Ruffle on 2008-09-08
Running from a minimal live disk, pentium 4 2.4 Ghz with 1 GB of DDR 333, no graphic environment.
Exact command:
```
dd if=/dev/hda of=/dev/hdb bs=512k
```

both drives are 250 Gig ata 133

It's been running for about 30 hours now, both drives feel like they are running and the ide light is lit up solid, I've also seen no errors onscreen. I know the small block size will make it take longer, but I'm really starting to wonder about this....

Thanks to anyone who can give me an estimate on this and help bring me peace of mind :)

---

### Post by HermanAB on 2008-09-08
Something is wrong. Open another konsole and check what is going on.

You can see what is going on using kill:
# ps -e|grep dd

Note the dd process number, then:
# kill -USR1 ddpid

Every time you send the above signal, dd will hiccup and spit out how many bytes were copied, then continue on its way.

BTW, bs=100K is usually the fastest on my systems.

Cheers,

Herman

---

### Post by Krusty Ruffle on 2008-09-08
> **HermanAB said:**
> 
Note the dd process number, then:
# kill -USR1 ddpid

Every time you send the above signal, dd will hiccup and spit out how many bytes were copied, then continue on its way.

Heh... Something must have been wrong, when I used that command it just killed the process completely, the disk was about 75% done so I have 3 good partitions and a corrupted fourth, but I can work with that. I'm just going to rework the fourth partition and hand copy the data in it...

Thank you for your reply, even if it didn't work ut the pest possible it did at least work out :)

---


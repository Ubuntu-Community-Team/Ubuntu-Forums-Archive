---
title: "[SOLVED] Would booting from a memory card be more efficient?"
date: 2008-09-03
forum: General Help
---

### Post by sexyclient on 2008-09-03
OK, so I've been pondering the question of booting from a memory card for a while now.  With the state that these little buggers (SD, SDHC, etc.) are in right now, you can get one relatively cheaply, and (as I have been lead to believe) can offer performance boosts over standard hard drives.

Right now, I'm considering getting a new computer - possibly an [asus eeebox]("http://event.asus.com/eeepc/microsites/eeebox/en/index.html"), or maybe a netbook if one comes out with dvi/hdmi output so I can hook it up to my TV to play HD content on it.  The main idea is to get a lightweight computer that I could use to browse the web, play 720p HD movies on (through xbmc), and (if its a netbook) carry it around.

The problem with this plan, though, is that all my options come with limited space, and hard drive performance.  That's why I've devised the clever scheme of using a memory card to house my OS (ubuntu, of course) and using any of my new computer's incumbent storage for whatever superfluous tasks that requires it.

So I ask: Would booting Ubuntu or any other OS from a memory card be faster or in any way more efficient?  How about the drawbacks (stability for example)?

---

### Post by ntbutler on 2008-09-03
In all honesty, i can't really tell, best thing to do may be to just try it, it can't hurt.
You will need to ensure that your bios can allow you to boot from memory cards, otherwise you will fall over from the start. If you can, as long as the system hardware you buy has a descent clock speed, bus speed etc then it sounds like the way to go. It seems to be something along the lines of the eeepc solid state hard drives anyway, it may just come down to a test of, on that hardware, which one a) can you boot from and b) gives a better response time.
If you do give it a go, give us a heads up and it might be something i may try for my next upgrade.

---

### Post by anjilslaire on 2008-09-03
Why don't you just install the OS on the built-in drive, and use the external flash drive to load your media? The external storage card will wear out quicker with all the read-writes used by the OS, and the internal storage will be better suited to the OS.

I realize thats not what you're wanting to do, but I think you'll be happier this way in the long run.

---

### Post by mb_webguy on 2008-09-03
> **anjilslaire said:**
> Why don't you just install the OS on the built-in drive, and use the external flash drive to load your media? The external storage card will wear out quicker with all the read-writes used by the OS, and the internal storage will be better suited to the OS.

I realize thats not what you're wanting to do, but I think you'll be happier this way in the long run.

+1

Even if your BIOS allows you to boot from a memory card, the advantages (a possibly faster startup) don't outweigh the disadvantages (rapid deterioration of the memory card due to frequent read/write operations).  And besides, you're not really freeing up any storage by doing this, since if you have a 100GB hard drive and a 4GB memory card, you have a total of 104GB, regardless of where you put the OS.

---

### Post by Ryadt on 2008-09-03
> **sexyclient said:**
> OK, so I've been pondering the question of booting from a memory card for a while now.  With the state that these little buggers (SD, SDHC, etc.) are in right now, you can get one relatively cheaply, and (as I have been lead to believe) can offer performance boosts over standard hard drives.

Right now, I'm considering getting a new computer - possibly an [asus eeebox]("http://event.asus.com/eeepc/microsites/eeebox/en/index.html"), or maybe a netbook if one comes out with dvi/hdmi output so I can hook it up to my TV to play HD content on it.  The main idea is to get a lightweight computer that I could use to browse the web, play 720p HD movies on (through xbmc), and (if its a netbook) carry it around.

The problem with this plan, though, is that all my options come with limited space, and hard drive performance.  That's why I've devised the clever scheme of using a memory card to house my OS (ubuntu, of course) and using any of my new computer's incumbent storage for whatever superfluous tasks that requires it.

So I ask: Would booting Ubuntu or any other OS from a memory card be faster or in any way more efficient?  How about the drawbacks (stability for example)?
You probably will be able to install it if your card is 4gb. But unless your BIOS has an option to boot from card reader, you will have to install a boot partition on your HD.

---

### Post by sexyclient on 2008-09-04
Thanks for the feedback all.  

This is all, of course, assuming that I can indeed boot from a memory card.  Also, I'm not looking to increase space - that isn't a concern seeing as how inexpensive external hard drives, memory cards, and flash drives are now.  

I'm more interested in finding out the performance enhancements.  From what I've been led to believe, it would lead to faster boot and application load times - though exactly how fast of a speed increase is completely out of the scope of my speculation.  I also figured that one of the drawbacks may include accelerated drive deterioration compared to a standard drive - and yet again, I'm left with no reliable basis with which to make any sort of accurate speculation on just how much this would reduce the drives lifespan, and any reference for comparison between the lifespan of a memorycard vs a standard HD hosting an OS.

I'd like to find out though, and also any other bonuses and/or drawbacks that may present themselves.

I've also been wondering if I could move parts of the OS that are the most write-intensive to the standard hard drive and keep other parts of the OS hosted on the memory card (maybe things like log files?).  I know the home folder can be stored on a separate drive/partition but I'm not so sure about dissecting more of the OS.

I definitely plan on conducting this experiment once I get my new computer, whatever it may be.

---

### Post by mb_webguy on 2008-09-04
> **sexyclient said:**
> I've also been wondering if I could move parts of the OS that are the most write-intensive to the standard hard drive and keep other parts of the OS hosted on the memory card (maybe things like log files?).  I know the home folder can be stored on a separate drive/partition but I'm not so sure about dissecting more of the OS.

You can mount any directory on a separate partition.  Linux is very flexible that way.  But it seems to me that any boost in performance is going to be due to the faster read/write speed of the memory card, and that by moving the bits of the OS that involve the most read or write operations to the hard drive, you would be defeating the purpose of putting the OS on the memory card in the first place...

Also, except for possibly a few fractions of a second off of startup, I don't know that you'd necessarily notice any difference in performance.  Hard drive access speeds aren't as fast as those of flash memory, but they're pretty darn fast.  And once a program or file is loaded into memory, storage takes a back seat for the most part.  Therefore, while a program might load faster from a memory card, it won't necessarily perform any faster once it's loaded.

---

### Post by sexyclient on 2008-09-04
But surely, if I were to mount only the most read/write intensive portions of the OS onto the standard HD I'd be able to achieve some form of balance between acceptable memory card integrity and (substantially?) faster boot times if nothing else.  Maybe I could put parts of the OS that are only used during boot up (if there are any, and hopefully there are), and other parts that aren't constantly hammered with read/write requests onto the memory card and just keep the rest on the standard HD.

---

### Post by mc4man on 2008-09-04
Here is a very **basic** look at performance differences of sdhc, ssd,  and a run of the mill laptop hdd.
Even the very best sdhc cards with a fast reader can't match a hdd or are even in the same ballpark as a ssd drive  in terms of transfer rate (read, write)

[http://www.notebookreview.com/default.asp?newsID=4258](http://www.notebookreview.com/default.asp?newsID=4258)

---

### Post by sexyclient on 2008-09-04
That puts an end to all that.  Thanks, I think I'll stick with a standard HD.

---

### Post by mc4man on 2008-09-04
you did note that they can be useful as secondary storage, particularly in laptops with a small primary drive (either hdd or ssd

---


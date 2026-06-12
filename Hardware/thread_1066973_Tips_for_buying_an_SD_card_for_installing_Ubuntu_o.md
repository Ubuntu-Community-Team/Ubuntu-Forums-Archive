---
title: "Tips for buying an SD card for installing Ubuntu on please :)"
date: 2009-02-11
forum: Hardware
---

### Post by KenBW2 on 2009-02-11
I'm looking at buying a faster SD card for my EeePC, as the current Class 4 one I have is painfully slow.

I've seen one that quotes "Write speed up to 6MB/sec, Read speed up to 20MB/sec" from Class 4, and one that quotes "15MB/sec Read/Write speeds" from a Class 4. Are these any good, based on the fact that they're classed as only having 4MB/s?

Can anyone give me a few tips or even point me at a good one for this purpose? I'm in the UK, for purposes of delivery.

Thanks in advance :)

---

### Post by c1981 on 2009-02-11
Hi there,

To be honest the whole class 4 - 6 is more like a marketing scheme, as are
most "HD video SD cards". You're best bet would be a card that equals "133x" or more; usually Sandisk Extreme III or Kingston Ultimate series.

At the bottom of your post there is also mention of you having a swap file on your 8 gb SD card; - as far as I know that's a big no-no as it will slow down performance considerably, and probably kill the SD card sooner - as it could very well drastically up the amount of writes to the card (which is limited to a few hundred thousand writes per cell).

It would be better to upgrade the Ram in the eee to say 2 gb ddr-2 667 sodimm; it boosted my Eee PC 701 considerably.

Hope that helps.

---

### Post by KenBW2 on 2009-02-11
So you're saying the Class 4 issue is something to ignore? That [15MB/s one was a Sandisk Ultra II]("http://www.play.com/Electronics/Electronics/4-/5747498/SanDisk-16GB-SD-HC-Ultra-II-Memory-Card/Product.html") - is that good enough then?

WRT the Swap thing. It's been on there over a year now and hasn't shown any problems :) Unfortunately I bought the 2G EeePC so I can't upgrade the RAM :(

Thanks for the help :)

---

### Post by c1981 on 2009-02-11
A 15Mb/s card (like Sandisk ultra II) is too slow too comfortably boot anything other than SystemrescueCD or GeexBox (mini media center distro with eee optimizations); Any card approaching at least 20+ Mb/s write and 30+ Mb/s read is generally ok. 

I bought a class 6 SDHC card a while ago; useless for anything other than storing basic files.

It'll have to be a Sandisk Extreme III / Kingston Ultimate 266X or better;

this one should do nicely:

[http://www.sandisk.com/Products/Item(2687)-SDSDX3-016G-A31-SanDisk_Extreme_III_SDHC_16GB.aspx]("http://www.sandisk.com/Products/Item(2687)-SDSDX3-016G-A31-SanDisk_Extreme_III_SDHC_16GB.aspx")

I've used a 133X speed Transcend CF card to boot my desktop for over a year now; only when it's updating does it become too slow for comfort. The card averages at 35 Mb/s read and 20 Mb/s write.
Recently I've upgraded to a Kingston Ultimate 266X CF (40 Mb/s read/write) and I've officially said goodbye to having OS's installed on harddrives. (All data is stored on file-servers). 

On my Eee I use the internal SSD (I have the 4 gig version..) as root partition and the class 6 SDHC card split in 2 partitions: /home & /data
no swap file, no access time updates etc. Works like a charm and saves the SSD: most writes are done to the SD card, unless it is updating software. This way I can toss the (cheap) SD when it dies and save the SSD as much as possible.

Although each cell in the SD can be written many, many times over - and wear-leveling algorithms are in place (depending on card quality) - they do die eventually. With flash memory age isn't a factor, the number of writes is. I've deliberately stress-tested a few different CF types by endlessly wiping and deploying images onto them; and the cheaper ones died a lot sooner than expected and a lot sooner than a HDD would have.
When using a flash card as swap space, the number of writes are far more erratic and larger in number. Although I must admit that in the Eee's case, it generally doesn't do that much swapping anyway (when running optimized distro's like Easy Peasy / Ubuntu Eee / Xubuntu or even Suse).

Sorry about the RAM suggestion - I forgot about the 2G surf version..

No problem :-)

---

### Post by c1981 on 2009-02-11
P.S If you decide to get the Sandisk one; don't get it from the Sandisk site
    posted in the link; the 8GB version should be around € 42 - no more, or 
    something is amiss. ;-)

---

### Post by KenBW2 on 2009-02-11
> A 15Mb/s card (like Sandisk ultra II) is too slow too comfortably boot anything...

I currently boot Ubuntu from a [[COLOR="Blue"]cheap Class 4 SD card[/COLOR]]("http://www.play.com/Electronics/Electronics/4-/3511925/Play-com-8GB-SD-HC-Memory-Card/Product.html"), and wouldn't describe it as uncomfortable - just irritating :). 15Mb/s would be more than 3 times the speed of that, which would do me nicely. Or have I understood it wrong?

---

### Post by KenBW2 on 2009-02-15
Don't matter - I just bought a Dell Inspiron Mini 9 instead :D

---

### Post by c1981 on 2009-02-17
Sorry about the late reply; it's been mayhem the past week.

30Mb/s would 've been fine - but then so is a new laptop ;-)

---


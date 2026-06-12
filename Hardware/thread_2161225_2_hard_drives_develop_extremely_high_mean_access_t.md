---
title: "2 hard drives develop extremely high mean access time - SMART says OK - trust it?"
date: 2013-07-09
forum: Hardware
---

### Post by Dreamer Fithp Apprentice on 2013-07-09
I have 2 internal SATA hard drives that both started getting extremely slow at about the same time. One of them was almost new. Smart still says they are ok. External USB drives worked fine. So I assumed it was my onboard SATA controller and replaced my mobo. Oops. They are still slow. Average access time like 1.4 seconds. Any ideas other than 2 HDs just coincidentally went bad at the same time and maybe SMART is just kinda dumb after all?

---

### Post by hansdown on 2013-07-09
Hi Dreamer Fithp Apprentice .

1.4 seconds seems kinda.............not slow.

I realize, that immediate gratification is all the rage, but.... seriously?

Let's look at why this may be, please.

Could you please post your hardware specs?

Also, please post your os version.

Thanks.

---

### Post by Dreamer Fithp Apprentice on 2013-07-10
> **hansdown said:**
> Hi Dreamer Fithp Apprentice .

1.4 seconds seems kinda.............not slow.Actually, that's pretty slow. Should be about a hundredth of that. Perhaps you are thinking milliseconds. Which is what I should have reported in, seeing as the value would usually be measured in that. Mea culpa, I was being flip. The values I get running a benchmark vary quite a bit on different runs but close to half seem to be somewhere near where they should be, around 15 ms or so, and close to half are over a thousand. I'm wondering if the high figures come from averaging several normal times and one REALLY LONG one.
> **hansdown said:**
> Could you please post your hardware specs?

Also, please post your os version.Asus board with Athlon II dual core
 [ more detail here:
[http://www.ebay.com/ctg/ASUSTeK-COMPUTER-M4A77TD-Socket-AM3-AMD-Motherboard-/78615755?_tab=1&_trksid=p2047675.l2644](http://www.ebay.com/ctg/ASUSTeK-COMPUTER-M4A77TD-Socket-AM3-AMD-Motherboard-/78615755?_tab=1&_trksid=p2047675.l2644) ]

 with 4 gB RAM. 64 bit Precise Lubuntu with Mate DE.

I have one of the 2 drives this is an issue with in now (I need another SATA power cable before I can hook up the other again.) I ran ```
sudo fsck -M -P -V -f -D /dev/sdaN
``` on all 3 partitions and found no errors in sda1 and sda2 but in the third, only other, and oddly denominated sda4 fsck said there was no "lost and found" and did I want to create one and I answered yes. No other errors were reported. I believe these are all primary partitions, although I could be mistaken. Why the 3rd one is named sda4 is a mystery to me. Possibly it had 3 partitions and I deleted the 3rd and expanded the 4th. Could this have anything to do with the slow occasional radically slow reads? I should also mention the first 2 partions are bootable, or should be, but since the slowing started they won't boot.

Attached is a typical run of the benchmark.

Thanks, Hansdown.

---

### Post by suppur5 on 2013-07-13
Dude, calm down. 1.4 isn't that long, as long as the sectors are good and smart reports back good I wouldn't worry so much. Them getting slow at the same time may have been something as simple as a software update. Run a memory test if you must. I doubt the hard drive is nothing if they both slowed down. Now if one did I'd worry about bad sectors. Smart didn't report back any bad sectors did it?

---

### Post by Ranko Kohime on 2013-07-14
1.4 seconds is 1,400ms.  We're talking about the time from when the disk receives an order for data and when that data is transferred into RAM.  And the OP says that is his AVERAGE.  That is so far outside of the normal range as to make me suspect the drives.  (and since the controller, i.e. motherboard, has already been replaced, that is ruled out of the equation)

@Dreamer: Which program are you using to do the benchmarks?  I use gnome-disks (formerly palimpsest), and it shows all of the data points in the chart that it derives the average from.  So you would be able to tell if it's one really long access amongst a sea of normal results, or consistently poor access.

ETA: For reference, most of my internal drives are in the range of 15-20ms, with perhaps 1 or 2 fliers up around 100-150.

---

### Post by Dreamer Fithp Apprentice on 2013-08-11
Thanks, Ranko. Sorry I'm tardy. My internet connection was down for a while and then the forum was down. I decided to put those drives away and not power them up until I have another drive with enough capacity to copy all the data off them before I do anything else. Better safe than sorry. So for now, I've shelved the problem, pending some purchases. Good point about the benchmark program showing the individual data, not just the averages. I should have thought of that. I can't answer about the name of hte program I benchmarked with because in the meantime I gave up the on 64 bit Precise and installed Debian testing, Jessie, the Mint variety over it. I just ran into too many problems with Precise. My plan now is to copy all the data off as soon as I have the hardware and them repartition and reformat those drives and then test them again.

---


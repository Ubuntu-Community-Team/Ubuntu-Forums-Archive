---
title: "3 TB External HDD + U 10.10 = 802 GB!? WHY!?"
date: 2011-03-19
forum: Hardware
---

### Post by Zaytoven on 2011-03-19
I'm running the 64 Bit version of 10.10 and I have an Hitachi 3 TB HDD that I use in an icy dock external enclosure so I can backup all of my video files and etc. When I hook up the HDD to my computer it is detected as an 802 GB HDD. First I bought a Western Digital 3 TB and it did the same thing so I returned it and bought an Hitachi since I have a 2 TB Hitachi and it has worked perfectly for me for over a year. Was wondering what do I need to do to get my full 2.7 TB or whatever it will be after a proper formatting.

---

### Post by Zaytoven on 2011-03-19
any advice?

---

### Post by gordintoronto on 2011-03-19
Here is a writeup about the issue with drives larger than 2 TB:
[http://www.ibm.com/developerworks/linux/library/l-gpt/index.html](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) 

If I'm reading that correctly, you need to use the 64-bit version of Ubuntu, and then you should be able to partition the drive with Gparted.

Or perhaps it will never work with your icy dock. Can you install it internally?

---

### Post by srs5694 on 2011-03-19
> **gordintoronto said:**
> Here is a writeup about the issue with drives larger than 2 TB:
[http://www.ibm.com/developerworks/linux/library/l-gpt/index.html](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) 

If I'm reading that correctly, you need to use the 64-bit version of Ubuntu, and then you should be able to partition the drive with Gparted.

No, you're not reading that correctly. I can speak authoritatively on the issue, since I wrote the article to which you've linked! ;)

A 32-bit version of Linux will work fine with large drives. The trouble is with the Master Boot Record (MBR) partition table, which has a limit of 2^32 sectors, which works out to 2 TiB with 512-byte sectors. The newer GUID Partition Table (GPT) scheme supports 2^64 sectors, which gives a lot of room for growth. There's *no* correlation between the bit-width of MBR vs. GPT and the bit width of the OS. 32-bit versions of Linux work fine with GPT, and 64-bit versions of Linux work fine with MBR.

> Or perhaps it will never work with your icy dock. Can you install it internally?

I've heard of external enclosures having their own 32-bit limits, and it's entirely possible that it's the docking station that's to blame in this case. I recommend contacting the manufacturer about this issue. They might or might not give you good information, though; customer support representatives are often ill-informed about bleeding-edge technologies like 3 TB hard disks. There's a chance that you'll find something in the device's manual or specifications sheet, too.

---

### Post by Zaytoven on 2011-03-20
I'm running the 64 Bit version of Ubuntu. I tried formatting it in Gparted but it only gives me 745 GB after formatting:-(. Guess I will have to install it internally. Hope it works when I install it internally :-(

---

### Post by Zaytoven on 2011-03-20
eh, i got bored and took the HDD out of my icy dock and popped it into the desktop itself and it formatted out at 2.5 TB. Should I now take it out of my desktop and put it back into my desktop or will I have some issues? Its formatted GDP and Ext4.

---

### Post by srs5694 on 2011-03-20
> **Zaytoven said:**
> eh, i got bored and took the HDD out of my icy dock and popped it into the desktop itself and it formatted out at 2.5 TB. Should I now take it out of my desktop and put it back into my desktop or will I have some issues? Its formatted GDP and Ext4.

Do you mean "...out of my desktop and back into my external enclosure..."? If so, chances are that won't work, but I can't be positive of that.

I'd speculate that the enclosure has its own 32-bit limit, which means that it's seeing only the first 2 TiB of the disk, and then "wrapping around," effectively lopping off the first 2 TiB of the disk. If so, when you put the disk back into the external enclosure, the current partition table will be 100% useless and the enclosure will still report the disk as being much smaller than it is.

As I said, you can contact the manufacturer about this. They might be clueless, but they might also have definitive information on this issue. If so, and if they confirm that the enclosure works only with sub-2TiB disks, then you'll have to either use the disk as an internal or buy a new enclosure that doesn't have this limitation.

---

### Post by Zaytoven on 2011-03-20
yup thats what I was talking about. dang it lol. Guess I'll just have to get another 2 TB for my enclosure once they get a little bit cheaper or hope for an firmware update for this enclosure or something lol. I didn't even know 3 TB was new technology I just saw that it was on sale on newegg for $170 free shipping and added it to the cart.

---


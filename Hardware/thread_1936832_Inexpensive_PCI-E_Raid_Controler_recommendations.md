---
title: "Inexpensive PCI-E Raid Controler recommendations"
date: 2012-03-06
forum: Hardware
---

### Post by Losergamer04 on 2012-03-06
I'm looking for advice on an inexpensive raid controller for a computer upgrade I am going to do.  I require dual boot (unfortunately Windblows for my BS degree and gaming) and it cannot install on a software raid of its own (you can't make one like you can Linux and install Windows 7.  I'm looking to do a 4x64GB SSD (too much? never).  What have you used that has the following specs that's cheap?  [THIS]("http://www.newegg.com/Product/Product.aspx?Item=16-115-077&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=linux&Page=1#scrollFullInfo") (HighPoint RocketRAID 640) is the best I could find.  
SATA III
PCI-E 4X
Works with Linux and Windblows

I've seen conflicting reports on the Linux support for the card.  I am  guessing support is in the newer kernels but I haven't found anything  definitive.   That, and perhaps there is another good card I am missing?  Any input would be appreciated.

---

### Post by Losergamer04 on 2012-03-07
No one has experience with Ubuntu and this raid card or one similar to it?

---

### Post by Jagoly on 2012-03-08
Trust me, you're putting yourself up for a hell of a lot of work for little reward. Putting the drives in raid will only speed up sequential read/write speeds, and not random access. Truthfully, a single 240gb drive would be far simpler, cleaner, more compatible, have better random access times, and be not alot slower in sequential performance.

I'll use corsair drives for an example. For around $370, you can get a force GT 240gb.

To get four force GT 60gb drives, that's around $410. Then factor in atleast another $160 for a decent raid card, and your paying a ridiculous amount of money.

Random i/o performance will be better on the single drive, and sequential won't be far behind. And you don't have to worry about the whole lot failing apon one of four drives dying. And an extra $200 to spend on something else isn't bad either.

There are much better places to spend the money.

May I ask what your other specs are?

---

### Post by Losergamer04 on 2012-03-08
I'll be upgrading when Ivy Bridge comes out and using the intergrated graphics.  I'm aiming for 16GB of memory.  Sound is the Xonar DX (great for $30!).  
 
I know it's a lot of work for little reward, but I'm crazy like that.  I think most of us Linux nerds just a lot of things for craps and giggles.  And you can find SF based drives for as low as $1.10/GB.  
 
I have to disagree with the sequential reads.  In theory, with four quality drives I could nearly max the card's through put at almost 2GB/sec read.  
 
Another reason I want the card is the lack of TRIM.  When a drive gets "dirty" the write performance drops like a rock.  Upping that dropped number by 4x makes the inevitable slow transfer rates more transparant. I found this to be true on my 60GB Vertex 1 SSD's I used to have in a Motherboard RAID in Windblows.

---

### Post by Jagoly on 2012-03-08
Yes, all those points are technically true. And yes, it's your money. Mabey two 120gb drives. Most 60gb drives aren't as fast to start with as there larger bretheren.

And no, sorry, I have no experience with highpoint raid controllers :-(
Good luck :-)

---


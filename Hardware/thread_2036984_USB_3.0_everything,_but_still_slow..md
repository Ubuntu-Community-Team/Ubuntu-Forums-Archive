---
title: "USB 3.0 everything, but still slow."
date: 2012-08-03
forum: Hardware
---

### Post by WinRiddance on 2012-08-03
The last few days I've spent looking at many threads on different forums. I was hopeful that this post holds the key since all but one of my drives/partitions was EXT3, but this didn't help either.
[http://askubuntu.com/questions/110304/slow-usb-3-0-speeds](http://askubuntu.com/questions/110304/slow-usb-3-0-speeds)
The second picture below shows the transfer speed in progress from one EXT4 formatted disk to another EXT4 formatted disk. No different than when both of those were formatted to EXT3.

[COLOR=Indigo]Here's the entire scoop. I purchased a new laptop about 3 months ago, primarily because it had USB 3.0 ports and I do a lot of work with image, movie, and other types of file transfers. I also purchased a Linux compatible USB 3.0 hub and made sure that my external drives (all but one) were also USB 3.0 compatible. Disk manager (see images) shows that my drive(s) are capable of 480 MBit/Sec speed and that the disks are healthy. However, when I transfer large files, this still takes place at snail pace. I'm getting seriously frustrated and just can't figure out what the heck is going on.[/COLOR]

I have a 64 bit quad core Intel I5 processor, 8 GB of RAM, and 256 MB dedicated graphics memory. It's a Dell Laptop with Ubuntu ... but I'm running the Mate Desktop (love it) with custom installed XFCE panels (like those the best out of all panels). Does anyone know how I can get my USB 3.0 speed properly working with Linux? Thanks in advance ...

.

---

### Post by WinRiddance on 2012-08-04
Wow, really? Bummmmmeeer ... !!!
Nobody knows anything specific about getting the most USB 3.0 speed out of Linux/Ubuntu? :o :(

.

---

### Post by Ubun2to on 2012-08-04
I got a laptop with 2 USB 3.0 ports from System76. They guarantee Ubuntu support with all of their products.
The one thing I can think of that would make the speed slow down a lot is if you were using a USB 2.0 cable, rather than a 3.0 cable. Regardless of whether your device is 3.0 or 3000.0, the thing that can really undermine the speed of the device is the connector. Make sure they are USB 3.0 cables, and if they aren't order new cables.
Also, when you got your laptop, did it come with Windows? If not, that is probably why-the drivers in the kernel might only be for 2.0, and you didn't get any proprietary drivers for the 3.0.
Those are just my thoughts.

---

### Post by WinRiddance on 2012-08-06
Yeah, that's exactly what I'm suspecting ... that I received USB 3.0 capable drives with incorrect cables. Two of the drives have standard USB 2.0 power cables with the little, almost perfectly square end that goes into the connector for power and the USB connector portion of the same cable isn't blue either. Looks just like a standard USB 2.0 power cable that printers use ... except that it is a little thicker than most.

I'll be testing that theory shortly as I just purchased USB 2.0 to USB 3.0 adapters as well as USB 3.0 cables that will fit from the drives to the adapters and then the USB 3.0 port. If the theory is correct, I should at least be able to attain full USB 2.0 transfer speeds of 45 to 60 MBit/sec. at that point. We'll see, and I'll report back ....

.

---

### Post by typhoon_tip on 2012-08-06
It also depends on hard-drive speeds and what you are copying. For instance, if you copy a lot of large, small files, you will never get close even to USB 2.0 speeds. Copying a very large, single file will do a proper test.

Moreover, before you commence, please go to the Disk Utility application in Ubuntu, and run a Read Benchmark Test on your internal Hard Drive. This will give you the average read speed of your hard drive. If you are copying, in some cases USB 3.0 is faster than internal HDD, and thus cannot exceed the limit of the speed given you by the benchmark test.

---

### Post by Ubun2to on 2012-08-08
> **typhoon_tip said:**
> If you are copying, in some cases USB 3.0 is faster than internal HDD, and thus cannot exceed the limit of the speed given you by the benchmark test.

Depends on what the RPM is for your hard drive. The real test would be to see if 3.0 can transfer data faster than a solid state drive.

---

### Post by typhoon_tip on 2012-08-08
> **Ubun2to said:**
> Depends on what the RPM is for your hard drive. The real test would be to see if 3.0 can transfer data faster than a solid state drive.

Exactly but also other things like cache, controller, and what you are copying. That's why I asked him to benchmark his source driver :popcorn:

---

### Post by WinRiddance on 2012-08-09
Well, I guess I'm just too ignorant as far as USB speeds are concerned. I'm not a USB techie so when I buy a computer that says mind boggling USB 3.0 transfer speed as well as the appropriate USB 3.0 drives/ports to go with that ... there's really nothing that anyone can say which would make me _**truly**_ _**understand**_ _**why**_ transfer speeds of my external drives are only 20 Mbit/second.

What a bunch of crock (sorry for venting). I've never heard of an instructional manual that explains why so many factors can cause horrible performance. What's the point in buying into the hype if absolutely none of it is even remotely realistic ... to anyone who knows little or nothing about technical USB standards? And why should the size of a file matter in the first place? Isn't that the whole purpose of hard disk buffers & cache, to provide the ability for constant speed **even if** you're transferring larger (1 GB+ files)?

[COLOR=Navy]Okay, I buy into even more hype ... Oooooohh, eSata, now that's the way to go if you're going with external drives ...[/COLOR]

So I go out and purchase an 8 TB eSata setup (2 x 4 TB) and after formatting to Ext4, **using strictly the eSata port** on the computer with the supplied eSata cable (and no more USB hub), I'm still only getting transfer speeds of about 38 Mbit/second. That's _from one of the older_ external 20 Mbit/second disks to the new eSata ... which actually proves three different things:
1. Those other USB drives are indeed capable to go above 20 Mbit/second for inexplicable reasons.
2. There's no simple logical explanation why the transfer speed is so much less when transferring to other drives.
3. At no point do we ever come remotely close to even max. USB **2.0** speeds while using USB 3.0 ports/disks.

_Even when I'm copying directly_ from one eSata partition to the other, my transfer speed which starts at about 110 Mbit/second gradually drops down to only  71 Mbit/second within 60 - 90 seconds where it then remains. On the other hand, if I elect to move (as opposed to copying) a large amount of files, then the sustainable transfer speed "only" comes down to 82 Mbit/second on the eSata setup.
Okay, much better than before, but still nothing to be dancing a jig about.

The USB or even eSata transfer speed baloney (hype) is exactly that ... baloney. I know dozens of people with computers - none of whom are techies - yet each one an individual who'd go to a store to purchase USB 2.0 or 3.0 or eSata **based on what the signs proclaim,** i.e. very good to excellent transfer speeds, etc. etc. etc. Heck, I'll go as far as to say that I'm willing to bet that 99% of all employees in places such as Bestbuy, Officemax, etc. have no clue how USB or eSata transfer speeds really work, yet the public is permitted to be sold on this nonsense of speeds that can never really be attained for any length of time.

Just for the record though, I've custom built and designed a couple of hundred computers in the past 18 - 20 years and until now I never knew squat about the technical specifications of USB standards. As a matter of fact, **I always attributed dirt slow transfers** to things like flash disks, memory cards, or drives without buffers. But now I know, based on everything that's been said here ... THERE IS NO ... satisfactory answer to this post.

[COLOR=Navy]**So, my personal solution?**[/COLOR] During the weekend I'll be starting with a clean installation of Xubuntu 11.10 or 12.04 plus the Mate desktop (love it), and minus the USB 3.0 hub as well as those two "supposed" USB 3.0 drives. All of my data is going to be managed on my 7200 rpm fast internal drive as well as the 7200 rpm 4 TB partitions. It's not a perfect solution, but it's a lot better than before ...
Thanks for all of the input here. **Have a fantastic Weekend.**

.

---

### Post by Ubun2to on 2012-08-09
> **WinRiddance said:**
> Well, I guess I'm just too ignorant as far as USB speeds are concerned. I'm not a USB techie so when I buy a computer that says mind boggling USB 3.0 transfer speed as well as the appropriate USB 3.0 drives/ports to go with that ... there's really nothing that anyone can say which would make me _**truly**_ _**understand**_ _**why**_ transfer speeds of my external drives are only 20 Mbit/second.

What a bunch of crock (sorry for venting). I've never heard of an instructional manual that explains why so many factors can cause horrible performance. What's the point in buying into the hype if absolutely none of it is even remotely realistic ... to anyone who knows little or nothing about technical USB standards? And why should the size of a file matter in the first place? Isn't that the whole purpose of hard disk buffers & cache, to provide the ability for constant speed **even if** you're transferring larger (1 GB+ files)?

[COLOR=Navy]Okay, I buy into even more hype ... Oooooohh, eSata, now that's the way to go if you're going with external drives ...[/COLOR]

So I go out and purchase an 8 TB eSata setup (2 x 4 TB) and after formatting to Ext4, **using strictly the eSata port** on the computer with the supplied eSata cable (and no more USB hub), I'm still only getting transfer speeds of about 38 Mbit/second. That's _from one of the older_ external 20 Mbit/second disks to the new eSata ... which actually proves three different things:
1. Those other USB drives are indeed capable to go above 20 Mbit/second for inexplicable reasons.
2. There's no simple logical explanation why the transfer speed is so much less when transferring to other drives.
3. At no point do we ever come remotely close to even max. USB **2.0** speeds while using USB 3.0 ports/disks.

_Even when I'm copying directly_ from one eSata partition to the other, my transfer speed which starts at about 110 Mbit/second gradually drops down to only  71 Mbit/second within 60 - 90 seconds where it then remains. On the other hand, if I elect to move (as opposed to copying) a large amount of files, then the sustainable transfer speed "only" comes down to 82 Mbit/second on the eSata setup.
Okay, much better than before, but still nothing to be dancing a jig about.

The USB or even eSata transfer speed baloney (hype) is exactly that ... baloney. I know dozens of people with computers - none of whom are techies - yet each one an individual who'd go to a store to purchase USB 2.0 or 3.0 or eSata **based on what the signs proclaim,** i.e. very good to excellent transfer speeds, etc. etc. etc. Heck, I'll go as far as to say that I'm willing to bet that 99% of all employees in places such as Bestbuy, Officemax, etc. have no clue how USB or eSata transfer speeds really work, yet the public is permitted to be sold on this nonsense of speeds that can never really be attained for any length of time.

Just for the record though, I've custom built and designed a couple of hundred computers in the past 18 - 20 years and until now I never knew squat about the technical specifications of USB standards. As a matter of fact, **I always attributed dirt slow transfers** to things like flash disks, memory cards, or drives without buffers. But now I know, based on everything that's been said here ... THERE IS NO ... satisfactory answer to this post.

[COLOR=Navy]**So, my personal solution?**[/COLOR] During the weekend I'll be starting with a clean installation of Xubuntu 11.10 or 12.04 plus the Mate desktop (love it), and minus the USB 3.0 hub as well as those two "supposed" USB 3.0 drives. All of my data is going to be managed on my 7200 rpm fast internal drive as well as the 7200 rpm 4 TB partitions. It's not a perfect solution, but it's a lot better than before ...
Thanks for all of the input here. **Have a fantastic Weekend.**

.

I have seen USB 3.0 PCI cards-those things can be really fast. Too bad the PCI cards only work with desktops, unless you want to make a custom laptop, which would be ridiculously big with PCI cards.

---

### Post by WinRiddance on 2012-08-10
Yes, I know that PCI cards can be pretty fast but the whole reason why all of us switched to laptops (four computers running 24 x 7 in our family) is because of the electricity consumption. Most good desktop PCs use up between 350 and 550 watts of power while Laptops only use up 65 watts of power (max). So all of our laptops use less power than a single desktop ... and that translates into some real savings all year long ... hundreds of dollars saved.

The **eSata solution** works for me. I live with my file manager, use it every day multiple times. Between my internal 7200 rpm drive and the two 7200 rpm eSata disks, I'm getting speeds of 110 Mbit/second for transfers of 2 - 5 GB in size. Everything larger than that transfers at apx. 80 Mbit/second. That works for me and I never plan on using external USB drives again. Take care.

.

---


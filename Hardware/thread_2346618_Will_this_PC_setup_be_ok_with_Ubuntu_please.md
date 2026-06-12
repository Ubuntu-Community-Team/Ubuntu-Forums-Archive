---
title: "Will this PC setup be ok with Ubuntu please?"
date: 2016-12-16
forum: Hardware
---

### Post by andrew-q2 on 2016-12-16
hi,   I'm going to build an Ubuntu PC, and not knowing much about Ubuntu, I'd be grateful for any comments about the suitability of these components -
i7 6700K
Samsung 256Gb 950 PRO M2 SSD (system will be here)
MSI Z170A "PC Mate" motherboard (I see one of the bios updates addresses some SSD NVME issues)
probably 32Gb memory, maybe 16
some hard disk
no video card - will use the built in graphics.

This will be used for various purposes from everyday browsing to heavy-duty photo processing, but not gaming, and probably no over-clocking.
So two questions if I may please -
Will these parts work together ok?
Will Ubuntu (16.04 LTS) be capable of making full use of these components, e.g. performing powerfully?

Any tips/pointers to help with the setup and installation will be welcome.

Thanks

---

### Post by DuckHook on 2016-12-16
Welcome to the forums, andrew-q2

Please don't duplicate post, as it confuses helpers and dilutes community effort.

What does MSI say about the MOBO? Does it support Linux? If it does, then there is usually a Linux-compatible sticker on the box or as part of their marketing material. This is usually the piece of the puzzle that is most balky. If anything will not work, or work oddly, it will likely be the MOBO.

Another question would be the SSD. Google the manufacturer's specs to see if there are any Linux issues. Probably not, because Samsungs are known to work quite reliably with Linux these days.

I believe the built-in graphics are not actually built in but rather just a conduit to the GPU in your CPU. In other words, you will need an APU if you want to forego an independent video card.

The usual advice when installing Linux on a personal-build machine is to work with a vendor who is willing to refund or exchange components without charge. Components are all tested for compatibility with Windows, but are only spottily tested with Linux. Some OEMs are better than others, but you should always cover your options by allowing for refunds or exchanges.

---

### Post by oldfred on 2016-12-17
Some info:
 MSI Z170A GAMING PRO motherboard
[http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1](http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1)
[http://askubuntu.com/questions/705796/msi-z170a-gaming-m5-with-linux-dual-boot](http://askubuntu.com/questions/705796/msi-z170a-gaming-m5-with-linux-dual-boot) 

I have Gigabyte Z170 with Samsung 850 in a SFF size desktop.

 oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ)

Each brand of motherboard seems to need some settings.

Generally you want to be sure to boot in UEFI mode with gpt partitioning. You should have fast boot off, at least until fully configured. Turn off secure boot. Check if UEFI has setting for video mode. You may need settings for USB ports on and/or UEFI boot from USB.

---

### Post by mörgæs on 2016-12-17
To save yourself trouble use the latest software, that is at least 16.10 and maybe 17.04 a month or so before release.

---

### Post by gordintoronto on 2016-12-17
Nice configuration, but overkill for your applications.

If you install 32 GB of memory, I guarantee that 16 GB will never be used. If you used an i5-6500, you would not notice the performance difference. Use the saved money to buy two or three big external hard drives for backup!

Oh, and start with a WD Black hard drive.

Try 16.04, but if it gives you any grief, go to 17.04, which means you will need to upgrade twice to get to the 18.04 LTS.

If you are going to use Wi-Fi, that is the component which is most likely to cause grief. Check it out before you buy something which won't work.

---

### Post by andrew-q2 on 2016-12-20
Thanks folks for the comments, which look very helpful.  Perhaps this won't be quite as straightforward as I thought!  The mention of UEFI is worrying! though I see the thread is marked as Solved so hopefully this aspect will be ok when I get into this for real.
I'll think about an i5.  Apart from the performance comment, the cost is also mounting now I'm looking at it all more thoroughly (I thought I could re-use a power supply, but the main connector config has moved on).
I'm told some of the photo apps use masses of memory.
If I don't overclock, will an air cooler be ok, rather than some fancy water-cooled system please?
Andrew

---

### Post by oldfred on 2016-12-20
You should only set to Solved it it is resolved.

You should not need water cooling if not overclocking. I have never overclocked, but do not play games.

Do not attempt to reuse any old components. I tried to re-use a somewhat newer power supply on my other build. My Asus Z97 had all sorts of LED and they gave nothing but errors. I ended up taking it to MicroCenter and for a few bucks they plugged it in on their test bench & it just worked. Sold me a nice new power supply.

My SFF system was a bit more expensive because I had to have smaller case which led to special power supply. I got all the parts from Amazon even though a couple were just a few bucks more per the pcpartpicker site. And then my wife complained as I had boxes all over dining room table and she was worried that it would take days like my Asus system. But the SFF one went together in about 3 hr and I had Ubuntu installed & mostly configured in another hour.

---


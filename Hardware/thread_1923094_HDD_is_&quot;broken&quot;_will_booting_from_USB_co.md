---
title: "HDD is &quot;broken&quot; will booting from USB continuously work?"
date: 2012-02-09
forum: Hardware
---

### Post by Kife1100 on 2012-02-09
Well I plan on fixing my parents laptop in the long run, hopefully in about 6 months we can either replace it or replace the HDD. Most likely replacing the laptop in general.

I have ran scans in the BIOS and the HDD can't be read, Windows on it moves impossibly slow even after I reformat it.

My plan is I told my mom to buy a 16gb flash drive so I can put another Operating System on it that won't be like Windows but it will be easy enough to use for things that they use computers for YT, Email, Looking up recipes, and Skype.

I am assuming because the laptop will be running directly from the USB at all times that there will be no issue. I may even disable the HDD in the BIOS.

Now I am not even sure if this will work and if it does, should I tell her to buy an 4gb thumb drive and a 16gb thumb drive. One to put Ubuntu on while the other can store programs?

Thanks a lot!

---

### Post by ahallubuntu on 2012-02-09
You can sure use a USB stick with Ubuntu to run the laptop without having the hard drive even installed, if you wish.

But if the hard drive is the problem, why not simply replace it?

Have you systematically tested the drive to confirm it is the problem?  Do so.  I suggest Parted Magic, which you can burn to a CD and boot on the laptop - it includes the Smartctl package ("SmartControl") that will let you access the drive's S.M.A.R.T. status and run tests on it.

Replacing a laptop hard drive isn't that hard in many cases.

Until a few months ago it also may have been cheap, but floods in Thailand that closed some hard drive factories there have temporarily reduced the supply of hard drives and raised the price.  That may make replacing the drive less worth the money, depending on how old the laptop is.  If it uses an old PATA/IDE type of laptop drive, it's probably too old to be worth it.  Look on NewEgg to see what current hard drive prices are, though.

---

### Post by xyzzyman on 2012-02-10
If she has an SD slot on her notebook, I'd recommend getting a 16GB SD card so she can just leave it in there and not have the USB drive sticking out. Weather you go USB or SD, you can install Ubuntu to it instead of doing it as a live cd. You should be good with just one 16GB. I gave 30GB for my Windows 7 partition that I rarely use, and just installing basic programs for a suitable system like Office, 7zip, etc and I went over 20GB in no time. With everything I have on Ubuntu I am under 5GB. 

And if that's all she does, go with Lubuntu 11.10 as it's a bit leaner so less chance of it using swap. As you can see from the screenshots: [http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Lubuntu%2011.10](http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Lubuntu%2011.10) it has a similar 'start' menu to Windows and you can put firefox and chrome icons on the desktop.

I've used Ubuntu on SD cards in media center PC's instead of HDD's on a number of occasions. Much cheaper than a HDD, and better on power.

---

### Post by Bucky Ball on 2012-02-10
All will be fine, BUT, and this is a big but, Ubuntu and its apps can use up to 16Gb after awhile so if you intend on saving data, what happens when you run out of space on the USB (or SD)? You don't have a hard drive to save anything to and only 16Gb on the stick. 

I suggest just replace the hard drive (as mentioned). That is no big deal (easy to do, esp. in a laptop). Or think about 32 - 64Gb stick/sd so you have room to store data.

---

### Post by xyzzyman on 2012-02-10
I think OP knows how to reinstall the HDD, and it's more of a cost issue, hence why 6 months out they'll decide which route to take. Unless his mom is saving 8GB's of recipes I wouldn't worry. Only OP knows his mom usage though. I'm amazed at how many family members over the years think their hard drive is probably full and you look and they have 500megs of pictures and that's it. lol

---

### Post by C.S.Cameron on 2012-02-10
Ubuntu running off USB2 is slower than running off of SATA.

A full install to flash drive takes up ~4.5 GB minimum.

A persistent install takes up ~0.75 GB + persistence.
Persistence is limited by FAT32 to 4GB casper-rw file and 4GB home-rw file unless you use persistent partitions.

---

### Post by xyzzyman on 2012-02-11
I can't believe I forgot about this:

[http://www.jolicloud.com/jolios](http://www.jolicloud.com/jolios)

Runs very nice off an SD card and does everything you listed including Skype. It's based off Ubuntu also. :) I used to run it on a netbook because it booted so quickly off the SD card and by not using the HDD I got even more time off my battery when I was out and about. It's probably the easiest thing they can use but still be functional.

---

### Post by Jay Car on 2012-02-11
I occasionally pick up cheap laptops at second-hand shops or yard sales, most have had their internal drives removed. Many older ones only have two USB ports, so I keep a variety of Live CDs handy.  

The majority of those old laptops worked great just using the Live CD and plugging in an 8GB thumb drive for storage, and a USB mouse, until I could get new drives for them.  

One old Dell needed a hard drive that was difficult to find, so it ran for several months with just the CD and the 8GB USB. It actually did quite well.

I know, this isn't necessarily the most helpful comment, mostly it's meant to make the case for using a Live CD to run the system, thus freeing-up the few USB ports for file storage.  A couple of 8GB drives can hold a LOT of recipes.

---


---
title: "Major Systems Failure"
date: 2015-11-03
forum: Hardware
---

### Post by courseinmiracles2 on 2015-11-03
After losing my webcam, I ran into some weird system crashes/freezing the last of which was loss of my keyboard. After ANOTHER reboot I am here typing again. 
Any good commands for checking my system? Most of this happened after the upgrade to 15.04, could be a possible conflict somewhere, maybe.

This toshiba is a satellite L650 and is about 6 or so years old I think, it's hard to pin it down. I've never had a windows machine last this long, so maybe it's just old age???

Any thoughts

---

### Post by tgalati4 on 2015-11-03
Pull it apart, clean it, reseat all the cables, check the voltage on the power brick.  Get a new battery.

---

### Post by sammiev on 2015-11-03
I have the same laptop and had no issues at all with 15.04.

Try running 15.04 live from a USB stick and see if the problem persist.

---

### Post by SeijiSensei on 2015-11-03
Do you have an external USB keyboard lying around?  If the laptop's keyboard acts up again, see if the external keyboard works.  Then you'll know it's likely a hardware problem on the laptop.

---

### Post by weatherman2 on 2015-11-03
Older laptops tend to get dirty - I agree.  Specifically, the CPU heat sink and fan area can get clogged so the CPU overheats and causes issues.  I have seen this problem numerous times on older laptops.  Often it's a chore to take apart a laptop just to get to the fan and heat sink - many screws and tabs, and it can be a frustrating process.  Sometimes you break things.  Do  a web search for your model laptop and see if there is a "disassembly guide" for your model - maybe even a video showing you exactly how to do it.  Or you may find a service manual with step-by-step instructions to show you exactly how to remove the heat sink (you don't have to remove it - just get to the point where you can remove it, so you can clean the dust/dirt out).  You may want to remove the fan, though.  You will probably need a tiny jeweler's screwdriver for that.

Beyond that, you could also have a problem with your hard drive or your RAM.  You can boot Ubuntu to run a Memtest and let it run for a few hours.  If you have any errors, replace your RAM.  You can test the hard drive using GSmartControl (aka smartmontools).  You can install GSmartControl in a Ubuntu live boot session but you may have to enable the "universe" repository first.

---

### Post by courseinmiracles2 on 2015-11-03
Thanks for all the feedback. Appreciate it.
It has recently ( last couple of months) had a new battery. I did see a video of how to take it apart as I have been thinking about giving it a clean, so that will be next. After that I will give an update.

Shortly after I wrote the last post the browser grey the fan came on and the whole thing froze. I left it for about fifteen minutes and it un-froze...

Thanks again for the feedback. I'll let you know.

---

### Post by Bucky Ball on 2015-11-03
Have you done a full update/upgrade since the upgrade to 15.04? 

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Then reboot. Sometimes fixes things after an upgrade to a newer release. You need to be online to do this effectively, or at all, naturally. :)

The upgrade to 15.04 was a clean install or upgrade from 14.10? If a clean install, you might like to try 15.10 as 15.04 reaches end of life in January anyhow. If a net upgrade, check your software sources and make sure there are no 14.10 repos still enabled.

---

### Post by mörgæs on 2015-11-04
> **tgalati4 said:**
> Pull it apart, clean it, reseat all the cables, check the voltage on the power brick.  Get a new battery.

Please don't jump to conclusions.

While your instructions might be necessary in the end (we don't know that yet) they are overly complicated for the average user. It would be more helpful to begin with an easier approach, for example a live boot as indicated in post #3.

---

### Post by Mike_Walsh on 2015-11-04
> **weatherman2 said:**
> Older laptops tend to get dirty - I agree.  Specifically, the CPU heat sink and fan area can get clogged so the CPU overheats and causes issues.  I have seen this problem numerous times on older laptops.  Often it's a chore to take apart a laptop just to get to the fan and heat sink - many screws and tabs, and it can be a frustrating process.  Sometimes you break things.  Do  a web search for your model laptop and see if there is a "disassembly guide" for your model - maybe even a video showing you exactly how to do it.  Or you may find a service manual with step-by-step instructions to show you exactly how to remove the heat sink (you don't have to remove it - just get to the point where you can remove it, so you can clean the dust/dirt out).  You may want to remove the fan, though.  You will probably need a tiny jeweler's screwdriver for that.

^^^^ +1.

Very sound advice. I run a 13-yr-old Dell Inspiron laptop; an original 1100. Admittedly, it hasn't had that much use over the years, but during that time it's been stripped down and thoroughly cleaned out on at least half-a-dozen occasions. The older laptops were quite a bit 'bulkier'; this tends to make the cleaning process somewhat easier.....lots more room to play with! It's astonishing the amount of dust that gets in there.....and the places in which it will collect. And the problem is almost always made worse by the fact that, to my knowledge at least, no manufacturer has ever seen fit to include something as simple as a light foam filter over the intakes.

It does make the process easier if you have a disassembly guide available. In my case, Dell provided a complete one at the rear of the very extensive owner's manual. Yes; things may well break while you're at it.....

All this is necessary on a model which was well-known for being saddled with Dell's famous lousy 'thermal solution'. I do believe it's helped to greatly extend the Dell's lifetime.

> **tgalati4 said:**
> Pull it apart, clean it, reseat all the cables,  check the voltage on the power brick.  Get a new battery.

Your computer's no different to your car. You wouldn't expect that to run faultlessly for 6 years without the odd service along the way, would you? A laptop has different requirements, certainly.....but it still needs a certain amount of TLC. And it will thank you for it, by performing in the manner in which you would want it to, running cooler, and lasting longer, too.

> **mörgæs said:**
> Please don't jump to conclusions.

While your instructions might be necessary in the end (we don't know that yet) they are overly complicated for the average user. It would be more helpful to begin with an easier approach, for example a live boot as indicated in post #3.

I'll agree; up to a point. I agree that the simplest solutions are best tried first.....but on a machine of this age, the possibility of a strip-down being required does, I feel, need to be at least mentioned.

Here's to the next 13 yrs..... :lol:


Regards,

Mike. ;)

---

### Post by weatherman2 on 2015-11-04
> **Mike_Walsh said:**
> ^^^^ +1.

Very sound advice. I run a 13-yr-old Dell Inspiron laptop; an original 1100. Admittedly, it hasn't had that much use over the years, but during that time it's been stripped down and thoroughly cleaned out on at least half-a-dozen occasions. The older laptops were quite a bit 'bulkier'; this tends to make the cleaning process somewhat easier.....lots more room to play with! It's astonishing the amount of dust that gets in there.....and the places in which it will collect. And the problem is almost always made worse by the fact that, to my knowledge at least, no manufacturer has ever seen fit to include something as simple as a light foam filter over the intakes.

Yeah, I've worked on a couple of those 1100's and had a few of them at one time. The good news is, it is extremely easy to get to the CPU to clean the heat sink and fan.  All you do is remove the keyboard then a few screws.  I could probably do it with my eyes closed now.  (On many other models, you have to take the bottom completely off, then the palmrest, etc. - a much harder job.)  The bad news is, that heat sink design in the 1100 seems to be a dust magnet.  So cleaning it out every so often is rather important.

The first 1100 I worked on was a donation from a friend.  His wife got tired of using it because it was so slow.  Yes, it's an old machine and was even a few years ago, but it was slower than it should have been.  The reason, it turned out, was that the heat sink was so clogged with dust that instead of shutting down due the heat, the P4 CPU was throttling down, making it even slower!  Once I cleaned it out, the fan became quiet and of  course much faster.  The P4 was kind of a lousy CPU, but it was designed, out of necessity, to operate very hot, even if throttled.

Unfortunately, I had a lot of trouble getting Ubuntu to work reliably on the 1100.   Today, I still have one left after a friend gave it back to me after upgrading - technically usable but not really worth using so gathering dust.  If I found someone who had absolutely no computer at all I would donate it - better than nothing.

I put a P4 2.8GHZ CPU in that one - it did make it a little faster.  But it will take only a 400MHZ FSB CPU, not a 533MHZ, so you have to get a specific P4 for it.  (And must be socket 478 also.)  But you can find them on eBay.  Easy to replace if you have some thermal paste for the new CPU.

---

### Post by Mike_Walsh on 2015-11-04
Hi, weatherman2.

Nice to come across somebody else who's been 'playing around' with the 1100s. I was beginning to think I was somewhat unique in that respect..!

Oh, to be sure, they'll never be able to run at any great speed, or with any real measure of dexterity as far as modern software is concerned. It's basically 15-yr old tech we're talking about. But the great thing about it is, it **still** runs.....and is quite reliable, when all's said and done.

Mine started with a 2.2 GHz Celeron (slow, but a good old piece of kit), 128 MB of RAM, and a 20 GB Hitachi Travelstar. The Celeron's been uprated to a 2.6 GHz P4; yes, I could have gone for the 2.8 , but for one thing, I couldn't find one when I wanted to do the upgrade.....and for another, I was trying to keep the TDP as similar as possible; the 1100's 'thermal solution' is as lousy as I stated! I wouldn't have minded a 3 GHz P4, with the 400 MHz FSB on the 478 socket; but they're rarer than hen's teeth.....Intel only made a very limited run of them, as they were more interested at that time in developing the then-new HT technology (and **those** were all on the 800 MHz FSB, of course).

[http://www.cpu-world.com/CPUs/Pentium_4/Intel-Pentium%204%203%20GHz%20-%20RK80532PC080512.html](http://www.cpu-world.com/CPUs/Pentium_4/Intel-Pentium%204%203%20GHz%20-%20RK80532PC080512.html)

CPU-World (run by a Russian national by the name of Gennady Shivets) do list it, but many tech sites will tell you, straight to your face, that it doesn't in fact exist.....

[ATTACH=CONFIG]265366[/ATTACH]

Well, there's the proof. CPU-World don't list the TDP, but I **have** discovered that it's somewhere in the region of nearly 80W.....which I reckon would be pushing that wretched heat-sink's capabilities beyond its capacity to cope..!

I'm **quite** sure you know where I'm coming from. We've got one guy on the 'Puppy' forums who also runs an 1100; he's in his late 60's, and candidly admits that the output from the exhaust vent works wonders for the rheumatism in his knees..... :lol:

---------------------------------------------------------------------------------------------------

As for the rest of it, I maxed the RAM to its 1 GB limit; and the Hitachi Travelstar has very recently (like less than a fortnight ago) been upgraded for a 32 GB [Transcend PATA SSD]("http://www.transcend-info.com/Products/No-418"). It's made a **real **difference running Xubuntu with this..! When I first tried replacing the very creaky Win XP with Linux last year, I couldn't get any of the 'buntus to give a proper display at all; all I got was a 640x480 window jammed into the top corner of the screen. They would all install, but weren't really usable.

I tried Lubuntu 14.04.2  earlier this year, and got a proper display straight off. Yay!! Subsequently, I then tried Xubuntu 14.04.2, 'cos I've always liked the XFCE desktop. Had to employ a workaround from here:-

[http://ubuntuforums.org/showthread.php?t=2222014&page=2&p=13016601&viewfull=1#post13016601](http://ubuntuforums.org/showthread.php?t=2222014&page=2&p=13016601&viewfull=1#post13016601)

...which worked nicely. You can read about my escapades with these in morgaes' 'Old hardware brought back to life' sticky in the 'General Help' forum.

In the meantime, I've been getting very much into Puppy Linux (brilliant little distro for elderly hardware, which works amazingly well on the Dell). Tahrpup 6.03 went onto the SSD, along with Xubuntu 14.04.3.....and this time, I didn't even need to employ the graphics 'workaround'. So I'm very pleased to now have a fully-functional dual-boot, with the two OS's I like the most (and booted by Puppy's Grub4DOS, which is superbly easy to set up). Network connection is taken care of with a TP-Link WN725N (v.2) USB 'nano' wi-fi adapter.....which auto-connects in Xubuntu, every time. (Only the 1100's 'big brother', the 5100, came with wi-fi as standard.)

[http://uk.tp-link.com/products/details/cat-11_TL-WN725N.html](http://uk.tp-link.com/products/details/cat-11_TL-WN725N.html)

Yes, the P4 is definitely the bottle-neck.....but I'm quite happy with the Dell as she now stands. Just goes to show that careful, patient upgrading can keep even old 'bricks' like the Dell (that battery pack alone weighs more than a MacBook 'Air'..!) viable as a basic computing solution. But then, I'm funny that way; I **like** messing about with elderly tech.......most people can't **give** it away fast enough, and parts for them are as cheap as chips, if you know where to look. Like all of £6.20p for the P4 on eBay!

(I escaped the famous 'exploding battery pack' episode.....which led to that long-running class-action lawsuit against Dell.) Mine's been replaced with a high-capacity, 7800 mAH version, anyway.....


Regards,

Mike. ;)

---

### Post by courseinmiracles2 on 2015-11-07
Hey Fellas, Just a quick up date... After 3 videos, I stripped it     down to expose the fan and gave it a good clean ( fan now very     quite) I didn't take out the mother board as I thought I was     skateing on pretty thin ice as it was. i.e. putting in back     together. As it was I had some problems reconnecting some of the     tabs.
    
    I did get my webcam back \\:D/ 
    
    I also installed GSmartControl and ran it without any errors.
    
    I definitely feels better and so far is running nicely. I also did an     update and a dist-upgrade.

So thanks again for the advice. I'm going to call this solved.

---

### Post by Bucky Ball on 2015-11-07
Great news. I might do a backup and try a clean myself. See the first link in my signature to mark thread solved. Enjoy. :)

---

### Post by tgalati4 on 2015-11-07
The next time it acts up, strip it down completely, touch up the solder points and replace any suspect capacitors.  Yes, this is advanced repair, but older machines do need maintenance.  Reliable hardware will give you decent Linux uptime.

---


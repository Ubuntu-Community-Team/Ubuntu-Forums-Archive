---
title: "Clausoft Meenee Ubuntu laptop"
date: 2011-08-17
forum: Hardware
---

### Post by SirPecanGum on 2011-08-17
Anyone have experience with this laptop? 

[http://www.amazon.co.uk/gp/product/B004GGBUJY/ref=ox_sc_act_title_2?ie=UTF8&m=A97SL4X5I9WBB](http://www.amazon.co.uk/gp/product/B004GGBUJY/ref=ox_sc_act_title_2?ie=UTF8&m=A97SL4X5I9WBB)

---

### Post by candtalan on 2011-08-22
Yes, we have one, it is pretty nice

[http://ubuntuforums.org/showthread.php?p=10980805#post10980805](http://ubuntuforums.org/showthread.php?p=10980805#post10980805)

[http://amzn.to/rcz3SN](http://amzn.to/rcz3SN)

Enjoy!

---

### Post by PDiddlyDoodlyDo on 2011-10-09
I bought one of these second hand from Amazon for £200 on Friday. Here are my first impressions:

1. It looks great - minimalist styling, with no annoying flashing lights etc.

2. It has a low profile and feels light. I could happily carry this around all day

3. It's not flimsy, but it's not like a MacBook air. I'm going to buy a protective case for it. For walking around my home (watching TV, cooking, browsing before bed etc.), it's perfect.

4. The screen is a good size and clear. Obviously, a higher resolution would be nice, but at this price, the only fair comparison is a netbook... And it's better than that. Also, it doesn't suffer glare, because it has a matt texture.

5. The two biggest drawbacks are the battery life and the processing power. I charged it from 'new' for > 24hrs; and running windows it lasted 2hrs 20mins; running Ubuntu it has lasted slightly longer c. 2hrs 30mins.

6. The processor is just slightly slower than I would like, starting firefox takes 5 or so seconds. It might have been chosen because the battery isn't great, but a dual-core (e.g. the Tegra 2 in the Transformer) would have been a better choice I think.

7. I've installed Ubuntu 11.04 as a dual boot with a shared partition, and it works out of the box so far - wireless, keyboard, mouse, etc. I still haven't tried the webcam in Ubuntu.

8. The hard drive is bigger than stated at 400GB. Personally, I would have preferred a much smaller SSD hard drive; and relied on my NAS for the serious storage.

Overall, I'm very, very pleased with this laptop - it's a wake-up call for the major manufacturers, who seem to have missed this market for a cheap laptop that will do the non-gamer, simple everyday things well. Whenever I need serious power at home, I just remote desktop my tower, but for everything else (email, iplayer, word processing, web development) I just use this.

---

### Post by richselby on 2011-12-26
Just to warn people of a serious headaches I'm having with this system. 

Trivial stuff first: If you're using it out of the box, the sudo password is meenee. As is the default user.

If you want to boot from a USB drive, you need to press F11 (that's Fn key + F9) to get a BIOS boot menu, otherwise you can't boot from the USB.

Now here's the scary bit: it came installed with Ubuntu 10.10, but this is now Dec 2011. So I wanted to move to Ubuntu 11.10. Not having any data on it yet, I thought the easiest thing to do would be to wipe the drive and start over with a new system. So I put the new Ubuntu 11.10 on a USB and made it bootable. Then I booted, and selected the erase and install option.

I've never had problems doing this on other machines. But it failed very quickly with the following error:

The ext4 file system creation in partion 1 of SCSI(0,0,0)(sda) failed.
 
I've tried to manually create an Ext4 (and failing that an Ext3) partition using gparted running from the USB key, but that fails too. 

So I have an attractive new laptop with a disk that won't take a file system. Of course the old 10.10 system it came with is hosed. So if anyone has any ideas around this, I'd love to hear them.

---

### Post by candtalan on 2011-12-28
> **richselby said:**
> Just to warn people of a serious headaches I'm having with this system. 

Trivial stuff first: If you're using it out of the box, the sudo password is meenee. As is the default user.

If you want to boot from a USB drive, you need to press F11 (that's Fn key + F9) to get a BIOS boot menu, otherwise you can't boot from the USB.

OK, that would seem pretty normal to me. Lots of machines use a function key to get a boot  media choice.
> 
Now here's the scary bit: it came installed with Ubuntu 10.10, but this is now Dec 2011. So I wanted to move to Ubuntu 11.10. Not having any data on it yet, I thought the easiest thing to do would be to wipe the drive and start over with a new system. So I put the new Ubuntu 11.10 on a USB and made it bootable. Then I booted, and selected the erase and install option.

I've never had problems doing this on other machines. But it failed very quickly with the following error:

The ext4 file system creation in partion 1 of SCSI(0,0,0)(sda) failed.
 
I've tried to manually create an Ext4 (and failing that an Ext3) partition using gparted running from the USB key, but that fails too. 

So I have an attractive new laptop with a disk that won't take a file system. Of course the old 10.10 system it came with is hosed. So if anyone has any ideas around this, I'd love to hear them.

I completely reinstalled 10.10 soon after I received mine, and I had no problems. I have very  recently also installed Ubuntu 11.10 to dual boot with the 10.10, again no problems.

Have you checked the hard drive? If you can boot into a alive session then with the Ubuntu CD you can at least use disc utility to check the hard drive? There are other tools of course.

It might be worth checking that your bootable usb checks itself as having correct content. Also maybe try another bootable media with a different method of creating it. In principle also it will be possible to use a live CD in an external usb CD/DVD drive if such a drive is available.

You also have two usb slsots, do they both give the same results?

For the record, I have had no problems with this machine at all. Apart from  - if you could call it a 'problem' -  when people marvel at it and ask 'Who makes it?' I answer 
'Meenee'
their face gets suddenly pale, and they change the subject.... Sad state of our retail indoctrination I think. Lovely machine. I hope you can get it sorted. If I can help, I will.

hth

---

### Post by richselby on 2011-12-28
Thanks for your interest, cantalan. I didn't expect anyone else to notice, except perhaps a potential buyer Googling around. And yes, this is meant as a warning saying beware of completely wiping and reinstalling on the Meenee. It might not go to plan. You are better off with sticking with the existing disk partition layout at least.

I can boot into the live system from either USB drive no problem. The trouble is laying  a filesystem down on the 320GB hard drive at all. Before fsck runs, it needs to have a filesystem to check. And the mkfs.ext4 command fails. As does mkfs.ext3 and even mkdosfs (FAT32) command. 

This evening when I tried to instal Ubuntu 11.10 I get a different error: Ubi-partman failed with exit code 10.

I tried the Ubuntu Disk Utility (from the live OS), and the first self-test failed with a read error, although this might be a consequence of not having a filesystem down there.

One more straw to clutch at: I recall when I first attempted to install Ubuntu 11.10, it flashed up what the pre-installed partitions were when it was asking whether I was sure I wanted to start over. They seemed pretty weird to me, including some non-allocated space and a small FAT32 partition, but I wasn't looking too closely. 

I wonder, could you have a look at the partitions set up on the disk and let me know what's there. I might be able to emulate it manually. Gparted should report what's there.

---

### Post by candtalan on 2011-12-29
> **richselby said:**
> Thanks for your interest, cantalan. I didn't expect anyone else to notice, except perhaps a potential buyer Googling around. And yes, this is meant as a warning saying beware of completely wiping and reinstalling on the Meenee. It might not go to plan. You are better off with sticking with the existing disk partition layout at least.
I think your warning is premature. There seemed to be quite a number of meenees sold including with windows and I have not seen any sign of strange problems.
> 
I can boot into the live system from either USB drive no problem 
good, that means your machine is basically ok and working - mainboard, usb, video  etc and display.

>  The trouble is laying  a filesystem down on the 320GB hard drive at all. Before fsck runs, it needs to have a filesystem to check. And the mkfs.ext4 command fails. As does mkfs.ext3 and even mkdosfs (FAT32) command. 

The drive needs to work as a hard drive first, before writing a filesystem.
I attach screenshots of my current meenee (using it  to send this now). As I mentioned, one of the first things I did was to wipe and start afresh with again - ubuntu 10.10. I had no problems when that was done, the drive partitioned ok and formatted etc as expected. It is an ordinary (rotating) hard drive after all. Recently I needed to install ubuntu 11.10 and I did this in a hurry, so I used the installer facilites of choosing 'install alongside' which is why there are now two swap partitions and not just one - which would have the situation if I had done my usual thing of using the manual (advanced) allocation of partitions. However, you see there is a normal partition arrangement, with nothing unusual.

the second screenshot is of the disk utility. I only rarely use actual disk test, I usually first look at the SMART data held by the hard drive itself, it is fairly clever, and it keeps records. In my case I would NEVER expect to see any red entries, and no errors whatsoever. Even if the self repair is doing stuff to keep the drive working, I would regard any errors at all as a serious warning of possible future fail.

> 
This evening when I tried to instal Ubuntu 11.10 I get a different error: Ubi-partman failed with exit code 10.

I tried the Ubuntu Disk Utility (from the live OS), and the first self-test failed with a read error


from what you are seeing I am sorry to think that it is a consequence of disk failure. a disk surface test ignores any filesystem, it may even be a normal requirement to have no filesystem, it depends on the test. manufactureres of hard drives do have various tools which can be downloaded and used also.

one thing I have sometimes found useful in emergency is to make a small partition (10GB) or several such, and with a chance that one of them will have few enough disk errors to work (and stay working??) then do the install in that one only. Although this is a bit desperate, it also depends on the errors not increasing (like if the drive has decided to start seriously failing.....)

hth, keep in touch?

---

### Post by richselby on 2012-01-02
Thanks again, much appreciated for your advice. I looked at the SMART data, re-ran the tests and got a red warning straight away. So I am blaming a disk defect. It's a good idea about making several wee partitions, but a lot of work. So I decided, reluctantly, to return the machine to Amazon and request a refund.

Maybe I got the runt of the litter?

---

### Post by sacridex on 2012-03-08
Hello,

The Meenee got an upgrade. It now has an Atom N570.
I think im gonna buy one. Can anyone review the new model?
And is it easily possible to replace the disk(with a ssd)?

---

### Post by matthewfelgate on 2012-06-12
Did you buy one?  Did it work well with an SSD?
(I am thinking of doing the same thing)

---

### Post by discarded on 2012-08-20
> **matthewfelgate said:**
> Did you buy one?  Did it work well with an SSD?
(I am thinking of doing the same thing)

Did *you* buy one? ;) I'm thinking of doing the same thing. And btw, is its wireless card compatible with bactrack 5??

---

### Post by candtalan on 2012-08-22
> **discarded said:**
> And btw, is its wireless card compatible with bactrack 5??

yes I have just tried backtrack 5R3 live session on a usb and it can connect ok - have just signed on into a wpa2 access point.

BTW boot choice of media on the meenee is F11 (Fn F9)

---

### Post by candtalan on 2012-08-28
> **candtalan said:**
> Yes, we have one, it is pretty nice
[http://ubuntuforums.org/showthread.php?p=10980805#post10980805](http://ubuntuforums.org/showthread.php?p=10980805#post10980805)
[http://amzn.to/rcz3SN](http://amzn.to/rcz3SN)
Enjoy!

More information: HDMI 
Ubuntu 11.10 installed, and also tried 12.04.01 live session.
For the first time I tried to use the hdmi mini connector, with a mini to standard adaptor, and a hdmi cable, and used our widescreen hd ready TV a 
Panasonic TX-L32S10B
and  unfortunately the external display did  not work. The external display was recognised 16:9 and an error message appeared relating to a resolution not being possible for  3D. I also logged in to 2D (ubuntu 11.10) with no success for external display.

I was trying this for a friend, who would have needed an external display.

Any other experiences out there please?

---

### Post by candtalan on 2012-09-08
> **candtalan said:**
> More information: HDMI 
Ubuntu 11.10 installed, and also tried 12.04.01 live session.
For the first time I tried to use the hdmi mini connector, with a mini to standard adaptor, and a hdmi cable, and used our widescreen hd ready TV a 
Panasonic TX-L32S10B
and  unfortunately the external display did  not work. The external display was recognised 16:9 and an error message appeared relating to a resolution not being possible for  3D. I also logged in to 2D (ubuntu 11.10) with no success for external display.

I was trying this for a friend, who would have needed an external display.

Any other experiences out there please?

Ah! Heads up!
The output for external display is offered on a mini HDMI format socket, however, it looks to me as if it is in fact, still VGA (but wired through an alien connector). I had not realised that the facility *requires* a special cable adapter from Clausoft (aproximately 10 uk pounds). This adapter is cheap enough to suggest that a true conversion from hdmi to vga is not actually taking place, and the adapter looks to me like the connector ends are perfectly standard items, with no extra conversion chips inside.

The special adapter cable is a short cable, mini HDMI connector to VGA connector.
I have tried it, it works ok as normal vga, for example to my wide screen television set.

---

### Post by zendob on 2012-10-10
I have installed ubuntu 12.04 onto my daughters meenee, and it is working well. Had some issues with the 10.10 it came installed with, just niggly things like backspace key sticking and sound not working properly, but they seem to be fixed by the upgrade. Just had cover replaced as hinge got broken, they were very helpful. I am keen to hear if somebody has replaced the hard drive with an SSD though, I imagine it would help battery life, general speed etc. as long as it works...

---

### Post by ninorc on 2013-01-22
Hello, fellow meenee users. 
[LEFT]I got one of these a few weeks ago for £175 off eBay!
In general, I love it. Nothing about it is 'premium', but  it's like a thousand pounds cheaper than a Macbook. 
However,  its trackpad is extremely irritating and so sensitive/erratic it  makes  typing tedious. I'm wondering if using an external mouse  - meenee sell  a Bluetooth mouse for a tenner - will automatically disable the  trackpad and make my life easier?   

[/LEFT]

---

### Post by candtalan on 2013-01-22
> **ninorc said:**
> Hello, fellow meenee users. 
[LEFT]I got one of these a few weeks ago for £175 off eBay!
In general, I love it. Nothing about it is 'premium', but  it's like a thousand pounds cheaper than a Macbook. 
However,  its trackpad is extremely irritating and so sensitive/erratic it  makes  typing tedious. I'm wondering if using an external mouse  - meenee sell  a Bluetooth mouse for a tenner - will automatically disable the  trackpad and make my life easier?   
[/LEFT]
Hi, Note that the trackpad can/should be disabled by you, if you say intend to do typing Fn F2 keys (or use the mouse). It is not automatic in my unit.

In fact it was a long time before I noticed these keys, and IIRC I thought then as you do, too sensitive or something, any way I immediately reinstalled Ubuntu thinking a software problem. It is running 12.04 now, seems ok, sensitivity setting is low value, is ok. The other thing with touchpads, for me, is the 'tapping' being used as mouse clicks (I do not see an option for this in settings on this machine). (I usually want to turn tapping off). I have the early version, it reports as two CPU 1.66GHz x2 with atom N455 cpu. Later model I think is faster.
Enjoy!

---

### Post by ninorc on 2013-01-22
> **candtalan said:**
> Hi, Note that the trackpad can/should be disabled by you, if you say intend to do typing Fn F2 keys (or use the mouse). It is not automatic in my unit.

Ah ha! Thank you very much:-)

---

### Post by sam26 on 2013-10-01
Hello from  a new User. I am a PGCE student and am thinking of buying a Meenee (with Ubuntu installed) so that I can use open office (Libreoffice) as presentations  are really important. Reading back I see some issues with installing Ubuntu 11mand although I have Ubuntu on my falling apart laptop, I am not the best at resolving computer issues. Also I would like to know how many USB ports there are and if I can connect (and get a cable) so that I can connect to another screen?  (thanks)

---

### Post by candtalan on 2013-10-02
> **sam26 said:**
> Hello from  a new User. I am a PGCE student and am thinking of buying a Meenee (with Ubuntu installed) so that I can use open office (Libreoffice) as presentations  are really important. Reading back I see some issues with installing Ubuntu 11mand although I have Ubuntu on my falling apart laptop, I am not the best at resolving computer issues. Also I would like to know how many USB ports there are and if I can connect (and get a cable) so that I can connect to another screen?  (thanks)
The version of meenie I have is one of the first ones. Later models were a bit faster. As you see I think from my detailed earlier post/link, it is ok but not fast at all. Also the battery is not at all big. But I like it, it is a nice  machine. USB is I think only one slot each side (left, right) external display: the connector which looks to be a mini HDMI format is a mini hdmi connector ok, BUT it does not output hdmi (!) it outputs vga. My guess is that the thin sleek case was just too small for a chunky  traditional vga connector.  It needs a special custom adapter cable - which is wired custom - with an apparent mini hdmi one end and a conventional vga the other end (buy from meenee). However, it works well. My (early) machine struggles with replay of full screen video.

hth

---

### Post by sam26 on 2013-10-02
Thanks for that. Looks like it will do what I need then. I just have to install Ubuntu 12. (I hope that goes smoothly)

---

### Post by candtalan on 2013-10-03
It should go ok. I am using 12.04 LTS, (and I think I tried 13.04 also)

---

### Post by ninorc on 2013-10-22
Upthread, you'll see that I was initially enthusiastic about my meenee, purchased in January for £175. It's styled like a MacBook but is a grand cheaper! There's a chunk missing from the middle of the thread, from around June this year (poss, because of the forum take-down?) in which I praised a positive Customer Service experience when a hinge started breaking and they fixed it under warranty. But now the other hinge is broken, barely four months on.It is because the machine gets so flaming hot that it warps its flimsy plastic casing! So, I've thrown in the towel and re[laced it.

The meenee is a tempting proposition because it's so cheap, but it is very flimsy with no battery life. Clausoft were selling these dirt cheapon eBay recently but now seem to have vanished and their meenee.me site is'down for maintenance'. So, I would give meenee a swerve...

---


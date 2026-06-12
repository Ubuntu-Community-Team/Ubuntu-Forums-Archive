---
title: "Acer Aspire One AOD150-iBb and 9.04"
date: 2009-06-17
forum: Hardware
---

### Post by Sui Nim Tao on 2009-06-17
Hi,

This is a general outlook and compatibility report on the ACER AOD150-1Bb (D150), this is the UK version (blue) with no Bluetooth or 3G sim ability for mobile broadband and the 2200mAh 3 cell battery.

Well first off, I’ll give my feedback on the device to those thinking of purchasing one, I have had for 2 days and need to get time to play with it more.

As usual here in the UK we seem to pay over and above the costs of most other countries but I managed to get this at £279, so not bad for saying, but then it has some bits missing as mentioned above.

Now the Bluetooth doesn’t bother me, I have a dongle, the 3G ability too doesn’t bother me, I would rather use a dongle as it is easily interchangeable between laptops, but the battery, the piddly little 2200mAh battery only lasts for about 2 and a half to 3 hours, which is pretty rubbish to say the least.

**So bad points**

1) Battery life (purchase a 4400 if you can at around £50)

2) No Bluetooth (not a deal breaker for me, check your specs some have this)

3) No 3G (not a deal breaker for me, check your specs some have this)

4) No slip or bag in the box, tight ****’s

**Whats average**

1) Keyboard, bigger than a eeepc900, but smaller than a NC110, suitable for medium  sized hands (lucky for me)

3) Trackpad area is averagely sized

**Good points**

1) Easily upgradeable, has service areas on back for upgrading HDD, ram, wireless

2) Trackpad area is recessed slightly, this is a god send for me as I no longer catch it when typing.

3) Trackpad is very sensitive, much better than my eeepc900, I can get to both sides of screen with mouse in one stroke and I don’t have to push my finger through it to get it to work, it works with a gentle struck.

4) Everything’s stiff, mouse buttons, ports, screen, my eee was like a clowns pants when I first got it, makes for good wear.
5) Screen quality good, res is still only 1024X600 on a 10.1” display, but everything is so much bigger, you can then down the fonts size to 8 or 9(would be 10 on the eee 8.9”), and you actually get more real estate on your desktop as the text is smaller and still very readable. Effectively, I have more space on desktop and in programs as the windows adjust to the smaller text size.

6) Full sized right shift key, man if you type a lot this is a big deal, trust me. Also you get proper page up down keys not a crappy function key combo, there really are a lot of keys on that keyboard, certainly more than a Dell mini.

7) It has the 280 atom, which is running at 667mhz so a little quicker than the 270 atom which is more common (check your specs, I here you can get 270 ones too, maybe we did score 1 here in the UK).

There are other areas, but they are more personal choice really, like a glossy screen, nice look, mouse buttons at bottom, glossy case (if you don’t mind a finger magnet).

First thoughts, I love it, it’s super quick with ubuntu 9.04 on it using ext4, boots in about 20 seconds (has quick boot, and a nice f12 option for boot device select), shots down in about 5 to 10, trackpad is awesome (maybe it doesn’t need to be bigger), very sensitive but I like this (the track pad on eee900 is god awefull).

Battery life sucks like a big sucking thing in a sucking contest that won first prize for sucking, but I have a 6 cell on order, the wireless activity light doesn’t work at present (there is a fix) although wireless works well, and the mic is none existent. So lets go into more detail.

**9.04 out the box**

1)Boots fine, no problems, installed from USB device

2) Correct resolution at 1024 X 600 (might want to turn font size down though)

3) Wireless works out the box (atheros chipset), tested on WEP and WPA (ensure you switch on by sliding the switch on the front across). The wireless will search and find wireless points without being switched on, but will not connect (as it still receives but not transmit), so don’t think it’s not working if it cannot connect, you need to switch it on.

Only thing is you don’t know when it’s on as the LED activity light for the wireless, doesn’t work in ubuntu, so if you cannot connect, just push the switch and try again.

There is a fix for this, so I will try this and report back when I have time, it’s not a deal breaker as it all works so I will sort this when I can.

Also there is the ability to install the closed source atheros drivers if you have issues with the open source ones, do to device drivers in administration.

4) Ethernet works (cannot test gigabit connection as no router with this functionality)

5) VGA out works, can switch between modes using as dual screen or replicate screen, this can be a pain to get right but works well once set. You can switch using the function key for external monitor.

6) USB work, all 3 work fine and pickup all 3 of my memory sticks, an external hard drive, dvd, printer, Bluetooth.

7) SD card slot works fine with my 8gig card and 4gig card, still works after suspend too, full size card sits flush, is tight fit too.

8 ) headphones not tested yet, although reports are that it works but doesn’t turn off main speakers, will verify this.

9) ext mic not tested yet, although reports are that it works, will test this.

10) Int mic does not work yet, next kernel upgrade??

11) camera still not tested yet, although reports are that it works, will test this

12)  Sound works fine, no crackles are hissing, a little stutter under heavy load, but then this is a netbook isn’t it. Sound is plenty loud enough for a netbook.

13) Suspend works fully, is very quick too about 5 to 10 seconds to suspend and about 2 seconds to come out and bring up the login. After suspend the wireless reconnects and was fine after an hour of browsing, sound still worked fine playing moving clips back and all seemed to work as before. The lid has no action, if you shut the lid the netbook just turns the screen off but doesn’t suspend (I hear this can be fixed, will look into it)

14) All function keys work apart from the first 3 which look like they might be tied into windows OS maybe, not sure as I don’t recognise the symbol, but the following function keys work, sound up/down, mute, brightness up/down, monitor select, turn off track pad, suspend.

15) 3D desktop works, I can get all extra effects working very smoth so driver seems to be fine

16) Checking the system monitor, the 280 is reported as 2 cpu’s (due to hyperthreading ???), all seems to look ok, still need to monitor CPU temp to check cooling.

Overall there are a few little niggles, but them this is linux, and wouldn’t be the same without the niggles. I can live with that, I will update this as I can, I am doing this as there doesn’t seem to be a lot on the D150, so this is my findings,.

The system seems very quick, there is no lag, no firefox lockup (like some netbooks, eee900), I will carry out the firefox changes though, like switching on write while loading page (this helped on eee900 a lot as firefox waits on loading pages while writing to hard drive, and I had the dog slow 16gb SSD, if you have this use ext4 file system made a big difference).

I can whole heartedly say  this is a good bit of kit, quite well supported, needs the 4400 battery as standard, but apart from that, I can use as a normal laptop. I have run virtualbox with XP on it while browsing web and checking emails with only 1gig of RAM (although Vbox can be a little slow, so will get 2gig). If you want to update the Ram to 2 gig, you will need to buy a 2 gig stick of 667mhz DDR2 (SO DIMM) and replace the 1 gig one through the access point on the back.

There maybe something I have missed but this is a good starting point, so I will report back as I can.

SO overall 8/10 for this baby, I’m not sending it back, I love it.

Paul

---

### Post by malangaman on 2009-06-17
Thanks for the fine report.

---

### Post by Sui Nim Tao on 2009-06-17
No problem,

An update on the things I missed off,

Mic, this is definitely not working, I have confirmed this again, external mic should work though as i'm told, but have no mic to check this.

Headphones, these do work, in the headphone jack, and they also kill the sound to the speakers when inserted, something that failed on other aspire one series

webcam, this works fine, as tested in ekiga

So the D150 pretty much works out the box, with only the mic, wifi led, giving issues, and the wifi led has fixes out there.

They also need to work on the lid switch too, but again i think there is a fix out there for this.

oh and system temp sits there at 27 degrees c so all good on that front.

I'm am very happy with this, I will update on fixes to the broken things as I find them, or others can add to this thread, I will more than likely have a good stab at them when I have five min free.

thanks

Paul

---

### Post by malangaman on 2009-06-18
This link has been very helpful to me:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by itziar on 2009-06-19
I'm absolutely new in Ubuntu. After many days trying, my mic is finally working! I have the AAO D-150, and the internal mic hasn't worked until I've installed the []("http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.30-2-generic_2.6.30-2.3_i386.deb")[new kerne]("http://launchpadlibrarian.net/26201996/linux-image-2.6.30-2-generic_2.6.30-2.3_i386.deb")l[COLOR=#000080]_,_[/COLOR], as I read in another post.

Edit: The link was broken. Now it should be ok!

---

### Post by Sui Nim Tao on 2009-06-19
Good to hear the new kernel will fix this, I will await the next release of ubuntu i'm not fussed about fixing it till then as i never use it.

Thanks for the link i'll check that out when i have 5 free.

Paul

---

### Post by dabernathy on 2009-07-15
Hi all,

I'm running Ubuntu netbook remix on an Acer Aspire One D150, and things have been working pretty well. But recently my sound went completely out, and it looks like the sound card is no longer recognized (aplay -l give me nothing). I tried intalling the latest ALSA upgrade but still no sound. Any help for this noob?

---


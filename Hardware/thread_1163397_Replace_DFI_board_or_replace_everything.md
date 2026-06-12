---
title: "Replace DFI board or replace everything"
date: 2009-05-18
forum: Hardware
---

### Post by Tux+ on 2009-05-18
I have a DFI Infinity NF4 board that is over 5 years old on a socket 939 running an AMD 4000+, 2GB RAM. I've been pretty happy with the set up so far but the latest version of Ubuntu (8.10 and onwards) complain about a BIOS bug. I'm on 8.04 at the moment and it runs fine.

I have tried turning off ACPI, APIC, etc but either it locks up or it runs dog slow. In short I am thinking about replacing it.

My question is shall I replace just the mothboard with an Asrock 939N68PV (Because that's the only one I can get from UK online store) or save a bit up and replace everything for a new Core 2 duo system. The Asrock board costs £60 but I'm looking to spend £200 on an upgrade.

The reason why I want to move onto the new releases is because I have Hauppage TD-500 which I can not get up and running in 8.04 but have managed to see it work (breifly) on 8.10.

This is a desktop / mythbox setup and not sure if I want to spending another £60 on an aging system or wait (at least till end of summer) and get a whole new system. The advantage of getting the new mobo is that I can wait till next year and migrate the current box as a mythtv server and a separate desktop or buy a new system earlier and have the mythtv/desktop set up continue.

Sorry for the long post but comemnts welcome.

---

### Post by Dark_Stang on 2009-05-18
If it was me, I would just wait and build. Multicore is the only way to go these days. And if you have a processor that fits a 939 socket, I'm assuming it's at least 3 years old, so you never know when that's going to go. 

My roomate did a fresh build this year because his 939 board died. We actually couldn't find a new 939 board at a decent price (in the US) so he ended up getting a decent AM2 board, a cheap dual core processor, and 2 gigs of memory for about $130 USD total.

---

### Post by Tux+ on 2009-05-19
Thanks for your suggestion. I was on the fence about the decision and if there are no more replays I'll go with getting a new build.

---

### Post by coffeecat on 2009-05-19
> **Tux+ said:**
> The Asrock board costs £60

That's from Ebuyer, isn't it? :wink:

I saw your post last night and I had a hunt around in my bookmarks to see if I could find a different socket 939 board here in the UK, but could only find the Asrock with about half-a-dozen suppliers. Could have saved you 54p though. :p

I'd go for the new build. Old technology is usually more expensive. I didn't look closely at the Asrock specs, but I wouldn't be surprised if you could get something much better with an AM2+ socket but cheaper. And, as Dark_Stang said, the dual-core X2 processors are coming right down in price.

As far as the Hauppage card is concerned, here are a couple of links that may or may not help to get it working in Hardy. You can install a whole load of kernel drivers from [this site]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers"). Be warned, there's hundreds of the blighters. If you're lucky, your Hauppage might be among them. Or, [The Linx Tv Wiki]("http://www.linuxtv.org/wiki/index.php/Main_Page") might lead you somewhere useful.

Is your Hauppage a PCI card or USB? If USB, do a lsusb. The USB ID (in the form XXXX:YYYY) might help with a google search.

---

### Post by Tux+ on 2009-05-19
Thank coffeecat for the links. The TV card is a PCI and dmesg does detect the card correctly I will try it out later this week. You can see my (dead) thread about it here:
[http://ubuntuforums.org/showthread.php?t=1098160](http://ubuntuforums.org/showthread.php?t=1098160) 

I did see the mobo on Ebuyer =p as well as other places for more £££.

In terms of a Core 2 mobo do you recommend any? I've always tended to go for Asus but saw the P5Q range has problems in Ubuntu.

---

### Post by coffeecat on 2009-05-19
> **Tux+ said:**
> In terms of a Core 2 mobo do you recommend any?

Funny you should ask that. [I might be in the market for a new m'board myself]("http://ubuntuforums.org/showthread.php?t=1163870"). You don't know of a good ATI card do you? :p

Whatever, don't get an Abit AN-M2 which is the board giving me the problems. Not that you can anyway - Abit has withdrawn from the motherboard game. Hooray!

> **Tux+ said:**
> I've always tended to go for Asus but saw the P5Q range has problems in Ubuntu.

Depends on how long ago. With a new chipset you'll always get problems until the drivers get into the kernel. Weren't all the problems last year? I must admit I haven't been following the saga. I know that's an Intel board but if, by chance, you wanted to get a motherboard for an AMD CPU, Personal Computer World magazine lists [this Gigabyte one]("http://www.ebuyer.com/product/160853") in its Best Buy list, even though they reviewed it a year ago. Actually, strictly speaking they're recommending the GA-MA78GM-S2H, but that was the nearest I could find on Ebuyer. I don't know whether it's compatible with Ubuntu - looks as though it ought to be - but if I don't get a response to my thread I'll be looking seriously at that board myself. I'll be doing some searching around first, of course.

---

### Post by Tux+ on 2009-05-19
I doubt I will go with AMD this time round so I have settled on looking for an Intel machine and it has to have PCI since my TV card is too.

As for the P5Q problems I didn't notice the timestamp on the posts / articles. Thinking it was Intel I would have thought it worked out of the box since they are pretty good to the FOSS communtity.

Good luck with the mobo hunt and let me know how you get on.

---


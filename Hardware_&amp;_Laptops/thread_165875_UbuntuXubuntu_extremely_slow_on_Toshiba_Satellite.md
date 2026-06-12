---
title: "Ubuntu/Xubuntu extremely slow on Toshiba Satellite"
date: 2006-04-25
forum: Hardware &amp; Laptops
---

### Post by shamrock_uk on 2006-04-25
Basically, my problem is that Ubuntu crawls (incl Xubuntu / Kubuntu) relative to the performance of Windows XP or Windows 2000 on my laptop. 

Sorry, the laptop case doesn't appear to have the exact model number on it, but it's the Satellite which has a Celeron 800 with 128MB of RAM and a ~16GB hard drive. 

I've hesitated to post as there's no one package that runs slow that I can pin down, nor is it fixed in Dapper which has generally been much swifter on other machines in my experience. Nevertheless, perhaps someone out there can help.

Basically, any sort of multitasking whatsoever brings the system to an almost complete halt - starting something like gaim can take a full minute if something else is happening in the background. It grinds to a complete halt if something like synaptic is installing packages.

I can't watch divx films without unacceptable distortion - even with hard framedropping in mplayer it's still not great. DVDs are out of the question. It takes about 2 minutes to boot, another good minute to load Gnome. 

All the usual basic optimisations like DMA are enabled on all drives, the times from hdparm seem reasonable and installing a light WM like xfce really doesn't help (apart from a slightly faster time to desktop).


Yet Windows absolutely flies in comparison - I realise that it prelinks extensively for faster startup times, but it will let me watch DVD's and divx's with no problems. I can multitask easily - winamp + opera + downloads with no delays in switching. In Ubuntu I'm looking at a good thirty seconds of maxed out hard drive and no response simply to switch between them. Right now in WinXP, I have winamp open (but not playing), an opera download in progress and I'm playing Alpha Centauri, yet the system is perfectly responsive. 

I just can't explain this difference, especially considering that WinXP is pretty RAM thirsty after all, certainly using more than xfce, yet in Linux it just seems like I'm on a computer that has only a fraction of the power. Furthermore top doesn't show all my RAM as being utilised so I'm not even sure that extensive swapping is the problem here. I've even tried using fluxbox, but it doesn't solve the performance issues, although it does start reasonably fast at about 10 seconds.

It also seems to be fairly similar across distributions, so I'm inclined to think it's not purely a Ubuntu issue. 

If anybody could offer some help or general advice it would be much appreciated - I'm at a complete loss to explain this, especially as it occurs in Suse 10.1, Breezy right through to the most recent Dapper build, across many seperate (and on occasion, clean) installs.

Thanks in advance... :)

---

### Post by Tom Tiger on 2006-04-26
If you have the serial number or the Pat code from the bottom of the system (big silver sticker) I can easily trace how the system was configured.  

However.... 128 mb of ram is not very much.... I would recommend upgrading the system to at least 256 mb or if possible 512 mb of ram.  It is odd that XP runs good with only 128mb...but.... how big is your swapfile under linux?

To check what upgrades are possible on this toshiba I need the exact type.

---

### Post by shamrock_uk on 2006-04-26
[QUOTE=Tom Tiger]If you have the serial number or the Pat code from the bottom of the system (big silver sticker) I can easily trace how the system was configured.  

However.... 128 mb of ram is not very much.... I would recommend upgrading the system to at least 256 mb or if possible 512 mb of ram.  It is odd that XP runs good with only 128mb...but.... how big is your swapfile under linux?

To check what upgrades are possible on this toshiba I need the exact type.[/QUOTE]

Thanks for your reply Tom Tiger. 

I'll look up the serial number when I get in from work, but tbh I doubt I'll spend any money upgrading it. I received it second hand for only £150 quid and having just bought a top-end desktop am not really planning to spend any money on it. 

I'm just really confused to be honest - the first thing I did when I got the laptop was wipe Windows, but now I've ended up reinstalling it...most peculiar. 

I created a swap partition using the 2 x system RAM guideline - so it's 256MB. 512MB would perhaps be better but the arrangement of the partition tables makes it more trouble than its worth to increase the size. 

Am I correct in thinking that the Celeron 800 should be using the 386 kernel? A look at the 686 package didn't mention the Celeron in the list of appropriate processors. 

I hear what you're saying about RAM, but to be honest I've never had performance problems with either Windows or Ubuntu with 128MB before. 

My parents computer at home is a K6-2 500 with 128MB of RAM and its Ubuntu performance blows my laptop out of the water (performance is good and multitasking is not a problem). Sure, the K6-2 is a better processor, but with a cool 300MHz advantage to the Celeron I wouldn't expect *this* much of a difference. Especially when we're not really talking FPU-intensive tasks. 

Serial number to follow :)

---


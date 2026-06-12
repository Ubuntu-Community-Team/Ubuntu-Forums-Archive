---
title: "Please advise me on how to do a linux install on the 'generic chinese 7&quot; notebook'"
date: 2015-12-11
forum: Hardware
---

### Post by martin183 on 2015-12-11
I'm at my wits end with this thing now. 

I've read through the 100 odd page thread well large chunks of it and still can't make progress with the thing. 

I bought it for 20 bucks on ebay seeing windows (knowing nothing of the horrors of CE at the time) thinking it would be a simple matter of a quick wipe and install. Hey it runs windows it MUST run linux right? WRONG!

It is so tantalising that the thing looks neat and I read even some success stories but each time I'm hit with brick walls and getting good information on these backwards devices is really a masochistic act.

I was able to get into the bios with the ztk or whatever but then non of the option made sense so didn't help me. 

I read the instructions about putting the fat part on sd card and the ext3 part on the rest of the card. I tried to boot with it but the notebook doesn't read it or try and boot from it like others say. It just totally ignores it. I read others having this issue but no clear solution.

I notice my version chip isnt the same as the guys purporting success. The success stories I read seem to all be on 8505 (850 something anyhow might not remember right) but mine is 7802. But the thing is the board and adhoc BIOS is exactly the same as the OP in that long thread so I wonder if somehow it could work with their instructions.

Here are my specs: 
> 

[LIST]
[*]Processor : AK7802Q216 248MHz: 
[*]Display : 7&#8221; High resolution TFT .(800 x 480 pixels) 
[*]Internal Memory : DDR 64MB / 2GB Nand-flash 
[*]External Memory : SD card , U-Disk , USB-HDD 
[*]Connectivity : - WIFI RIEEE 802.11 b/g - Ethernet RJ-45 
[*]Connections  : - USB 2.0 x 1 (supports external memory) - USB 1.1 x 2 (supports  keyboard & mouse only) - SD / MMC card slot (up to 8GB) - Microphone  jack x 1 - Earphone jack x 1 - DC jack x 1 
[*]Speakers : Built in 2 x 0.5W 
[*]Keypad : QWERTY 86 keys 
[*]Battery : 7 
[/LIST]
                           


So since I cant get it to boot from sd card I have no idea what to try now? Im really thinking I should just cut my loses and resell on ebay because looking at other closed auctions it seems I could quite likely get my money back since I got a cheap deal. At worst it woud be a learning lesson and Id still get something back. Im really getting sick of it now and would just like the frustration off my mind of constantly being disappointed at searching online for hours and hours day after day and getting nowhere.

At the same time I wonder if success is just around the corner if someone could give me the right code to open the safe. Likewise I could easily wreck it from what Ive read and it would be even more useless than it is now with dreaded windows ce. 

So this post is my last ditch attempt at maybe getting some answers as to a solution or if people say Im better off cutting my loses then I will do that.

To note I only wanted something I could rdp into my main computer on windows. And windows ce while it suppsedly could run rdp i kept getting the stupid execution errors thanks to windows ce- even tho I apparently downloaded the ce version of rdp; still it wouldn't execute. So if I could get rdp working that would be an alternative but ideally it would be nice to have a slim linux on it. So advice for either of those would be welcome.

---

### Post by matt_symes on 2015-12-11
Hi

> **martin183 said:**
> I'm at my wits end with this thing now. 

I've read through the 100 odd page thread well large chunks of it and still can't make progress with the thing. 

I bought it for 20 bucks on ebay seeing windows (knowing nothing of the horrors of CE at the time) thinking it would be a simple matter of a quick wipe and install. Hey it runs windows it MUST run linux right? WRONG!

It is so tantalising that the thing looks neat and I read even some success stories but each time I'm hit with brick walls and getting good information on these backwards devices is really a masochistic act.

I was able to get into the bios with the ztk or whatever but then non of the option made sense so didn't help me. 

I read the instructions about putting the fat part on sd card and the ext3 part on the rest of the card. I tried to boot with it but the notebook doesn't read it or try and boot from it like others say. It just totally ignores it. I read others having this issue but no clear solution.

I notice my version chip isnt the same as the guys purporting success. The success stories I read seem to all be on 8505 (850 something anyhow might not remember right) but mine is 7802. But the thing is the board and adhoc BIOS is exactly the same as the OP in that long thread so I wonder if somehow it could work with their instructions.

Here are my specs: 


So since I cant get it to boot from sd card I have no idea what to try now? Im really thinking I should just cut my loses and resell on ebay because looking at other closed auctions it seems I could quite likely get my money back since I got a cheap deal. At worst it woud be a learning lesson and Id still get something back. Im really getting sick of it now and would just like the frustration off my mind of constantly being disappointed at searching online for hours and hours day after day and getting nowhere.

At the same time I wonder if success is just around the corner if someone could give me the right code to open the safe. Likewise I could easily wreck it from what Ive read and it would be even more useless than it is now with dreaded windows ce. 

So this post is my last ditch attempt at maybe getting some answers as to a solution or if people say Im better off cutting my loses then I will do that.

To note I only wanted something I could rdp into my main computer on windows. And windows ce while it suppsedly could run rdp i kept getting the stupid execution errors thanks to windows ce- even tho I apparently downloaded the ce version of rdp; still it wouldn't execute. So if I could get rdp working that would be an alternative but ideally it would be nice to have a slim linux on it. So advice for either of those would be welcome.

Even if you could get Linux to run on it, I'm not convinced the CPU's (ARM @ 248MHz with 64M Ram) powerful enough for what you want (rdp).

Kind regards

---


---
title: "considering purchasing an acer 3680-2022"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by dynacrylic on 2007-03-12
I'm considering purchasing an Acer 3680-2022 and curious if anyone else has installed some flavor of ubuntu on it or something comparable to it. 

Here's the basic specs:
*  Intel® Celeron® M Processor 430
* 512MB PC4200 DDR2 RAM
* Combo 8x DVD-ROM; 24x24x24 CD-RW
* 14.1" Widescreen XGA CrystalBrite display
* 80GB 4,200RPM Ultra ATA Hard Drive
* Intel® Graphics Media Accelerator 950 Video Chipset (Up to 224MB of Shared Memory)
* Acer InviLink 802.11b/g Wi-Fi CERTIFIED Wireless Network

The laptop is pretty cheap ($399 us dollars). I can only see myself using it for word processing, email, web browsing and atlantik.

I'm only concerned with driver issues and basic performance at this time.  I'm not too worried about it running beryl. But if someone is using something a laptop comparable to this and actually running beryl on it, it would be great to hear how it performs.

thanks much!

---

### Post by matburton on 2007-03-13
Hey,

I have something slightly similar. Its a Rock Pegasus 650.
1GB DDR2 & Centrino 2GHz

I have the i915 as well (Intel 900GMA) and I'm running beryl fine!
I needed to install the 915resolution fix first though.
Also other people have needed to adjust the memory the card uses in xorg.conf.

I know nothing about that wireless card!

Hope that gives you a bit of insight.

---

### Post by bazzer on 2007-03-13
Well I'm posting from a Travelmate 2492WLMi, WXGA 15.4, IG950, WLAN etc.... All works ok after some initial faffing, but I wouldn't say it works perfectly straight away. I had to install this [915 fix]("http://ubuntuforums.org/showthread.php?t=277690&highlight=intel+950+graphics"), and the wireless was a nightmare until I finally followed a good guide.... I have a broadcom internal card and [this]("http://www.ubuntuforums.org/showthread.php?t=341357") worked for me...

---

### Post by MJN on 2007-04-03
Dynacrylic, are you still considering the purchase?
 
If so, thought you might be interested to hear I've got the very same machine and Dapper Kubuntu is working fine on it. Whilst the majority worked out of the box the usual 915resolution package was required for the widescreen resolution. WiFi also worked by default although some addiotnal configuration was required to get WPA-PSK encryption off the ground.
 
Most of the Fn keys work (as they're low-level hardware based) however the volumes ones will require further configuration - from what I've read it's relatively straightforward but I've yet to get round to it.
 
Mathew

---

### Post by daigonsai on 2007-04-05
> **dynacrylic said:**
> I'm considering purchasing an Acer 3680-2022 and curious if anyone else has installed some flavor of ubuntu on it or something comparable to it. 


Posting from a 3680-2022 running Kubuntu Edgy.  

> 
Here's the basic specs:
*  Intel® Celeron® M Processor 430
* 512MB PC4200 DDR2 RAM


Runs Vista very, very slowly.  Quite adequate for Kubuntu, even with the system carving out 64MB of memory for video use.

> 
* Combo 8x DVD-ROM; 24x24x24 CD-RW
* 14.1" Widescreen XGA CrystalBrite display
* 80GB 4,200RPM Ultra ATA Hard Drive
* Intel® Graphics Media Accelerator 950 Video Chipset (Up to 224MB of Shared Memory)


A quick note about the GMA 950 and its 224MB of shared memory: the only video memory options available in the BIOS are 64MB, 128MB, and something called "MaxDVMT" for which I haven't been able to find a comprehensible definition.  Perhaps that's where you can get your 224MB.

> 
* Acer InviLink 802.11b/g Wi-Fi CERTIFIED Wireless Network


The label on the bottom of the machine says "Atheros AR5BMB5".  From what I've found via Google, AR5BMB5 appears to be Askey's model number for a wireless card using an Atheros chipset.  The Madwifi drivers work fine (once you get them working--see below).

> 
The laptop is pretty cheap ($399 us dollars). I can only see myself using it for word processing, email, web browsing and atlantik.


It's certainly an adequate machine for those tasks.  I can't speak for Atlantik, but it runs Maelstrom just fine. :)

> 
I'm only concerned with driver issues and basic performance at this time.


The machine performs pretty well for an entry-level, value-priced system.  Regarding driver issues, this is what I've found so far:

[LIST]
[*]The front-panel switch will enable and disable the wireless adapter, but the LED is always on.  If you get a message that the "hardware revision is not supported", then the following commands should fix it:

**modprobe -vr ath_pci**
*(push the front-panel switch ONCE)*
**modprobe -v ath_pci**

I have yet to find anything that will cause the front-panel LED to correctly report the status of the wireless adapter.  If anyone knows of any software to do this, please let me know. 


[*]The euro-sign and dollar-sign keys (on either side of the up-arrow key) don't work.  They don't even produce scancodes.  They worked under Vista, so I'm guessing some sort of special keyboard driver is required for full functionality.  (The four hotkeys at the upper left produce scancodes.  The "mail" button even brings up the composer of your default e-mail program.)


[*] The 915resolution hack is required to get 1280x800 resolution.


[*] You'll want to configure an InputDevice section for the touchpad in xorg.conf, and install ksynaptics, qsynaptics, or gsynaptics to tweak it.  The touchpad is pretty difficult to use with a plain vanilla mouse driver.


[*]Haven't yet attempted to use the modem, card reader, or any PCMCIA/Cardbus devices.
[/LIST]

> 
I'm not too worried about it running beryl. But if someone is using something a laptop comparable to this and actually running beryl on it, it would be great to hear how it performs.


I don't have Beryl installed currently, but I did "install" it a couple of times while running from the Live CD.  (I was very surprised that this worked, but I had to try it because I needed knetworkmanager, and when it worked I decided this would be a good opportunity to try out a few other things.  Of course, the things I installed didn't persist between reboots :) )  I didn't do much with Beryl while it was here, but it seemed to run rather well.  OpenGL screensavers, on the other hand, have performed horribly so far.

> 
thanks much!

No problem.

BTW, Acer will give refunds for the OEM Vista Home Basic (a little over $50), but their policy requires you to ship the machine to them.  Considering shipping costs and the time you'll be deprived of the use of your machine, it's just not cost-effective unless you live next door to the service center.  Make a factory restore disc (or disc set, if you don't have a USB DVD writer), put it on the shelf, and wipe the drive to install your Ubuntu.

If you don't want to pay the Microsoft tax, don't buy Acer--or at least understand the cost of reclaiming that portion of your money.  If I had it to do over, I'd just go to System76 and pony up the extra $200 for the Gazelle Value (for you it'd be an extra $300; I paid $499 for my Acer).  System76 would offer better support for a Linux installation anyway--even in the markets where Acer sells laptops with Linux installed, they don't worry about the hardware actually functioning out-of-the-box.  From the reports I've heard/read, they just slap a default installation of Linpus Linux on it and ship it out. 

That's all I've got.  Hope it helps.

---

### Post by MJN on 2007-04-05
Great post - good to hear your experiences with this machine...

> **daigonsai said:**
> Posting from a 3680-2022 running Kubuntu Edgy.  

Runs Vista very, very slowly.  Quite adequate for Kubuntu, even with the system carving out 64MB of memory for video use.


Whilst I'm no particular fan of Vista (I'm keeping it for curiosity sake) I can confirm it runs much, much faster with 1024MB on this machine. The difference is incredible and kind of makes the default 512MB a very poor, and sneaky, cost cutter given it comes with Vista pre-installed. Pre RAM-upgrade I was finding Vista practically impossible to use (some might say that's not down to the memory! ;))

> A quick note about the GMA 950 and its 224MB of shared memory: the only video memory options available in the BIOS are 64MB, 128MB, and something called "MaxDVMT" for which I haven't been able to find a comprehensible definition.  Perhaps that's where you can get your 224MB.The BIOS memory settings are, as you know, the amount of shared memory to give to the video adapter. However note that these are *maximum* values i.e any that's not used by the video adapter is left in the pool for the OS. MaxDVMT is, as you say, somewhat under-discussed on t'interweb however I did find an Intel doc that attempted to clarify what it meant and from what I recall it is practically the '*assign whatever it needs upto 224MB*' setting but again, if the video doesn't require it at any moment in time it is returned to the pot. Now that I've got 1024MB RAM MaxDVMT is a safe setting (and indeed I think Intel may even have said that for RAM >=512MB this should be the desired setting).

> [LIST]
[*] I have yet to find anything that will cause the front-panel LED to correctly report the status of the wireless adapter.  If anyone knows of any software to do this, please let me know.[/LIST]I'm sure I read that the **acerhk **module can enable the front panel LEDs to work correctly. Or was it just the buttons? Not sure... (haven't investigated further)

> [LIST]
[*]The euro-sign and dollar-sign keys (on either side of the up-arrow key) don't work.  They don't even produce scancodes.  They worked under Vista, so I'm guessing some sort of special keyboard driver is required for full functionality.  (The four hotkeys at the upper left produce scancodes.  The "mail" button even brings up the composer of your default e-mail program.)[/LIST]Hmm... I'm sure I got scancodes when I messed with them (sorry, not at the machine right now) so perhaps it is a 'driver' issue... but then I don't know why I'd be using a different one that you (other than that I'm using Dapper).

> That's all I've got.  Hope it helps.It certainly helps me - it's one of the rare occasions in the world of Linux that having a laptop is an advantage - at least there are others with *exactly* the same hardware setup as yourself!

Mathew

P.S. I swapped my US keyboard for a UK one (I bought it whilst away on business) and having removed the top panel noticed there is an LED under the e-mail hotkey - I always assumed I was just missing some paint on the envelope logo but it turns out it's transparent. So, I was wondering if you've ever seen it light up? I haven't but then I don't expect it to - all my e-mail is done via webmail however I was wondering how it is accessed as I'm sure I could rig something up to monitor my mail and light that thing (in Kubuntu and/or Vista).

---


---
title: "&quot;Just Works&quot; USB WiFi/SATA/Bluetooth Suggestions"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by sceo on 2007-10-19
Hey all.  I'm one of those people you may have read about on Slashdot a few days ago.  That is, I'm sick of XP but DON'T want Vista!  I have a 64-bit processor, but I have to run 32-bit XP, which feels wasteful.  I'm not paying for Vista, so I want to make a permanent switch to Ubuntu (Gutsy 64-bit).  Thanks to Google Docs and Aptana, I think I've got all the functionality I need on a *nix Distribution, and I love Ubuntu (have it on my laptop).  So, for my desktop -- in order to make the switch -- I'll need some new hardware.  
[LIST]
[*]Wifi NIC (USB or PCI)
[*]SATA Hard Drive
[*]Bluetooth Dongle
[/LIST]
The #1 thing keeping me from the switch now is my current wireless card.  My current card will work with Ndiswrapper, but NOT with SMP!  I definitely want the SMP and 64-bit, since that's what's frustrating me about WinXP now.  I mean, I have a dual-core 64-bit processor, just wasting away.  So, I ask (and I know this has been asked before, but not answered too well), what Wifi (either USB or PCI) "just works" out of the box, *and supports WPA*?  I prefer USB, but would definitely get a PCI if it just worked.  I am also willing to pay a premium for hardware that will just work.

Secondly, I need a SATA hard drive (I'm getting rid of this IDE hard drive cuz it's slow, and putting it in a second desktop machine for my girlfriend's school use).  How is SATA support in Gutsy/amd64?  Any recommendations for SATA drives?  I don't need anything big at all, I would be fine with 80GB.

Thirdly, I'd like some kind of Bluetooth support.  My consulting business relies heavily on Skype since our partners are scattered all over the country.  I practically *require* the Bluetooth headset for chatting on Skype.  I already have a Bluetooth dongle that I might be able to get working, but if there are recommendations I'll take them.

Again, primary importance is the NIC.  Thanks in advance to anyone who has any 'just works' recommendations for any of these three pieces of hardware.  From looking at other posts, writing about hardware that DOESN'T work is not helpful.  Please post only if you know of hardware that "just works."  With any luck, this post may become a resource for future use.  Thank you thank you thank you!

---

### Post by jsully1 on 2007-10-19
If you have no specific reason to use a 64bit OS, then there is absolutely no reason to switch to it.  The only real reason to switch to a 64bit install is to utilize more than 3.5GB RAM, since 32bits can only address 4,096 megabytes total without some fun PAE hacks.  

There is no performance benefit from going to a 64bit OS, and you may even find that driver and program support is far worse - for example there's no native flash player build for 64bit linux.  I've got a Core2Duo in my laptop with 2GB RAM, I rock a 32 bit install, and would never really consider going to 64 bit as I just don't need it and the headaches that can accompany it.

That said SMP *is* important, as it allows your OS to take advantage of both cores.  32bit XP should have no problem whatsoever supporting your dual core CPU.

Wifi, SATA (been around for like 10 years now!) and many blutooth dongles should all work out of the box.  The nice thing is that you can just boot your computer with the Gutsy Installer CD and you'll be able to tell immediately (before installing) if things work out of the box.

---

### Post by sceo on 2007-10-19
Hmm, that's good insight.  I do think the 64-bit support is better in the *nix world than the Windows world, but that may just be my perception.  You make a good point, though -- I only have 2GB of RAM.  So I probably will install the regular i386 version of Ubuntu to maximize software choices, but will definitely want to utilize SMP, which doesn't work with my existing NIC.  Have you any experience with specific Wifi cards, SATA drives, or Bluetooth dongles that "just work?"  (love that phrase... ;) )

---

### Post by jsully1 on 2007-10-19
SATA support will be based on the controller on your motherboard.  I've tried a number or boards by MSI, ASUS, and Abit that have all worked out of the box.  My Thinkpads (T22 and T60) also work no problem.

Wireless also works out of the box with my Thinkpad (built in Intel chipset), that's about the extent of my hardware experience though.

---

### Post by sceo on 2007-10-19
OK, good to know that it's the motherboard chipset.  I can find that out and look it up.  Thanks for replying and being so helpful!

---

### Post by sceo on 2007-10-19
Of course, like I said - wireless is most important, without that - everything else is pointless.  Who has a wifi card that just works with WPA?

---

### Post by sceo on 2007-10-19
Ahh, THIS helps!  Took me a while to find, though:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I also think my SATA controller "should" work, based on the linuxquestions HCL.  So, I think I'm going to pull the trigger on this SATA drive and USB WNIC.

---

### Post by steveneddy on 2007-10-19
Go 64 bit. You will be much happier.

Once you go 64, you never go back.

---

### Post by David A Knight on 2007-10-20
> **jsully1 said:**
> 
There is no performance benefit from going to a 64bit OS, and you may even find that driver and program support is far worse - for example there's no native flash player build for 64bit linux.  I've got a Core2Duo in my laptop with 2GB RAM, I rock a 32 bit install, and would never really consider going to 64 bit as I just don't need it and the headaches that can accompany it.
.

Except of course amd64 is a different architecture to plain old i386.  If the architecture is the same then yes, there isn't any benefit directly.  Code compiled for 64bit amd64 will make use of the extra registers that are available, resulting in faster code.

As for driver support, this is linux, the source gets compiled and baring any bugs in the drivers they just work.  There are of course the closed source drivers, but nvidia (being the most used one I suspect) provide a 64bit version.

Program support far worse?  Not at all.  Again, open source, code gets compiled, bang, it works.  Closed source?  not a problem, 64bit linux can run 32bit apps just fine, so long as the 32bit libraries are installed.  Infact gutsy includes a 32bit compiled wine in the 64bit repositories.

32bit flash? nspluginwrapper can apparently get that working in a 64bit browser, or if flash is that important, install a 32bit browser.  Problem solved.

---


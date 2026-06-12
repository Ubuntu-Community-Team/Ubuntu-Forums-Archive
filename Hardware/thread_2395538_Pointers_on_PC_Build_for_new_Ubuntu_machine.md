---
title: "Pointers on PC Build for new Ubuntu machine"
date: 2018-07-03
forum: Hardware
---

### Post by Mr_J_ on 2018-07-03
I've been aching to come back to linux after an ongoing and extended stay in Windows.
The last time I built a machine it was Windows XP and there were some problems with picking up any hardware and have it work off-shelf.

I would like to hear from the forum if this is still the case and if so any points of interest to be aware of.

It's going to be a web browsing computer, preferably silent, no recent games going in. There might be some light programming, but that shouldn't impact too much.
Any motherboards I should look into? That work off the shelf... Or safe bet manufacturers...

Preferably something that last another few years.
I don't need any one specific build, but some pointers would be nice.

The one thing it has to have is wifi! The rest is pretty much open.

Thank you for any and all help!

---

### Post by TheFu on 2018-07-03
For $1500 you can get an amazing machine.   What's the budget?

But really for normal web browsing and not much more, any $60 Intel/AMD CPU would be fine these days.  Linux support is much different than it used to be, provided you avoid really new stuff.

The sort of programming you do matters.  Python, Perl, bash would be easy on anything.  Java, OTOH, means you want a Core i7 with 32G of RAM.  So, if you aren't doing Java, $200 would build a minimal system - get a chromebook.  Main things are look for 1500 passmark or better.

Basically, budget dictates many things.   For under $500, you can build an amazing machine.

But you should also check for any Linux issues with the specific MB and specific GPU and any peripherals BEFORE buying them. Google is your friend.  Audio almost always works.  If you stay with Intel for NICs, those pretty much always work. GPUs can be iffy because there are so many different lines within each vendor.  It isn't "nVidia vs AMD" since different types have different issues.   I've been using the onboard Intel GPUs about the last 10 yrs and been very happy.  Intel GPUs have great support for video and are fast enough for programming.  

Printers are hit or miss.  I'm using a 13 yrs old Samsung laser printer that is well supported.  Also have an all-in-one from brother that does everything except print.  I never bought any replacement ink, since I never intended to use it as a printer.  It scans, faxes, perfectly.

I can't help with wifi.  I don't use it (and never will inside my home) for our computers.  Wifi security is an issue, so I don't trust it. Bluetooth is even worse. There are other threads in these forums about those considerations.

---

### Post by robehickman on 2018-07-03
For web browsing my current AMD A4-5300 is perfectly fine, which was bottom of the barrel 3 years ago when I got it. Considering that anything should be fine, I find that RAM usage is the main issue, with firefox being much better than chrome in that regard.

As noted above, programming with interpreted languages isn't a problem on anything. I wrote my own file synchroniser/versioning system for binary files in python and even on the A4 it's a lot faster than I expected it to be, given python isn't the fastest language in the world and my design strongly favours code simplicity. You can get pretty fast builds with C(++) by including all of the C/CPP files into a single file and compiling that, plus avoiding templates. 'Handmade hero' has some interesting points on this subject, and John Blow's JAI language is being developed along the same idea, I think Go also does this. Java is a language I'm inclined to avoid.

---

### Post by TheFu on 2018-07-03
The AMD A4-5300 has a passmark of 2000. If you want double the performance, look for a CPU with 4000 passmark.  For triple the performance, then 6000 passmark.  An AMD Ryzen 5 1600 is 12,200 passmarks for reference.  That would be a huge jump in performance.

If RAM is the problem, I'd add more, to a point.  If you post **inxi -Fz**, perhaps someone could help better with upgrade suggestions?  Swap management can be important too. Do you want to just trade-out a few parts or build a completely new system?   I'm using the same ATX case from 1999 myself. Still works perfectly, so why bother blowing $40-$100 for a newer one?

Have you been to pcpartpicker yet?

---

### Post by robehickman on 2018-07-03
I was mainly making a point about even low end computers being pretty fast these days for **[COLOR=#000000]Mr_J_,[/COLOR]**[COLOR=#000000] I don't wish to hijack this thread.[/COLOR]**[COLOR=#000000][/COLOR]** The only issue I have with this system is really just a lack of storage options, it's performance is fine for what I do with it.

---

### Post by Mr_J_ on 2018-07-04
Not a problem.
I am considering a budget pc build in order to replace a current laptop if/when it fails. The programming would be in python.
These are just the pointers I needed, thank you! I remember my old wifi card was a pain for years before it got stable enough.
Just wanted to avoid future headaches. Thank you all for your help!

---

### Post by TheFu on 2018-07-04
> **Mr_J_ said:**
> Not a problem.
I am considering a budget pc build in order to replace a current laptop if/when it fails. The programming would be in python.
These are just the pointers I needed, thank you! I remember my old wifi card was a pain for years before it got stable enough.
Just wanted to avoid future headaches. Thank you all for your help!

Wifi adapters change all the time. Which is well supported or not will change over time. I have an Intel wifi chip in my chromebook and it "just works."  OTOH, I use a USB3-GigE adapter at home to avoid using wifi there.  150 Mbps (wifi) doesn't compare to 920 Mbps (wired).  Wifi is something I avoid whenever possible and if I'm forced to use it, there is always a VPN running too - even in my home.   When WPA3 becomes available, I'll still be using a VPN with all wifi.  I simply don't trust wifi security, since every 1-2 yrs a new flaw is uncovered that has been around since the beginning.

Definitely get the exact chip being used for wifi and search for issues people are having using it with Linux.  If it is over a year old and you don't find any issues, it is probably fine.  If wifi is really a huge concern, I'd ask that specific question in the networking sub-forum.  

Mine is "Intel Wireless 7260" and uses the iwlwifi driver.  No idea if that chip is available in a stand alone card.

---

### Post by Dennis N on 2018-07-04
> **Mr_J_ said:**
> Not a problem.
I am considering a budget pc build in order to replace a current laptop if/when it fails. The programming would be in python.
These are just the pointers I needed, thank you! I remember my old wifi card was a pain for years before it got stable enough.
Just wanted to avoid future headaches. Thank you all for your help!

For a desktop machine in a location without ethernet access, consider powerline networking as an alternative to wifi. That was the case for one of our computers here, and the powerline network is far faster  than the wifi is and very reliable.

---

### Post by TheFu on 2018-07-04
> **Dennis N said:**
> For a desktop machine in a location without ethernet access, consider powerline networking as an alternative to wifi. That was the case for one of our computers here, and the powerline network is far faster  than the wifi is and very reliable.

+1 - I use powerline to bridge the network between floors here.  House is 25 yrs old (to give you a wire age) and I'm seeing 60 Mbps between floors using a 600 Mbps powerline kit.  It is mainly used for video streaming to the family room.  Wifi bandwidth varies wildly.  The powerline bandwidth is consistent 55-65 Mbps.  The rest of the house is GigE and rock solid at 920+ Mbps, even going through multiple dumb switches.   

The only warning about powerline networking is to ensure you re-establish the encryption (there is a button on each device) so your neighbors don't have access into your LAN.  Turns out that electrical lines are porous for powerline data connections.

---

### Post by kurt18947 on 2018-07-04
> The only warning about powerline networking is to ensure you  re-establish the encryption (there is a button on each device) so your  neighbors don't have access into your LAN.  Turns out that electrical  lines are porous for powerline data connections.

I think it depends on where the user is. My understanding is that the network signal will be available to anyone on the same transformer. For rural users, each user may have their own transformer so no issue. Someone living in an apartment building in a large city? Who knows how many people can see your network signal. A 3rd option which I'm using now is MoCA. It uses existing coax TV cables.  Ethernet and the video signal share the same conductor but use different frequencies. 

As far as buying hardware, newer is not necessarily better as was mentioned above. For instance, there's a thread on this forum about Ryzen APUs with integrated graphics that creates a split screen. There's a way around that glitch - use a standalone video card for a while - but it illustrates the risk. There was another problem with motherboards using AMD 970 chipsets where USB3 ports didn't work. A motherboard or at least the chipset that's been around for months would be a safer bet. If it has issues they'll likely be solved or there's a fix/workaround.

---

### Post by him610 on 2018-07-04
On power supplies....
Recommend you make sure your chosen power supply, motherboard, and case are all fit and connector compatible. Also, you might consider a semi-modular power supply - allows you to eliminate unnecessary cables from the inside of your case.

---

### Post by robehickman on 2018-07-05
> **him610 said:**
> Also, you might consider a semi-modular power supply - allows you to eliminate unnecessary cables from the inside of your case.

Agree.

---


---
title: "Help the New Guy Please :)"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by spooter on 2009-01-26
Hi all,

Im new to Linux and Kubuntu.  I have tried it in the past but now I have no choice but to try it after my Windows Vista trial expired and can’t afford to buy a copy.  I have installed this onto my newly built machine and so far im impressed.

**PC Spec**

Antec 300 Three Hundred Case
Akasa AK 860SF
Arctic Power 500W PSU With PCI-E 2x SATA, 20+4 ATX12V 8pin +12V Connectors
MSI 8600GTS 256MB Overclocked Edition Dual DVI HDTV Out PCI-E Graphics Card
Maxtor 500GB Hard Drive SATAII 7200rpm *32MB Cache* - OEM
4Gb DRR 800 
AMD X2 6000 @ 3Ghz
SUS M3N78 GeForce 8200 Socket AM2+ onboard Graphics 8 channel audio ATX Motherboard

**Install**

The install went well for all hardware except the sound but I was happy enough pasting text into the terminal to fix this.  

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

**Games**

The one game I play is counterstrike source so I needed this working so Installed Wine downloaded Steam and installed without problems.  After installing CSS I couldn’t get the game to play with crashing but after changing the game to run in dx 8 and changing the Open GL setting to high in the Nvidia setting panel I got it working.  I haven’t tried playing it much but hopefully it will be stable.

**Questions**

How do I tweak my Counterstrike Source game in wine for best performance or do I just need to accept the FPS isn’t going to be a high?

Are the any tweaks I should apply to a fresh install in Windows I would make quite a few changes.

What antivirus should I install?  Do I need one?

I would often defrag my Windows machine should I defrag this?

I used Firefox on Windows so it made sense to install it on Kubuntu but have noticed the pages don’t load nearly as fast?  Any ideas on resolving this?

Is there a way I can see the start-up apps?  I have a Widget which opens at the start and for some reason its gone funny and can’t see to stop it opening.

Sorry about all the questions but been new I have so many but look forward to converting.

Thanks

---

### Post by Melk79 on 2009-01-26
> 
How do I tweak my Counterstrike Source game in wine for best performance or do I just need to accept the FPS isn’t going to be a high?
Not sure, but my experience is Wine won't get the same performance.

> Are the any tweaks I should apply to a fresh install in Windows I would make quite a few changes.
It depends on your preferences, but many sites are good resources.  If you like eye candy, install Compiz Fusion.  Install the ubuntu-restricted-extras from Synaptic Package Manager for prop. codes, etc. [http://www.funnestra.org/ubuntu/intrepid/](http://www.funnestra.org/ubuntu/intrepid/), [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php), [http://www.stchman.com/](http://www.stchman.com/)
> What antivirus should I install?  Do I need one?
You don't need one generally speaking because you have good odds of not getting a virus in Linux distros, but security is still important.  The links above offer suggestions, when you're more comfortable with Linux I like to use Bastille to tighten up security.
> I would often defrag my Windows machine should I defrag this?
Simple: no. Long version: [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)
> I used Firefox on Windows so it made sense to install it on Kubuntu but have noticed the pages don’t load nearly as fast?  Any ideas on resolving this? Go to about:config in the address bar. Type IPv6 in the filter and change setting to true. Seemed to help me.
> Is there a way I can see the start-up apps?  I have a Widget which opens at the start and for some reason its gone funny and can’t see to stop it opening.System>Preferences>Sessions shows startup programs, but it kind of sound like you have the widget layer turned on with Compiz.  Do you have CompizConfig Settings Manager under System>Preferences?  You can disable there if it is giving you trouble.

---


---
title: "Netgear WG511 Wireless Card Not Working..."
date: 2006-05-15
forum: Hardware &amp; Laptops
---

### Post by ironmagma on 2006-05-15
Hey everybody!

I just installed Ubuntu Breezy as a second boot on this laptop here, but it doesn't seem to want to support my Netgear WG511 bus card.  I've tried enabling it with ifconfig, but no luck.  Any ideas?

The device itself is displayed in the device manager, but it doesn't even light up (on the actual device).  :-/

Edit: it works fine with windows... :-S  thanks in advance! :D

---

### Post by slightly72 on 2006-05-15
Don't have a good solution, but maybe there's no driver loaded for the device, even if it's displayed in Device Manager (take a look for the string info.linux.driver in the advanced tab). If there's no driver loaded, you might want to try using ndiswrapper, it's listed as working with it. I'm thinking that people would not try ndiswrapper if there would be a native linux driver for it. You can find instructions for using ndiswrapper in the ubuntu wiki.

---

### Post by dm64 on 2006-05-16
[QUOTE=ironmagma]Hey everybody!

I just installed Ubuntu Breezy as a second boot on this laptop here, but it doesn't seem to want to support my Netgear WG511 bus card.  I've tried enabling it with ifconfig, but no luck.  Any ideas?

The device itself is displayed in the device manager, but it doesn't even light up (on the actual device).  :-/

Edit: it works fine with windows... :-S  thanks in advance! :D[/QUOTE]

Hi there
After a week of banging my head against the nearest wall (and being a complete Linux noobie) this post was my saviour!

[http://ubuntuforums.org/archive/index.php/t-76804.html]("http://http://ubuntuforums.org/archive/index.php/t-76804.html")

I followed all steps in the top post (first got all of the drivers an transferred them to the laptop via CD) and it worked perfectly.

Hope that helps!

---

### Post by AndrewB on 2006-05-16
I'm using this card in my Gateway.

Open a terminal, and try the following:
> sudo su <enter>
modprobe ath_pci <enter>
iwconfig ath0 essid "your network name" key ''your WEP hex, without quotes" mode managed<enter>
pump -i ath0


For me works like a charm.

---

### Post by AndrewB on 2006-05-21
>  sudo su <enter>
modprobe ath_pci <enter>
iwconfig ath0 essid "your network name" key ''your WEP hex, without quotes" mode managed<enter>
pump -i ath0

my bad, Try this
[COLOR="Red"]sudo su <enter>
modprobe ath_pci <enter>
iwconfig ath0 mode Managed
iwconfig ath0 essid "your network name"<enter>
iwconfig key ''your WEP hex, without quotes" <enter>
**ifconfig ath0 up**<enter>[/COLOR]

it's the small differences between distro's that gets me ;)

---

### Post by ironmagma on 2006-05-27
Hi again!  Sorry for being so late to reply to this thread 8-[


> 
Hi there
After a week of banging my head against the nearest wall (and being a complete Linux noobie) this post was my saviour!

[http://ubuntuforums.org/archive/index.php/t-76804.html](http://ubuntuforums.org/archive/index.php/t-76804.html)

I followed all steps in the top post (first got all of the drivers an transferred them to the laptop via CD) and it worked perfectly.

Hope that helps!



Hmm, I did all that and still no results (well, at least that I know the driver is installed now.  ndiswrapper -l  gives me an accurate status of my driver ("Driver installed.  Hardware present.") and detects when the hardware is not present.

But still one thing gets me: how do I start it up?

I've tried up'ing it with ifconfig, but I get something like

SICOCSIFFLAGS: Timer expired.

or something to that effect (I think i misspelled the first word).

The lights on the card haven't even turned on yet (they work in Windows, fine, though). Got any suggestions?

Also: what is an ESSID? Is it the same as an SSID (network name)?

and AndrewB: what do I put for my WEP key if I have none? (I know, I know, but I'd like to keep it as nothing just until I can actually get the thing working.  I don't think it's as much the communication configuration as other stuff.)

[QUOTE=AndrewB]my bad, Try this
[COLOR="Red"]sudo su <enter>
modprobe ath_pci <enter>
iwconfig ath0 mode Managed
iwconfig ath0 essid "your network name"<enter>
iwconfig key ''your WEP hex, without quotes" <enter>
**ifconfig ath0 up**<enter>[/COLOR]

it's the small differences between distro's that gets me ;)[/QUOTE]

---

### Post by kmoffat on 2006-05-27
I have an older wg511, and all I had to do was load prism54 using:

modprobe prism54

then use the network config dialog under System/Administration/Network

However, not all wg511 cards use the prism chip.

---

### Post by ironmagma on 2006-05-27
Hmm still not working. :-/

---


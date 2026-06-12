---
title: "Intrepid: Wireless won't reconnect from Hibernation or Suspend"
date: 2008-11-02
forum: Hardware
---

### Post by timsan on 2008-11-02
Hello, 

Just upgraded to Intrepid since my Hardy was crashing (mostly on the mplayer-mozilla plugin). 

All is working fine, though, one big problem is after switching on from hibernation or suspend mode, the wireless won't reconnect. This worked fine in Hardy. 

In Hardy, the hibernation did show me an error message and in Intrepid I receive no error messages (it seems much improved), though, my wireless won't reconnect. 

The only solution is to reboot. 

Thus, do I need to change anything? Or should I file a bug report? I noticed as well that wifi-radar won't work anymore in Intrepid.

timsan

laptop: Dell D610/Netgear pcm card (ath chip)

---

### Post by Ambiguity on 2008-11-02
I am having the exact same issue. This was not a problem till upgrading to Intrepid. I also have an Atheros wifi card.

lspci:
06:04.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

I found a bug report that seems to be for this exact issue:
[https://bugs.launchpad.net/ubuntu/+bug/292032](https://bugs.launchpad.net/ubuntu/+bug/292032)

This bug report sounds the same as well, it is older but there are more discussions:
[https://bugs.launchpad.net/ubuntu/+bug/282263](https://bugs.launchpad.net/ubuntu/+bug/282263)
which is a duplicate of:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/272300](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/272300)

Seems to be an issue with madwifi. The last bug report has a few solutions that seem to have worked for some. I will try these later.

---

### Post by Ambiguity on 2008-11-02
Typing "sudo iwconfig ath0 up" enables it for me after resume.

---

### Post by farhill on 2008-11-02
This item in the release notes may also help
[http://www.ubuntu.com/getubuntu/releasenotes/810#Wireless%20doesn%27t%20work%20after%20suspend%20with%20ath_pci%20driver](http://www.ubuntu.com/getubuntu/releasenotes/810#Wireless%20doesn%27t%20work%20after%20suspend%20with%20ath_pci%20driver)

---

### Post by timsan on 2008-11-02
hello, 

Thanks a lot for the links, I should have looked in the bug reports in the first place!

I had to make a few simple additions to a few files as stated in the bug reports. It seemed that wifi0 goes down and doesn't come back up after the laptop is awoken. 

It worked after the suspend, I'll need to try it with hibernating too (I feel it should work too).

ta! 


> **Ambiguity said:**
> I am having the exact same issue. This was not a problem till upgrading to Intrepid. I also have an Atheros wifi card.

lspci:
06:04.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

I found a bug report that seems to be for this exact issue:
[https://bugs.launchpad.net/ubuntu/+bug/292032](https://bugs.launchpad.net/ubuntu/+bug/292032)

This bug report sounds the same as well, it is older but there are more discussions:
[https://bugs.launchpad.net/ubuntu/+bug/282263](https://bugs.launchpad.net/ubuntu/+bug/282263)
which is a duplicate of:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/272300](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/272300)

Seems to be an issue with madwifi. The last bug report has a few solutions that seem to have worked for some. I will try these later.

---

### Post by Mic_Droz on 2008-11-10
I'm having a similar issue, but ony after upgrading my Hardy Kernel - i'm still on Hardy now - this is pissing me off greatly, because the other kernel's worked fine with suspend and resume - would adding the line to /etc/pm/config.d/madwifi in Hardy work just as well? Or will it result in a downward spiral that somehow ends with the destruction of the earh?

Oh yeah, and after resume, the little light that tells me that bluetooth is on sometimes comes on - which is quite odd seeing as I don't have bluetooth on my laptop (Acer aspire 3620)?

Cheers and Beers

---

### Post by mtinman on 2008-11-26
> **farhill said:**
> This item in the release notes may also help
[http://www.ubuntu.com/getubuntu/releasenotes/810#Wireless%20doesn%27t%20work%20after%20suspend%20with%20ath_pci%20driver](http://www.ubuntu.com/getubuntu/releasenotes/810#Wireless%20doesn%27t%20work%20after%20suspend%20with%20ath_pci%20driver)
Farhill, I used your advice, and that fixed my problem Thanks.

---

### Post by VanHammersly on 2009-02-04
This solution also worked for me on my MacBook Pro, first generation.  I am using the proprietary ati driver and using the script listed by farhill to have suspend working perfectly.

---


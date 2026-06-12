---
title: "Broadcom BCM4311 on Dell Vostro 1500."
date: 2015-04-10
forum: Hardware
---

### Post by someone7 on 2015-04-10
Hello. I have been running Linux on my Dell Vostro 1500 for awhile. Back on a much earlier version of Ubuntu, my computer ran fine with no problems (10.04 Lucid Lynx). After leaving 10.04, after there was no more support for it, I switched to another LTS Ubuntu, and then to Linux Mint. Ever since, I have been having problems. I usually need to hard-restart my computer after only an hour or so of use, when I used to leave it on for weeks at a time. I thought I might have had a memory issue, but the memtest reveals nothing wrong.

I eventually got it in my head that it must have been something wrong with the drivers for my wireless card. Back on 10.04, I just used the proprietary drivers that the manufacturer made for it (the Broadcom STA wireless driver). If I remember correctly, there was a kernal update to Linux that broke this driver, and it no longer worked, so everyone had to start using the open-source one (the b43 driver). I have had trouble with this computer ever since using the open-source driver, and no amount of directions can seem to solve the problem of needing to hard-restart the computer ever couple of hours. This has been going on for about 2 years now.

The last thing I tried was using the NDISwrapper with the Windows drivers, but for some reason, Linux just never recognized it. "sudo modprobe" commands did nothing to make Linux start using the NDISwrapper. I installed the graphical frontend for it, ndisgtk, and it says that the bcmwl5 windows driver is installed, but switching to it with "sudo modprobe" commands does nothing but make me lose wireless, until I switch back to the b43 driver that makes my computer crash every few hours.

Any helps appreciated. At this point, I am ready to chuck this computer and buy something new that is compatible with the latest versions of the Linux kernal.

---

### Post by weatherman2 on 2015-04-10
I suspect you may have several, unrelated issues.

First of all, the Vostro 1500 is a few years old.  I had a 1510 for a while and that would now be old too.  These old laptops often get dirty inside, and the CPU heat sink and fan can get clogged with dust and dirt, causing the laptops to overheat and shut down.  I've cleaned out a number of them, and the cooling improvement can be dramatic.

Some Dell laptops have easy access to the CPU and heat sink.  Some are accessible via a panel on the bottom of the laptop.  Others require you to remove the keyboard so a little more involved.  But you can probably find info online on how to do this, if you are interested in trying it yourself.  Dell probably has a service manual online showing you exactly how to do it.  Or search the web for "vostro 1500 teardown" or on YouTube.  Someone may already have a video for the 1500 showing exactly how to do it.  Maybe it's not that hard.

But you'd want to remove the copper heat sink with the fins and blow out all the dust.

As for the wireless card: you shouldn't want/need to use ndiswrapper - only as an absolute last resort.  This is an old wireless card; even if there's still no good open source driver, you should still have the option for a proprietary driver that should work reliably by now.

Even so, replacing the wireless card should be pretty easy.  I know I replaced the wireless card in my 1510 with an Intel card that was automatically supported.  When you explore cleaning out the laptop as described above, you will also probably see how to access the wireless card.  It's generally in a little slot secured with one screw or a few clips.  There are two or three antenna wires clipped on to it; just pop them off and remove the card and plop a new one in.  Intel cards can be had on eBay used for as little as $10 USD.

I think the 1510 had a full-sized mini-PCI card.  The 1500 probably does too (easy to verify online).  I'd recommend an Intel 5100 for it - but get the "full sized" card not the "half sized."  Also, make sure you DO NOT get the Lenovo/IBM/HP version of the 5100.  You don't even need the "Dell" version - a Toshiba or Acer version of the card should work just fine.  Get a used card not a "new" one from Asia - I have had bad luck with engineering samples sold from Asia as "new."  All of the used cards I've bought on eBay have worked fine.

The Intel 5100 is an 802.11n dual band wireless card as well, so probably an upgrade from the 802.11g card in there now!

---

### Post by dora5 on 2015-04-11
Will this solution work for my 
[FONT=system][SIZE=1][COLOR=#000000]Broadcom Corporation BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver  Dell Wireless 1470 Dua Band WLAN MIni-PCI?[/COLOR][/SIZE][/FONT]   I believe it's full size.  Trouble is, there's real variety in mini-PCI cards.

I'd like it to be both easier to use and easier to connect to public networks such as on the bus and in a hospital.

I don't believe those cards came in anything more advanced than g.   

Thanks!

Dora

---

### Post by weatherman2 on 2015-04-11
> **dora5 said:**
> Will this solution work for my 
[FONT=system][SIZE=1][COLOR=#000000]Broadcom Corporation BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver  Dell Wireless 1470 Dua Band WLAN MIni-PCI?[/COLOR][/SIZE][/FONT]   I believe it's full size.  Trouble is, there's real variety in mini-PCI cards.

I'd like it to be both easier to use and easier to connect to public networks such as on the bus and in a hospital.

I don't believe those cards came in anything more advanced than g.

Right, your card is older than the one in the Vostro 1500.  It's larger than the "full size" Intel 5100 card I was talking about - it's wider too.  An older style of mini-PCI card:

[https://wikidevi.com/wiki/Dell_Wireless_1470_Dual-Band_WLAN_miniPCI_Card](https://wikidevi.com/wiki/Dell_Wireless_1470_Dual-Band_WLAN_miniPCI_Card)

And you're right: upgrade options for that form factor are limited.  There may be an 802.11n card available for that form factor but I am not aware of any.

---

### Post by someone7 on 2015-04-18
> **weatherman2 said:**
> First of all, the Vostro 1500 is a few years old.  I had a 1510 for a while and that would now be old too.  These old laptops often get dirty inside, and the CPU heat sink and fan can get clogged with dust and dirt, causing the laptops to overheat and shut down.  I've cleaned out a number of them, and the cooling improvement can be dramatic.

Well, my computer doesn't seem to be overheating (it doesn't feel hot), nor does it shut down on its own. It merely freezes until I hard-reset it. Nevertheless, it wouldn't hurt to try it.

> As for the wireless card: you shouldn't want/need to use ndiswrapper - only as an absolute last resort.  This is an old wireless card; even if there's still no good open source driver, you should still have the option for a proprietary driver that should work reliably by now.

The proprietary driver no longer works. The STA driver became non-functional after various changes in the Linux kernal. That is when I started experiencing problems with this computer.

> I think the 1510 had a full-sized mini-PCI card.  The 1500 probably does too (easy to verify online).  I'd recommend an Intel 5100 for it - but get the "full sized" card not the "half sized."  Also, make sure you DO NOT get the Lenovo/IBM/HP version of the 5100.  You don't even need the "Dell" version - a Toshiba or Acer version of the card should work just fine.  Get a used card not a "new" one from Asia - I have had bad luck with engineering samples sold from Asia as "new."  All of the used cards I've bought on eBay have worked fine.

I'm gonna try this, and if it doesn't work, I'll just buy another computer. Playing around trying to get ndiswrapper working with the Windows Broadcom drivers has pushed the limits of my patience.

---

### Post by someone7 on 2015-04-18
Just bought this:

[http://www.ebay.com/itm/Intel-Wifi-Link-5300-533AN-MMW-wireless-WiFi-PCI-E-card-802-11N-AGN-full-height-/201105629799?pt=LH_DefaultDomain_0&hash=item2ed2d46267](http://www.ebay.com/itm/Intel-Wifi-Link-5300-533AN-MMW-wireless-WiFi-PCI-E-card-802-11N-AGN-full-height-/201105629799?pt=LH_DefaultDomain_0&hash=item2ed2d46267)

Hopefully when it arrives, this will solve the issue. I'll report back with the results, and hopefully anyone still attempting to get their Broadcom cards working correctly in Linux can just throw them in the trash.

---

### Post by weatherman2 on 2015-04-18
> **someone7 said:**
> Just bought this:

[http://www.ebay.com/itm/Intel-Wifi-Link-5300-533AN-MMW-wireless-WiFi-PCI-E-card-802-11N-AGN-full-height-/201105629799?pt=LH_DefaultDomain_0&hash=item2ed2d46267](http://www.ebay.com/itm/Intel-Wifi-Link-5300-533AN-MMW-wireless-WiFi-PCI-E-card-802-11N-AGN-full-height-/201105629799?pt=LH_DefaultDomain_0&hash=item2ed2d46267)

Hopefully when it arrives, this will solve the issue. I'll report back with the results, and hopefully anyone still attempting to get their Broadcom cards working correctly in Linux can just throw them in the trash.

It may work, but your Vostro has only two antenna wires I think (is there a third one dangling in there, taped?).  I seem to think the 1510 had three wires but the original card used only two of them.  The Intel 5300 card has three antenna wire ports.  You can leave a wire off if you have only two, or you can try to attach a third wire on your own.

Also, as I said, I wouldn't have bought one from Asia.  I bought several "new" Intel wireless cards from eBay vendors in China, and they seemed to be engineering samples, mismarked as the wrong card, etc.  I have had great luck with used cards bought in the US.  Oh, well - hope it works for you.  Good luck!

---


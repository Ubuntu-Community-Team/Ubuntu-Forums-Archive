---
title: "Setting up the HP Laserjet MFP M175nw on Ubuntu / Linux (with wifi)"
date: 2013-12-13
forum: Hardware
---

### Post by lodp2 on 2013-12-13
I'm writing this so it'll turn up on search engines if somebody has the problem I had. So this is more like a blog post.

Unlike most other HP multi-function printers, the HP Laserjet pr 100 MFP M175nw's network functionality [is not officially supported]("http://hplipopensource.com/hplip-web/models/color_laserjet/hp_laserjet_100_colormfp_m175b.html"). It's weird, because **both printing and scanning works out of the box** on a wired network, and the wifi is quite easy to set up as well. 

But HP didn't bother to document it, prescribing instead a procedure with a temporary USB connection and its Windows-only driver CD.

You don't need that at all. Here's how you do it:

1. If your wifi-AP or router has a WPS button, you can probably just follow the manual. I haven't tried that.

2. If your wifi doesn't have WPS (like mine), first plug the printer into your router/ap with an ethernet cable.

3. Wait 20 sec or so, and the printer will show you its IP Adress (it alternates with the toner info every cpl. of seconds)

4. Put that IP into your computer's browser (has to be on the same network), which will get you to the printer's web interface. Navigate to Network > Wireless Configuration (or equivalent).

5. Make sure wireless is set to ON, select your wifi out of the list and enter your password etc. I actually had to type in the wifi name instead, otherwise the password wouldn't stick. But maybe that's just me.

6. Hit "Apply" and you should be done. Now,** the printer won't connect to the wifi unless you pull the ethernet plug**, and after that it may take a minute to connect (during which the wifi button will flash blue). Once you're connected, the wifi button turns to steady blue, and the display will show the printer's new IP address.

Having established the wifi connection, you can proceed to set up the printer with HP's own HPLIP toolbox, and printing / scanning on the network should work like a charm.

---

### Post by mrsfixit on 2013-12-14
This is good to know. Thanks for posting.

I am running Xubuntu 13.04, and I am tearing my hair out trying to find a laser printer that will work pretty much OOTB.

I looked at Brother, but the driver installation seems dodgy and way too complicated.

Your tutorial seems easy and straighforward, which means I can add the Laserjet MFP M175nw to my shortlist of machines that are known to work under Ubuntu. :-)

---

### Post by lodp2 on 2013-12-15
I don't know about Brother, but as for HP, it seems to me pretty much all their printers are officially supported on Linux / Ubuntu. Their own official printer control application HPLIP is in the Ubuntu repositories. They even have a list of printers recommended for Linux, with information about support level in certain distros, even down to the specific distro version: [http://hplipopensource.com/hplip-web/recommended.html](http://hplipopensource.com/hplip-web/recommended.html)

So no need to pull your hair out :) just get any HP printer off the recommended list, and they will work pretty much out of the box. If you install the "hplip-gui" package, even setting it up will be easy (with HPLIP toolbox).

I don't know about other manufacturers, but HP's support for printers in Linux is awesome.

---

### Post by mrsfixit on 2013-12-15
> **lodp2 said:**
> I don't know about Brother, but as for HP, it seems to me pretty much all their printers are officially supported on Linux / Ubuntu. Their own official printer control application HPLIP is in the Ubuntu repositories. They even have a list of printers recommended for Linux, with information about support level in certain distros, even down to the specific distro version: [http://hplipopensource.com/hplip-web/recommended.html](http://hplipopensource.com/hplip-web/recommended.html)

So no need to pull your hair out :) just get any HP printer off the recommended list, and they will work pretty much out of the box. If you install the "hplip-gui" package, even setting it up will be easy (with HPLIP toolbox).

I don't know about other manufacturers, but HP's support for printers in Linux is awesome.

I know. I currently have an HP Officejet 6500 but the damn thing is bankrupting me with ink costs. That's why I'm looking to switch to a laser.

I have HPLIP installed and I've never had an issue with any HP- inkjet, anyway.

Brother is supposedly well supported but getting their drivers to work is a bit of a chore. The thing about Brother is that the cost of the toner is half of what the HP toner costs. I find the toner costs for HP very high, with a low output per cartridge.

I'm doing my homework now, and will find something I know will work *before* I buy it.

Maybe that will save the rest of my hair... LOL :-)

---

### Post by lodp2 on 2013-12-15
I've been using off-brand toner with my HP printers for the past 15 years. Occasionally you will get one with bad quality, but right now I'm very satisfied with the one I got for my HP 2015 Laserjet. It cost about a quarter of the original toner (&#8364;16 vs. &#8364;57), and you can hardly spot the difference to the original.

---

### Post by mrsfixit on 2013-12-15
> **lodp2 said:**
> I've been using off-brand toner with my HP printers for the past 15 years. Occasionally you will get one with bad quality, but right now I'm very satisfied with the one I got for my HP 2015 Laserjet. It cost about a quarter of the original toner (€16 vs. €57), and you can hardly spot the difference to the original.

Hmmm, I didn't consider that as an option. I know the recent inkjets like mine with the chipped cartridges have issies with being refilled.

But if I could find a reliable source for aftermarket toner that would definitely swing me towards HP again...

It's just obscene what they charge for this stuff, don't you think?

---


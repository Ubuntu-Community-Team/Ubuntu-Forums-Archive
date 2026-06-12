---
title: "No connection with Linksys WPC54GS ver 2 wireless card"
date: 2008-11-10
forum: Hardware
---

### Post by MawcDrums on 2008-11-10
I've seen a few threads on this, but all are old and seemingly outdated (as I tried the fixes and they didn't work.)

There are no wireless networks recognized at all, (this will only be a problem for another month or so because I'm getting a new laptop for christmas)and it doesn't show my card as a device in the network manager

I plugged in my laptop to my router directly and it connected right away.

I realize you guys probably want to see what the story is when I pull the info in the Terminal, however I'm at work and dont have my laptop with me..

It did find it, however it gave me the ESSID= "" thing, and according to the directions in the help files: "If there is an entry that says ESSID="" then see the section called &#8220;Configuring WPA support.&#8221;."

So we click on Configuring WPA support, and it says Wireless network security

Configuring WPA support.
WiFi Protected Access (WPA) is an based on WEP and provides stronger security.

WPA is integrated with Network Manager. You must also have the wpasupplicant package installed.

If you need to manually configure WPA support, see the Wiki Entry.


SO we go to the wiki, and everything is for version 6.06 or 6.10.

I know some people have posted fixes with ndiswrapper and such, and I tried that to no avail.

Any hints?:confused::confused:

---

### Post by ampron on 2008-11-11
I have also had troubles getting Ubuntu to work with that card. I plug in the card and nothing, when I have gotten something with older versions of Ubuntu I have to download the drivers, but don't have a connection because of course the wireless card isn't working. Any ideas?

---

### Post by ampron on 2008-11-11
I got the card to work. I went to this page, [http://ubuntu.cafuego.net/dists/intrepid-cafuego/broadcom/]("http://ubuntu.cafuego.net/dists/intrepid-cafuego/broadcom/"), and ran the .deb package. I restarted with the card plugged in and it was working.

---

### Post by novellahub on 2009-02-04
> **ampron said:**
> I got the card to work. I went to this page, [http://ubuntu.cafuego.net/dists/intrepid-cafuego/broadcom/]("http://ubuntu.cafuego.net/dists/intrepid-cafuego/broadcom/"), and ran the .deb package. I restarted with the card plugged in and it was working.

Thanks for posting these directions.  It works great!

---


---
title: "Aspire One + Ubuntu = No Wireless"
date: 2008-12-03
forum: Hardware
---

### Post by itayl2 on 2008-12-03
Hi,


I've gotten tired of Windows recently and decided to turn to Linux.

I installed Ubuntu 8.1, and since then - no wireless.

I have the Atheros AR50007 (I think) - and just no luck.  I have absolutely no knowledge concerning ubuntu, so obviously things are not easy for me... :\

I've tried the various guides regarding madwifi and ndiswrapper, with no luck... I can currently see the wireless networks, but cannot connect to any of them.

Anyone? I'm hopeless... :\

If you do bother and help me (please? :) ), please be specific and detailed because I truly am completely new in this environment...


Thanks so much in advanced.

---

### Post by the3dman on 2008-12-03
I dont know what guides you tried for ndiswrapper already but this is how I did my acer.

First connect to a wired network. You can use the add/remove apps to download and install the program ndiswrapper then download the windows xp drivers and (extract the zip to your desktop) for your card from Acer. Then use the ndiswrapper tool you installed (which will now be in your system menus somewhere) to select the .inf file from those drivers, and hopefully that will work for you.

As far as why you cannot connect I am unsure sorry.

---

### Post by bushd on 2008-12-03
In order to verify what wireless card you're using in terminal:
lshw -C network

That will atleast let you know if the card is even being recognized.

What type of network are you trying to connect to - WPA2 Personal, Enterprise, WPA, WEP, etc.  I know nm-applet, the typical gui you seen on intrepid install, atleast for me, will not connect to WPA2 Ent PEAP networks.  It would hose the computer every time it was authenticated.

Try to update your install through a wired network like previously mentioned.  If that has nm-applet not connecting still your next method may be using wpa_supplicant with wext.  I use NDIS for nm-applet but for some reason I can only make wext work for wpa_supplicant.

NDIS can be installed through Synaptic I believe.  All you need to do is find the windows version of your .sys file from the driver zip you downloaded for it.  I pointed the NDISWrapper gui to that file and it worked like a charm.  Then I had to go through the trouble of making NDIS become the driver.  I know there is a tutorial on that around here somewhere.  If NDIS is actually installed and running on that lshw -C network terminal command you'll see "configuration: broadcast=X driver=ndiswrapper+Y" on the last line of the Wireless interface network entry.

---

### Post by renoturx on 2008-12-03
Hey, I can't remember which thread had it, but some one suggested deactivating support for Atheros 802.11 wireless in "System->Administration->Hardware drivers", then using synaptic to load "linux-backports-modules-intrepid-generic" once loaded restart.
I have an Aspire one running Ibex, have tried this and it works. no need for ndis or mad wifi..
I was able so successfully connect using an open network.

Support for 5xxx series of Atheros 802.11 wireless becomes active upon reboot this is what lets you connect. Don't deactivate it.

---

### Post by itayl2 on 2008-12-04
Thanks for all the replies!

Will try today to install the xp drivers like two of you have suggested... I think all the networks I've been trying to connect to were WPA2 so maybe that was part of the reason...

now.... when you say "making wext work for wpa_supplicant" - I have no idea what that means :)

Sorry, really clueless to linux... think of me as a grandmother logging into XP :)


will try the xp thing today and probably get back here for more idiotic questions! :)

---

### Post by andreasis on 2008-12-04
itayl2, welcome to the forum!

I have an Aspire One too, and I've been through what you've been through.

Firstly I'd like to congratulate you on making the switch. I'd like to give you my sincere opinion that Ubuntu Hardy works much faster than Intrepid and I find it to be much more reliable on the Aspire One as well.

To get everything working smoothly, I followed this guide: [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

If you are still set on keeping Intrepid, follow one of the following guides:

[https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One](https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One)

or the more updated

[https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)


Please note that Ubuntu Hardy is a LTS (long term support) release, and Ubuntu will support it until April 2011, as opposed to Intrepid, which Ubuntu will only support until April 2010.

Let me know how else I can help... my Aspire One's up and running flawlessly and fast, and it would definitely be cool if we can get yours up and running to its full potential too.

---


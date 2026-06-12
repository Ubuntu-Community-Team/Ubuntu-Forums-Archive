---
title: "another wireless issue."
date: 2008-08-15
forum: General Help
---

### Post by jackechanprime on 2008-08-15
i have a Compaq Presario C700 with an Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter. i've downloaded ndiswrapper to run the windows driver.the computer can connect to the internet just fine over wireless, its just that it freezes after a minute or two, seemingly randomly.

---

### Post by jackechanprime on 2008-08-16
bump

---

### Post by jackechanprime on 2008-08-16
bump, again. someone plz help.:(

---

### Post by jackechanprime on 2008-08-17
bump.

---

### Post by jackechanprime on 2008-08-17
sorry, i may have been a bit ambiguous there.

my origional message;

*'i have a Compaq Presario C700 with an Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter. i've downloaded ndiswrapper to run the windows driver.the computer can connect to the internet just fine over wireless, its just that it freezes after a minute or two, seemingly randomly.'*

i'd like to expound on that. there was a bit of dramma downloading the driver. we tried madwifi, but the .tar file was empty, so we tried about 3 other things, which may or may not still be installed, i'm not sure, none of which seemed to work in any way shape of form. Eventually we downloaded ndiswrapper and thanks to that the wireless card started functioning, but at the same time, the computer began crashing without fail, almost promptly after booting. for some reason, plugging in the eathernet cable stops this. my friend says theres something wrong with the driver, or that theyre conflicting or something. whatever the problem actually is, this is really hampering the function of my computer. plz, anyone help.

---

### Post by jackechanprime on 2008-08-18
bump

---

### Post by dingansich on 2008-08-18
I'm hardly an expert on these matters, but I went through a lot of trouble getting WiFi working reliably on my setup so I'll tell you what worked for me.

First, I had more success with the atheros wifi chipset than the ralink chipset.  (Those are the only 2 I've tried.)  I currently have an atheros based D-Link PCI adapter (dwa-1320 I think) working very nicely.

Second, I tried ndiswrapper, and had stability issues with it after it was 'working' (ie. my connection would die for no reason).  I only used ndiswrapper to get my old ralink adapter working.  For the atheros chipset madwifi worked just fine.  I do recall blacklisting a number of modules when I was setting ndiswrapper up - specifically the native driver modules for my card.  Maybe this is what is causing your problem?

Third, I use Wicd rather than the default network manager.  I don't see how this could make a difference as far as stability is concerned, but I find it a better way to manage my connection.

So in a nutshell - and again I'm no expert - my feeling is that you should try sticking to madwifi (which was 'just there' for me ... I didn't have to download anything in Hardy - it seems to be included in the linux-restricted-modules package), and use Wicd to manage the interface.  If you're going to stick with ndiswrapper, maybe look into this blacklisting issue.  Maybe I'm remembering things incorrectly, but I think you need to prevent the native linux module from loading, otherwise you end up with two drivers fighting for the same hardware ... or so I assume.

Sorry I can't be of more help.

---

### Post by jackechanprime on 2008-08-18
hmm. thx. i'll look into it in a moment. however i think i have a bunch of drivers blacklisted already. i don't know how to check. i'm kinda leaning on a friend on this one, but hes really busy, so i'm looking around for help. thx again, and i'll b right back with more info on if this has anything to do with the price of tea in china.

---

### Post by dingansich on 2008-08-19
Check this file: /etc/modprobe.d/blacklist  to see what you have blacklisted.

edit: Maybe take a look at this thread: [http://ubuntuforums.org/showthread.php?t=814879](http://ubuntuforums.org/showthread.php?t=814879) About 2/3 the way down the page there's someone that lists how they managed to get madwifi working on their machine.

---


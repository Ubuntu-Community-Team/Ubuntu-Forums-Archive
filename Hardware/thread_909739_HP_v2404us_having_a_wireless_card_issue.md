---
title: "HP v2404us having a wireless card issue?"
date: 2008-09-03
forum: Hardware
---

### Post by tapper1999 on 2008-09-03
I would like to start off by saying that I am a total noob with linux.

Recently I have decided that I would like to leave the extremely wrong world of Microsoft and gain entry into the free world of open source. :)

I have downloaded Ubuntu and proceeded to install it on an HP v2404us model laptop.  The installation has went extremely well and with all but one hitch.

The wireless card is recognized by the system however the button to enable the wireless card does not turn on.  The BIOS of the machine does state that the card is enabled.

I have searched high and low for help with this issue and the results have been kind of mixed.  One result states that the driver should work perfectly under 8.04 and another states that i need to reload linux after activating the card under windows using a wireless assistance application.

I have changed out the hard drive with one that had windows installed on it and have used the wireless assistant application.  However when I replace the drive and reinstall linux to it, I still have the same problem.

Can someone please help assist me with this problem?


[INDENT][B][I]I happened to resolve this issue by connecting the laptop to a wired internet connection.  I the proceeded to download all system updates.  After a reboot of the system I went ahead and opened the restricted drivers notification.  To my surprise there are three drivers:  ATI video, the built-in modem, and the BCM43XX wireless card.

Now that these drivers are installed the wireless light is on and I can connect to wireless networks now :)

SIDE NOTE:  Before the new driver was installed I was able to see wireless connection when the laptop was placed right next to a wireless router; however a connection could not be established. [/I][/B][/INDENT]

---


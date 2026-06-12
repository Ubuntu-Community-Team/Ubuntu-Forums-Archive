---
title: "Help - Don't know how to turn wireless on"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by davidmorgen on 2009-08-14
I just installed Ubunto 9.04.  My wireless does not seem to be turned on.  I typed a command in the terminal server: iwconfig, and it says no wireless extensions.  I also typed lspci and network 0, which shows up as wireless interface, is disabled.  It does not describe the card under wireless but above, under network controller, it says Broadcom, and BCM4306 Wirless LAN controller.  

What do I need to do?  Install a driver?  If so, I don't even know how to do that.  

Please help!

THANKS!:popcorn:

---

### Post by raymondh on 2009-08-14
1.  Check if the wifi switch is on ... if you do have a wifi switch. In some laptops, it'll be in front of the machine or at it's side.  In an HP, you double tap the wifi icon (upper right) until it turns blue. it may also be a FN key like my MSI.
2.  Go to system > administration > hardware drivers and install drivers.

---

### Post by davidmorgen on 2009-08-14
Raymond, thanks for your reply.  I do have a WIFI button, which, when I pressed it before I installed UBUNTU, would turn blue and it would enable WIFI.  Now, when I press it, the light above the button does not turn blue.  Any ideas?

---

### Post by raymondh on 2009-08-14
David,

Ok...more "let's make sure" as I research/google your card

See the wifi icon on your top right?  Make sure (rt. click) that both boxes (wireless/networking) are enabled.  Also, (lf. click), do you see your network?

have you gone through this links from the network/wireless sub-forum?

[http://ubuntuforums.org/showthread.php?t=1176117](http://ubuntuforums.org/showthread.php?t=1176117)
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

You may want to post there hoping that the wifi gurus have an instant fix.  I'll follow your thread and post in should I find something.... if you decide to move your post there.

---

### Post by davidmorgen on 2009-08-14
Thanks Raymond.  The networking and wireless boxes are checked.  If I left click on the wireless icon, Wired Network and Wireless networks are greyed out.  Could this just be a missing driver issue, and that I need to install the correct driver?  Am sort of clueless here.   I will check the wireless subforum, thanks.

---

### Post by Mark Phelps on 2009-08-16
> **davidmorgen said:**
> Raymond, thanks for your reply.  I do have a WIFI button, which, when I pressed it before I installed UBUNTU, would turn blue and it would enable WIFI.  Now, when I press it, the light above the button does not turn blue.  Any ideas?

That's probably going to continue to remain a problem.  I have two laptops, a Compaq and an HP, and both exhibit the same problem.  IN MS Windows, a blue light comes on somewhere on the laptop to indicate that wireless has been enabled.  In Ubuntu, the enabling switches still work, but there is no blue light.

---

### Post by raymondh on 2009-08-16
> **davidmorgen said:**
> Thanks Raymond.  The networking and wireless boxes are checked.  If I left click on the wireless icon, Wired Network and Wireless networks are greyed out.  Could this just be a missing driver issue, and that I need to install the correct driver?  Am sort of clueless here.   I will check the wireless subforum, thanks.

David,

Are you able to connect via ethernet (cable).  If yes, do so and try to update your drivers.

Some members have resorted to [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") ... using the windows-based driver.

Update first .... then browse the manufacturer's website (of your card) to see if they have a linux driver for download ..... and then try ndiswrapper.

Good luck.

---


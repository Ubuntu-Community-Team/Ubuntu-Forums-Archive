---
title: "Acer Aspire 5102 and some I hope usual problems."
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by Gravesent on 2007-05-22
I'm new to Ubuntu, as a matter of fact I'm new to linux, I recently installed Ubuntu on my Acer Aspire 5102 laptop and I have these problems:

- wireless lan is misteriously not working, in the restricted driver manager I see my Atheros wireless card installed and in use but I have no posibility to connect to wireless networks, I understand that when in the radious of a wireless network a network icon is soposed to appear near the clock in the top right corner but the only networks I see there are my dialup modem and my regular lan network...

- desktop effects won't go, I installed the restricted driver for my radeon xpress x1100 card and at first I got a wierd error: Composite Extension not available (I think) I folowed a thread and managed to edit my xorg.conf file at the end like this:

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

The result of this was that the interface for starting desktop effects works now but they still can't be enabled, the error goes something like:

Desktop effects could not be be enabled (I remanber the "be be" part specificly :) )



What can I do?

---

### Post by the_saint07 on 2007-06-11
Hi, 

I have a Acer Aspire 5102WLMi and Fiesty Fawn on it. 
To solve the video card problem I followed the this guide:
[http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty](http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty)

Regarding the wireless, i have had a couple of problems but none of them permantent. Try to disable your wired card when using the wireless one.

Hope it helps.

---

### Post by radiobuzzer on 2007-12-25
Wireless works fine with me.

But there are more disappointing problems with this laptop:
- Until Ubuntu Feisty, the left speaker was not working by default. You could enable it after boot.
- Webcam is not supported and there are no drivers around
- Cannot have the MicroCard automounted (I haven't spent any time, it just didn't automount when I plugged in a card).
- The modem needed special proprietary drivers, which allow you to connect on 14.400bps unless you pay $20 or you get a 30-days limited edition ( [http://www.linuxant.com](http://www.linuxant.com) ). Though, they were not very satisfying (connection behaved strange) so I don't think I will pay.
- The realtime kernel used by ubuntustudio halts during boot. This has been submitted as a bug.
- I have not managed to do hibernation in any Ubuntu Version
- Since Gutsy, the laptop cannot "Suspend" and "resume"
- The key with the Euro sign (€) doesn't work :-)

---


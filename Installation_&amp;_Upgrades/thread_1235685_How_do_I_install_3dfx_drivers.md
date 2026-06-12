---
title: "How do I install 3dfx drivers?"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by litlfrog on 2009-08-09
We have a few old video cards sitting around the office. On one of our computers I'm trying to use a 3dfx video card, but it's not working at all well when I initially install it. I can only log in to a GNOME session in Failsafe mode and Firefox won't open. How do I a) determine exactly what card is installed (the model number isn't clear from the card) and b) configure Ubuntu to use a driver for that card?

---

### Post by phillw on 2009-08-09
[SIZE=2]Hi

The Voodoo drivers are available under Synaptic Package manager

The below article may also help you.

[http://ubuntuforums.org/showthread.php?t=878750](http://ubuntuforums.org/showthread.php?t=878750)

Regards,

Phill.
[/SIZE]

---

### Post by Narada on 2009-08-09
What kind of interface does it use? (PCI, PCI-X, AGP, PCI-E) Try running 'lspci' from a terminal and see if you can't find something about a graphics card or '3dfx' in there.

Have you tried using the vesa drivers with X? If you don't care about high resolution and don't want to hassle with it vesa should take care of you.

If Firefox is throwing a certain error, try running 'firefox' from a terminal and looking through the output for errors.

---

### Post by litlfrog on 2009-08-09
> **phillw said:**
> [SIZE=2]Hi

The Voodoo drivers are available under Synaptic Package manager

The below article may also help you.

[http://ubuntuforums.org/showthread.php?t=878750](http://ubuntuforums.org/showthread.php?t=878750)

Regards,

Phill.
[/SIZE]

Hmm, launching Firefox from the terminal worked fine, but it crashed about five minutes later when we went to open a new webpage. Still can't log in to GNOME except under failsafe mode. What we saw under Synaptic was that drivers for the card were already installed, but the xorg.conf file was completely generic. Using lspci we determined that the card is a Voodoo3. So if I've got a Voodoo 3 card and the drivers are installed but not being used, how do we make those drivers work? Do I need to set anything specific about the monitor?

---

### Post by Narada on 2009-08-09
Please post the output of:
```
cat /etc/X11/xorg.conf
```
We can check out your driver, monitor, etc. settings using that file.

---

### Post by litlfrog on 2009-08-09
Here it is

> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


---

### Post by Narada on 2009-08-09
That's all of it? Holy crap, you weren't kidding about generic. Try running this (without X running):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If it successfully re-writes xorg.conf, please post the cat output of it again. Also, in such case, try restarting X and see if it makes a difference.

---

### Post by litlfrog on 2009-08-09
OK, I'll try that now. I'm not sure how I'm supposed to run the dpkg-reconfigure without X running--stopping X takes us to a blank desktop screen with no cursor that doesn't respond to commands.

---

### Post by litlfrog on 2009-08-09
Had to restart the computer and logged into a failsafe terminal mode. Ran sudo dpkg-reconfigure -phigh xserver-xorg. The results that came back were exactly the same completely generic xorg.conf that showed up before.

---

### Post by Narada on 2009-08-09
I guess you could try running it while X is running, I just don't know if it will or not. Are you using Gnome? If so, kill gdm or use 'sudo init 3' from a terminal to drop out of X. Ctrl+Alt+Backspace may work, too, but if gdm is running I think it will just restart X as soon as you kill it.

-edit-
I was late, sorry.

At this point I'm not quite sure if there are any other auto-config X utilities for Ubuntu (I haven't actually used it since 6.06 was current), so someone running Ubuntu may be able to offer more accurate input. We may want to just write you up a basic xorg.conf and have you run it in the place of the dinky one that was generated. Gimme a bit to look for other X config utilities for Ubuntu. Hopefully someone comes along in the meantime and saves us. :D

---

### Post by phillw on 2009-08-09
I have not used voodoo cards for many years - a shame they went bust, but such is life, they were nice cards.

I've found this in the archives ... without a test unit & cards, I'm sorry that I can only point you towards articles that may be of help.

[http://ubuntuforums.org/archive/index.php/t-18106.html](http://ubuntuforums.org/archive/index.php/t-18106.html)

Phill. :confused:

---

### Post by Narada on 2009-08-09
Let's try this one:
```
sudo X -configure
```
:popcorn:

---

### Post by litlfrog on 2009-08-09
Hmm, this is getting frustrating. I can't figure out how I'm supposed to stop X from running, and if I try to run 
> sudo X -configure
 without doing so, I get a fatal server error. I don't see anything about xserver or gdm in the running processes, and the sudo init 3 didn't seem to do anything.

--EDIT--
This computer does have inadequate old onboard video, but it works. Would it be desirable or necessary to hook the monitor up to the onboard video output instead of the video card to work on this?

---

### Post by phillw on 2009-08-09
Whilst dusting off the cobwebs of voodoo boards ... I remembered this 'glitch' that could occur .... The article is quite clear - It could be something as daft as this .....

[http://www.wikihow.com/Disable-Onboard/Integrated-Video-On-Your-Computer](http://www.wikihow.com/Disable-Onboard/Integrated-Video-On-Your-Computer)

I remember having to do this for a new voodoo card some years ago.


Phill.

---

### Post by Narada on 2009-08-09
Perhaps the Xorg file being generated is exclusive to the onboard card? Disabling the onboard video in the BIOS and regenerating xorg.conf may yield different results.

In regards to being unable to kill X, did not killing the gdm process, running 'sudo init 3' from terminal, or Ctrl+Alt+Backspace work?

---

### Post by litlfrog on 2009-08-09
Unless we can figure out how to do so by changing a jumper on the mobo, I think I'll have to give this up. The PhoenixBIOS gives no way to disable onboard video, only switch between values of 512 or 1024 megs. It just seems crazy that this is so difficult--is it so much to ask to just download the drivers for a card, double-click a file, and forget about it?

---

### Post by phillw on 2009-08-10
Sorry to hear that link didn't work, From reading through it - they seemed to get it working, without bios altering - as one of the guys said - he had no bios control, either.

I'm afraid that, as i don't have any voodoo cards to play with, I cannot help you any more - I really thought that they had got the problem licked in that posting :-(

Phill.

---


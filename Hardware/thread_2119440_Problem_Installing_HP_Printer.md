---
title: "Problem Installing HP Printer"
date: 2013-02-23
forum: Hardware
---

### Post by lyni on 2013-02-23
I've have Ubuntu 12.04. yesterday I bought an HP Deskjet 3520 All in One Printer. I did look up the HP Linux Imaging site on [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

I thought it said that it was the right printer for the Ubuntu 12.04 but I must have looked at the wrong thing because its not supported.

anyway I have been having problems setting it up. today I installed the HPLIP but I still can't install the printer.

the small screen on the printer says 'Please use the SETUP cartridges that came with the printer.' I have installed them but I'm getting nowhere.

can someone please help?
thanks
lyn

---

### Post by fantab on 2013-02-24
HP 3520 is [**supported**]("http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3520_series.html") by the Linux Driver, HPLIP.

Install hplip-gui and set-up and configure your printer. Also you may have to set it as a default printer from System Settings -> Printers.

If you still have problems then Unplug the printer completely and replug it... it is sometimes necessary.

---

### Post by lyni on 2013-02-26
thank you for your reply.
I am still having problems. I've managed to get the printer to work as far as photocopying and scanning go but I still can't print from the computer.
I looked at installing the HPLIP but it says to go into the Terminal and that gets too complicated for me. I don't understand the Terminal well enough to do anything in it.
I installed the HPLIP from the Software Centre but that has not helped.
lyn

---

### Post by kurt18947 on 2013-02-26
> **lyni said:**
> thank you for your reply.
I am still having problems. I've managed to get the printer to work as far as photocopying and scanning go but I still can't print from the computer.
I looked at installing the HPLIP but it says to go into the Terminal and that gets too complicated for me. I don't understand the Terminal well enough to do anything in it.
**I installed the HPLIP from the Software Centre but that has not helped.**
lyn

That may be the problem.  I don't have an HP machine so do not have first-hand experience but the version of HPLIP in the Software Centre is somewhat dated.  The recommendation is to download the latest version from HP's web site.  Here is what i come up with:

[http://hplipopensource.com/hplip-web/index.html?](http://hplipopensource.com/hplip-web/index.html?)

But again, I do not have an HP machine to test this on so my advice may be worth what it cost you.:)

---

### Post by lyni on 2013-02-26
thank you Kurt, but like I said in my post I don't understand the Terminal enough to follow the directions in that link.
lyn

---

### Post by kurt18947 on 2013-02-27
> **lyni said:**
> thank you Kurt, but like I said in my post I don't understand the Terminal enough to follow the directions in that link.
lyn

Hi

Based on the table below, It looks like you need at least version 3.12.6.  Any idea what version of HPLIP is included in 12.04's repositories?  I'm using 13.04 right now and if I were to install HPLIP in this release, I'd get 3.12.11.  If 12.04 has a version >3.12.6, do have have HPLIP-GUI installed?  If not, that might help.  

A few hints if you decide to tackle the terminal.  When you enter a password or command, there is no feedback unless it DOESN'T succeed.  Copy/paste via right-click works just fine.  Letter case and punctuation do matter.  Why do manufacturers persist in using terminal installlation vs. GUI?  CLI inputs work the same regardless of desktop.  No matter Unity, Gnome-shell, KDE, Xfce, LXDE or something else, one set of scripts will work on them all.


Edit:  I guess the table didn't translate well.  Here's a link to the page:

[http://hplipopensource.com/hplip-web/supported_devices/deskjet_aio.html](http://hplipopensource.com/hplip-web/supported_devices/deskjet_aio.html)

---

### Post by fantab on 2013-03-01
Using terminal or CLI is NOT rocket science. It is as simple as a GUI, instead of point and click you have to enter text, thats is all. If you intend to use Linux you MUST learn to do things in the terminal. You can do it... its really quite simple and easy.

Just follow the instructions as shown [**HERE**]("http://hplipopensource.com/hplip-web/install/install/index.html").

If you are still having problem with Cli then post back here with your problem and we'll help.

Good Luck.

---

### Post by cyndijane on 2013-09-04
I am enough of a beginner that I don't even know how to go to the System Settings ->Printers. Where do I do that? Thanks!

---

### Post by lyni on 2013-09-09
> **cyndijane said:**
> I am enough of a beginner that I don't even know how to go to the System Settings ->Printers. Where do I do that? Thanks!

hi Cyndijane
if you have Ubuntu 12.4 you can go up to the right hand corner to the little star type icon where you Shut Down from. you will find System Settings there. just click on that. 
or on the left hand side of the screen you will have all those various icons, click on the one with tool (spanner?)that is the System Settings.
hope that helps
lyn

---


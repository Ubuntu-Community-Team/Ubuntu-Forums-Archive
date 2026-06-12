---
title: "Does Xubuntu not get the same love as Ubuntu?"
date: 2008-10-08
forum: General Help
---

### Post by Master One on 2008-10-08
For some reasons I like Xfce more than Gnome, especially since it feels snappier even on up-to-date hardware (although it is often mentioned, that Xfce on Xubuntu seems to be quite slow, compared to other distributions, or even Xfce installed on a plain commandline-Ubuntu as base).

I have two similar machines, one with Xubuntu 8.04.1 and the other with Ubuntu 8.04.1 installed. Right from the start, there are some differences that I can not find an explanation for, like:

- On Ubuntu the screen gets locked before suspend/hibernation, so that you have to enter the password on resume. That's not the case with Xubuntu, which could be quite problematic, especially if someone wants to use Xubuntu on a laptop. Is there even a simple solution for Xubuntu to have the same feature?

- On Ubuntu it's Firefox & Evolution, for which there are starters in the upper panel. On Xubuntu it's Firefox & Thunderbird, but there is only a starter for Firefox in the upper panel, not for Thunderbird (as if someone using Xubuntu is less likely to use an email client), which is quit annoying, because you can not just drag&drop something to the panel, but have to manually create a starter.

- On Ubuntu you have the time&date shown in the upper panel in a convenient format right from the beginning. On Xubuntu it's only the time, although there is also the Orage-Clock available as a panel-applet, which allows similar configuration (and even more) as the clock-applet on Ubuntu.

- On Ubuntu the volume-control-applet is installed by default, but not on Xubuntu (as if someone using Xubuntu is less likely to need a volume-control).

- On Ubuntu XSane is installed by default, on Xubuntu it has to be installed manually, which I did. I configured XSane on both machines for use with an Epson Perfection 1670 USB-Scanner (nothing special to be done, only the proper firmware-file has to be added). Scanner-recognition worked right away on Ubuntu, but not on Xubuntu. For some reason the folder /etc/sane.d had different permissions (drw-r--r-- on Xubuntu, drwxr-xr-x on Ubuntu), and the appropriate config file /etc/sane.d/snapscan.conf had just one line on Xubuntu ("firmware /etc/sane.d/"), whereas it was a full config file including comments on Ubuntu. Although I corrected those problems on Xubuntu, I could not get the mentioned scanner to work (Xsane searches for devices quite long, then it only tells "open of device snapscan:libusb:004:011 failed: Access to resource has been denied"). How can one and the same package produce such different results on Xubuntu and Ubuntu?

Looks like Xubuntu is not configured as properly as Ubuntu, after the installation has finished. Some issues are just minor, and can be fixed by doing some manual fiddling, for others (lock screen before suspend/hibernation and the XSane problems) I have not found a solution yet.

Isn't that strange? I mean, this is not about Kubuntu vs. Ubuntu with two completely different DEs & apps. Xfce has already been configured by the Xubuntu team to resemble the Gnome look & feel similar to Ubuntu, but not quite in detail. What do others think about that?

---

### Post by tyk on 2008-10-08
I use xubuntu on a laptop too and i have never faced a problem regarding screen locks. First screen locks and then suspend happens. At least two different scanners have also been tried and tested by me, one an hp one in all and the other an asus something or the other. no problems there at all. Since xfce is a lightweight gui, it does not install lots of little goodies to start with. the desktop itself is not as 'flexible' as gnome or kde, but the plugins available with the xubuntu panel are quite satisfying. also try creating launchers on the desktop. most common program launchers will configure by default.
I think xfce has got little to do with gnome except for some base dependencies. the look and feel is completely different and i use it on two highly contrasting machines with no xfce problems, only some [strange]("http://ubuntuforums.org/showthread.php?t=934899") linux ones :) one the laptop mentioned above (t23 thinkpad probably from 1997) and a q6600 bought this year.
Overall, hurray for xfce :KS

---

### Post by snowpine on 2008-10-08
There are only three "Officially supported" Ubuntu derivatives: Kubuntu, Edubuntu, and Ubuntu Server.

Xubuntu falls under the category of "Recognized derivatives... that use Ubuntu as their foundation and contribute signficantly towards the project".

[http://www.ubuntu.com/products/whatisubuntu/derivatives](http://www.ubuntu.com/products/whatisubuntu/derivatives)

So, you are correct that Xubuntu does not get the same "love" as Ubuntu, i.e. it is not as high a priority for Canonical as their "flagship" product, Ubuntu.

---

### Post by Calmatory on 2008-10-08
One of the problematic things of Xfce I found was the inability to right-click on a desktop to see the menu to set wallpaper etc. I am not quite sure if this was a bug and does it still remain as that happened in Xubuntu 7.10 IIRC.

Edit: Neither does the selecting with mouse work. Can't box the items I want. :(

Other than that, Xfce was great when I used it. :) Might as well jump back to it.

---

### Post by Master One on 2008-10-10
[QUOTE=tyk]I use xubuntu on a laptop too and i have never faced a problem regarding screen locks. First screen locks and then suspend happens.[/quote]
Are you sure, you do not confuse that kind of screen lock with the screensaver? Because I have disabled the screensaver (which is the only place offering the option "Lock screen when screensaver is active", there is nothing like this in the Power Manager Preferences), and only want it to lock when going into suspend or hibernation, which is working fine this way on Ubuntu, but not on Xubuntu (just a recent Xubuntu 8.04.1 installation, and always hiberating instead of turning that machine off, but it never asks for password and just resumes into the usable desktop). If there is no easy fix for this issue, the only other option would be to encrypt the whole harddisk, because then it would ask for the passphrase on resume from hibernation (which is still no solution for suspend-to-ram of course).

[QUOTE=tyk]At least two different scanners have also been tried and tested by me, one an hp one in all and the other an asus something or the other. no problems there at all.[/quote]
Did you just install xsane (which comes with xsane-common as a dep), or did you do something else as well, to get your scanning to work?

That matter is pretty strange, because it really should not matter, if xsane is already preinstalled on Ubuntu, or installed afterwards on Xubuntu, if the rest of the necessary config is exactly the same. Nevertheless, I did exactly the same on the Ubuntu & Xubuntu machines, and it worked right away on Ubuntu, but not on Xubuntu...

[QUOTE=tyk]Since xfce is a lightweight gui, it does not install lots of little goodies to start with. the desktop itself is not as 'flexible' as gnome or kde, but the plugins available with the xubuntu panel are quite satisfying. also try creating launchers on the desktop. most common program launchers will configure by default.[/quote]
Not a problem here, I like it light & fast, that's why I want to use Xfce even on decent hardware. It really is comfortable to work with. Launchers in the panel or the desktop are a non-issue, I was just curious why the Xubuntu devs decided to preconfigure it differently from Ubuntu.

[QUOTE=tyk]I think xfce has got little to do with gnome except for some base dependencies. the look and feel is completely different and i use it on two highly contrasting machines with no xfce problems, only some [strange]("http://ubuntuforums.org/showthread.php?t=934899") linux ones :) one the laptop mentioned above (t23 thinkpad probably from 1997) and a q6600 bought this year. Overall, hurray for xfce :KS[/QUOTE]
I know that Xfce has nothing to do with Gnome, except that it is based on Gtk+ as well. Nevertheless the Xubuntu devs decided to resemble the look & feel of Ubuntu, considering the panel and desktop configuration (not the artwork of course), instead of sticking with the default Xfce configuration.

[quote=snowpine]There are only three "Officially supported" Ubuntu derivatives: Kubuntu, Edubuntu, and Ubuntu Server. Xubuntu falls under the category of "Recognized derivatives... that use Ubuntu as their foundation and contribute signficantly towards the project".[/quote]
Looks like the mentioned page has not been updated, because [**here**](http://www.ubuntu.com/products/whatisubuntu/xubuntu) Xubuntu is mentioned to be "an official derivative of Ubuntu", which means it is indeed on the same level as Kubuntu, Edubuntu and Ubuntu Server.

[quote=Calmatory]One of the problematic things of Xfce I found was the inability to right-click on a desktop to see the menu to set wallpaper etc. I am not quite sure if this was a bug and does it still remain as that happened in Xubuntu 7.10 IIRC. Neither does the selecting with mouse work. Can't box the items I want.[/quote]
On Xubuntu a right-click on the desktop has an option for going to the desktop preferences, where you can change the wallpaper. But I do not think that a missing option for setting the wallpaper is something "problematic" (How often do you need that? I never change the wallpaper). Boxing desktop icons indeed does not work, but you still can shift-click or strg-click your selection, so that should not really be a point to prefer Gnome over Xfce neither.

---

### Post by Master One on 2008-10-13
> **snowpine said:**
> There are only three "Officially supported" Ubuntu derivatives: Kubuntu, Edubuntu, and Ubuntu Server. Xubuntu falls under the category of "Recognized derivatives... that use Ubuntu as their foundation and contribute signficantly towards the project". So, you are correct that Xubuntu does not get the same "love" as Ubuntu, i.e. it is not as high a priority for Canonical as their "flagship" product, Ubuntu.
Another indication for Xubuntu being on par with the rest of the official *ubuntus can be found right here in these forums:> **Main Support Categories**
Choose the most appropriate category for your questions regarding ANY Ubuntu/Kubuntu/**Xubuntu**/Edubuntu release.
There would be no offical support here in the main forums, if Xubuntu would have been just another "recognized derivative".

BTW Running sixux-xfce-2008-03 and Xubuntu 8.04.1 side-by-side does not look so good for Xubuntu, have a look [**here**](http://ubuntuforums.org/showthread.php?t=946303).

---

### Post by snowpine on 2008-10-13
I stand corrected, thanks for the updated links guys!

I have always been a little disappointed in Xubuntu. I don't think it is nearly as "lightweight" as it should/could be. My recommendation to Canonical is they need a truly lightweight distro that will run on older hardware than Xubuntu currently easily supports. Either by slimming down Xubuntu, or by developing an official variant along the lines of Fluxbuntu.

---

### Post by tyk on 2008-10-16
@Master One
"but it never asks for password and just resumes into the usable desktop"
yes that is true. even on the intrepid. suspend or hibernate and then come back to active desktop. hmm, though i dont have problems with that. i have not tried it yet but there is something called a 'xflock' or thereabouts. methinks it exactly only locks screen.

"Did you just install xsane (which comes with xsane-common as a dep), or did you do something else as well, to get your scanning to work?"
nothing else. one was a usb scanner and the other a parallel.

"Not a problem here, I like it light & fast, that's why I want to use Xfce even on decent hardware. "
ditto. got it on my quad-core too. absolutely dependable and zippy.

cheers.

---

### Post by tyk on 2008-10-26
xubuntu intrepid rc new status on thinkpad:
lock screen, suspend, hibernate work perfectly. all need now password entry for relogon.

---

### Post by OrangeCrate on 2008-10-26
Like the OP, I don't particularly like Gnome, and I do like Xfce.

I've tried individual installations of both Ubuntu and Xubuntu, and as already discussed, each lacks something that the other has. So, I've simply settled in on a hybrid of the two as my everyday OS.

I install the Xfce desktop over a complete Ubuntu installation. My current, (as of yesterday, I waited until the RC to add it) is Xfce/Intrepid. In my other partition, I have Xfce/Hardy.

What you end up with, is the best that Ubuntu has to offer, everything works "out of the box" on Xfce (OOo, Xsane, printer, etc.), plus you get the snappiness, and clean look of the Xfce interface.

IMO, the best of both worlds, on one desktop.

For anyone interested in trying this, the installation instructions are here:

[http://psychocats.net/ubuntu/xubuntu](http://psychocats.net/ubuntu/xubuntu)

(As always, thank you Aysiu, for your fine site.)

Edit:

Here's my current desktop, on my older 1.4 GHz Celeron, with 512 meg of RAM...

---

### Post by florentx on 2009-03-22
> **tyk said:**
> @Master One
"but it never asks for password and just resumes into the usable desktop"
yes that is true. even on the intrepid. suspend or hibernate and then come back to active desktop. hmm, though i dont have problems with that. i have not tried it yet but there is something called a 'xflock' or thereabouts. methinks it exactly only locks screen.

I have same issue with Jaunty.
I developped a small script which should fix this issue cleanly.

See here: [http://ubuntuforums.org/showpost.php?p=6938390&postcount=2](http://ubuntuforums.org/showpost.php?p=6938390&postcount=2)

-- 
Florent

---


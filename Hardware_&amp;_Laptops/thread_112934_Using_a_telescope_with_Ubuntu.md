---
title: "Using a telescope with Ubuntu"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by matthew on 2006-01-05
Has anyone here used a Meade telescope with Ubuntu?

I was given a Meade DS-2090AT-TC for Christmas (it's an amateur refracting telescope with automatic tracking). It came with the company's Autostar tracking software so it can be connected to a Windows laptop and once the scope is set up it can be controlled by the computer. The problem is that I don't have Windows on any computer I own.

It seems logical to me that there are astronomers out there that use Linux so there must be somthing similar (or better) available for Ubuntu. I've googled, read the Meade website and can't find anything. I have started playing with KStars (even though I use Gnome it seems to be working pretty well) and it says it will connect to a telescope so I hope to test that out in the next few days. In the meanwhile...

Does anyone have any experience with this stuff? Got any tips, advice, etc. for a total neophyte?

---

### Post by imrumpf on 2006-01-05
No real experience on a telescope but you COULD try to load the windows software on the CD with either Wine or Crossover Office. Sometimes one will work better than the other, and there's no harm in trying :p

---

### Post by hndrcks on 2006-01-05
The Sky Charts software is very good and includes scope control under Windows. I know that the author is working on a Linux version as well, Sourceforge page here

[http://skychart.sourceforge.net/](http://skychart.sourceforge.net/)

good luck!

---

### Post by Topsiho on 2006-01-05
Did you have a look into KStars, which is a desktop planetarium which is a part of the kdeedu package? You can also install only kstars (and it's dependencies of course) with apt-get, if I am correct with

sudo apt-get install kstars

Possibly it's in your language too, if you install the correct kde-i18n-xx file, in which the xx should be substituded for the letters for your country (nl is the Netherlands).

Edit: I discover that you probably all speak English natively. Let's say: not all people that read this interestedly do :)

In the main menu you 'll find an entrance of which I forgot the English name but which should be something like "Devices". The submenu's of this are, among other things, something like "Telescope Wizard", "Device manager" and "Configuring INDI". What this last item means you should discover for yourself :), it's a wonderland ....

Success,

Topsiho

---

### Post by matthew on 2006-01-05
Update: I discovered a metapackage in the repositories called education-astronomy that has a lot of great packages included in it. It looks like KStars should do what I want it to do...now I just need to wait for a little free time. If only my inlaws weren't coming for dinner tonight. :)

Thank you to all who have contributed so far. If anyone has any thoughts or experiences to share that haven't been mentioned already, please join in!

When I get this tested out I'll post my experiences.

---


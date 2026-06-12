---
title: "Problem with my Wacom tablet"
date: 2013-10-06
forum: Hardware
---

### Post by Abd_el_Rahman_Magdy on 2013-10-06
I really don't know if this is the appropriate category for my question. I have a Bamboo Pen & Touch that I use for drawing and animation. I am able to configure the pen buttons to some actions, but I want to configure the Express Keys of the tablet. When I go to Wacom Graphics Tablet in System Settings, and go to Map Buttons, this is what I get:

[ATTACH=CONFIG]246778[/ATTACH]

It shows no buttons at all, although my tablet has 4 buttons. How can I solve this??

---

### Post by Abd_el_Rahman_Magdy on 2013-10-06
Can anyone help????

---

### Post by Iowan on 2013-10-06
Your solution might be in another time zone. Please wait 24 hours before/between bumps.

---

### Post by Abd_el_Rahman_Magdy on 2013-10-06
Thank you Iowan.. dunno y I forgot abt the different time zones :D

---

### Post by Favux on 2013-10-07
Hi,

I'm guessing you are using Unity with Precise (12.04)?  The Gnome Wacom configuration gui applet doesn't support the ExpressKeys for BambooPT tablets yet in your version of Gnome.  Actually not sure if they are supported in the latest release of Gnome or not.  Anyway that's because Chris made the kernel report the buttons out of sequence and they didn't envision that when they coded up the applet.  Supposedly someone was going to fix that.  The KDE configuration applet handles them I think.  Otherwise you'll need to use xsetwacom commands probably in a script.  See parts IV. and V. on the old BambooPT HOW TO:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)  or the [updated version]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408").

---

### Post by Abd_el_Rahman_Magdy on 2013-10-09
Thank you Favux.. I installed the kde-config-tablet, but I have two problems with it
1) I don't know how to run it... I searched, and the only way I found is to run this command from terminal: kcmshell4 kcm_wacomtablet... Is this the appropriate way???

2) When I use that command, the applet starts, but I get this message: > D-Bus connection to the kded daemon not available.

Please start the Wacom tablet daemon and try again.
The daemon is responsible for tablet detection and profile support.

---

### Post by Favux on 2013-10-09
Sorry, I haven't used either gui much.  I tend to use xsetwacom commands in scripts.  I really should investigate the KDE Wacom gui in some detail though on my Kubuntu install.  Put that on the TODO list.  Basically the latest releases of both gui's have overcome most of their problems and are worth looking at now.

You haven't yet said what Desktop you have.  I'm still guessing it is Unity.  So while there may be support for Qt tool kit based code, maybe with a few extra dependencies called, it is not suprising that the KDE dBUS daemon is not running on what is at base a Gnome setup.  Follow?

I was just mentioning the KDE Wacom configuration gui for completeness sake and on the off chance you were using KDE.  I wasn't expecting you to hybridize your Unity/Gnome Desktop enough to run it.

---

### Post by Abd_el_Rahman_Magdy on 2013-10-09
As you said Favux, it's Unity. The problem is, um kinda beginner with Ubuntu, so I sometimes get lost when dealing with command lines; GUI makes things easier for me. I installed kdelibs5 to be able to use Krita and Kdenlive, since I wasn't very comfortable with Linux Mint KDE; I strangely suffered from a lot of wireless problems.. I think the same happens with Kubuntu.

Therefore, I need to be able to use the kde configuration applet in Ubuntu, if it is possible.

I need to ask abt other thing related to the same problem.. I am planning to get Intuos5.. will I get the same problem with the ExpressKeys, or will it be working fine with Ubuntu Tablet Settings??

Thanks a lot

---

### Post by Favux on 2013-10-09
Actually the Intuos 5's Express Keys should work fine with the Gnome Wacom applet.  It doesn't have the problem the Bamboo has with out of sequence keys.

Since Kubuntu is a no go due to the wireless problems then effectively you're left with xsetwacom commands for now.  I understand that CLI stuff can seem a little intimidating to a newbie.  But if you get a chance to spend a little time on it you'll find it isn't really that hard.

The HOW TO has sample scripts to get you started.  They were made with older versions of Ubuntu so the syntax has probably changed a little bit.  Just run **xinput list** in a terminal to get the current device names and you should be good to go.  Also more information on using xsetwacom is available on the wiki:
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)
from:
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---

### Post by Abd_el_Rahman_Magdy on 2013-10-09
Thank you very much.. I'll try xsetwacom :)

---


---
title: "Flash Player problems."
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by AaronSD on 2009-04-01
I just received my mini dell 9 with linux on it, so far i love it although firefox is giving me problems with flash. I searched the forums but to no avail.

I have installed flashplugin-nonfree yet when ever i go to a website which uses flash im prompted that i am missing plugins.

Im fairly new to linux (as in less than 24 hours of use) so try to make your answers user friendly thank you.

---

### Post by Guymed on 2009-04-01
I have the same problem. Only when I try to install it from the Adobe website, when I open the package it says 'wrong architecture 'i386''. I need for it to work because I run a website about flash games.

---

### Post by brianchidester on 2009-04-01
sudo apt-get install ubuntu-restricted-extras

---

### Post by Guymed on 2009-04-01
Sorry, but that STILL didn't work. IT DOESN'T WORK! EVERYTHING I TRY DOESN'T WORK!

---

### Post by bluewhaletail on 2009-04-01
Didn't work for me either.  I've gotten the Debian "install_flash_player_10_linux" package from Adobe and installed it.  I've installed the "adobe-flashplugin" via Adept manager.  I've invoked both

sudo apt-get install flashplugin-nonfree

and (most recently)

sudo apt-get install ubuntu-restricted-extras

Which apparently installed:

  cabextract gstreamer0.10-ffmpeg gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse java-common
  liba52-0.7.4 libavc1394-0 libavcodec1d libavformat1d libcdaudio1
  libdc1394-13 libdv4 libdvdread3 libfaac0 libfaad0 libfreebob0 libgmyth0
  libid3tag0 libiec61883-0 libiptcdata0 libjack0 liblame0 libmjpegtools0c2a
  libmms0 libmpeg2-4 liboil0.3 libopenspc0 libquicktime1 libsidplay1
  libsndfile1 libsoundtouch1c2 libwildmidi0 libx264-57 libxvidcore4
  msttcorefonts sun-java6-bin sun-java6-jre sun-java6-plugin
  ubuntu-restricted-extras unrar

Checked Firefox (vers 3.0.7) Tools/Add-ons (no change there), restarted, etc.  Nothing works.  I would very much appreciate if if someone could provide an absolutely fail-safe way to allow me to have flash work in the Firefox browser.  As a very new user to Kubuntu, I'm surprised that this is turning out to be such a hassle.

---

### Post by Guymed on 2009-04-01
I have made a quick guide to installing flash player. This just occured to me, because I had to install Ubuntu twice today. This is what made it work for me:

1. Shut down your computer after running Ubuntu/Kubuntu/Xubuntu.
2. Pull the power cord out of your computer (optional, but can help), then plug it back in and re-boot your computer.
3. Open up Firefox and go to a page that requires flash.
4. If a message comes up saying 'install missing plugins', click that.
5. It should install correctly.

Test it on play.clubpenguin.com.

Personal message me if it worked for you!

---

### Post by bluewhaletail on 2009-04-01
Guymed: Thanks for the suggestion.  Still no Flash functionality.  For play.clubpenguin.com and other websites, taking the "need to install" path generally leads me to an Adobe webpage where I end up downloading various install_flash_player_10 modules which, on subsequent open with GDebi Package Installer tell me that I already have a more recent version installed (so I quit/exit).

Which application is The One To Install With, as it were.  Firefox?  Adept manager?  GDebi Package Installer?  I think I've tried all three approaches, but maybe I've missed something.

---

### Post by Guymed on 2009-04-02
Hmm... I don't know why. I had to restart my system, then, try making a link looking like this:
apt:flashplugin-nonfree
That helped me to install it AFTER I rebooted and tried everything, literally EVERYTHING! It is an 18 file package.

---

### Post by brianchidester on 2009-04-02
bluewhaletail, do you have a Launchpad account? I suggest you file this bug under the dell mini project if you do. Use the format below when submitting and also include your version of firefox and flash -- This can be found in the synaptic package manager or if you are comfortable in the terminal then with the command 'apt-cache policy flashplugin-nonfree'. Post a bug number here when you do.

Build Version/Date:
Environment used for testing:

Summary:


Steps to Reproduce:


Expected result:


Actual result:

---

### Post by utnubuuser on 2009-04-02
There've been some posts about probs with the flash player, and in the solutions I've found, the procedure always calls for removing any currently installed instances of flash before trying something else.

ie, remove gnash, or unistall flash plugin through the FF toolbar, then attempt a new install.

Flash-plugin non-free has always worked on my gear, but I've no fancy cards.

---

### Post by bluewhaletail on 2009-04-09
Hi everyone.  Sorry for the delay; was working on other equipment recently.

Well, nothing works.

[COLOR="Red"]UPDATE: I got it to work

I removed all packages, Firefox and Flash related (including Gnash SWF thingies).
Then I removed my .mozilla file from home directory (probably not a factor)
Then I removed all Firefox folders on the system (by searching in Dolphin for *firefox*).
Then I used the Synaptic Package manager to add: Firefox, then the flashplugin-nonfree

That seems to have done the trick.  Thanks to all who contributed suggestions to my initial query.  I guess somehow I got something in there (via the Adobe website d/l package and manual install??) that broke subsequent installs.[/COLOR]

BELOW IS WHAT I WROTE BEFORE GETTING IT TO WORK:

Via Adept Manager, removed:
adobe-flashplugin
flashplugin-nonfree
RESTART
Go to webpage requiring Flash, click on install, won't work so hit <Manual Install> button and get to Adobe, d/l the latest module to desktop, install. Message:
Package 'install_flash_player_10_linux(2).deb' was installed
Killed all FF instances, RESTART
Via Adept Manager:
Upgrade: adobe-flashplugin
Install: flashplugin-nonfree
Run FF.  Still nothing under Tools/Add-ons for either the Plugins or Extensions tabs.

But as long as I have some readers (?), some comments:

To utnubuuser:  I wish I could see the Flash plugin via the toolbar (I assume you mean via Tools/Add-ons).  I don't even have that.

What is this flashplugin-nonfree all about?  What's the 'nonfree' aspect?  It seems as if the 'nonfree' modifier has absolutely no meaning to the potential user.  So why is it named thusly?

---


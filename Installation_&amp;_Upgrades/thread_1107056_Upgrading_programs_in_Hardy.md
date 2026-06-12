---
title: "Upgrading programs in Hardy?"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by Linux_Shishya on 2009-03-26
Hello folks!

Well I'm a newbie to Linux so please bear with me. :popcorn: 

I have installed the Hardy Heron Ubuntu version here as the latest Intrepid would work only without Compiz on my machine(Intel 845). But I wanted Compiz,:) so I downloaded and installed the next latest Hardy Heron. Everything works fine in Hardy, but the bundled programs such as GIMP have had new releases. GIMP apart I'd like to also update Nautilus to the newer one which has tabs feature as well as the compact icon mode. So now how do I update them? I added the repo list of Intrepid in the sources, which also showed up in Synaptic, but when I try to upgrade them it gives me a box which shows me components to be uninstalled, installed and upgraded.(see this>>[ATTACH]107679[/ATTACH]) Now I'm not really sure about this. What say, will nautilus and the latest GIMP work in Hardy? And if they don't how do I roll back the changes. Also is it okay if I first download the packages and manually run them later. This way I could backup my downloads, as I'm on dial-up.:P

Any help will be much appreciated. I have only begun setting up Linux, so I am open to any experimentation now than when I'd have a set system. So I don't mind tinkering around a bit even it screws up!;)

:-\"

---

### Post by spcwingo on 2009-03-26
Check out:

[http://www.getdeb.net]("http://www.getdeb.net")

Alternately, you can Google something like: "Ubuntu Gimp ppa" and see if that'll give updated versions of the apps that you're after.

---

### Post by Linux_Shishya on 2009-03-27
Well, I upgraded Gimp from the packages at getdeb.net. That went well without any problem. Next, I upgraded Nautilus through Synaptic by adding the Intrepid repos there.(Note: I'm running Hardy Heron)
Now I get the following error at login 
> There was an error starting the GNOME Settings Daemon. Some things, such as themes, sounds, or background settings may not work correctly. The Settings Daemon restarted too many times. GNOME will still try to restart the Settings Daemon next time you log in.

While upgrading Nautilus the following files were upgraded, removed or installed.
```
libcupsys2 will be removed
libgail-common will be removed
libgail18 will be removed
libgnomekbd2 will be removed
libgnomekbdui2 will be removed
capplets-data (version 1:2.22.1-0ubuntu4.1) will be upgraded to version 1:2.24.0.1-0ubuntu7
cupsddk (version 1.2.0-0ubuntu1) will be upgraded to version 1.2.3-3
cupsddk-drivers (version 1.2.0-0ubuntu1) will be upgraded to version 1.2.3-3
cupsys (version 1.3.7-1ubuntu3.3) will be upgraded to version 1.3.9-2
cupsys-bsd (version 1.3.7-1ubuntu3.3) will be upgraded to version 1.3.9-2
cupsys-client (version 1.3.7-1ubuntu3.3) will be upgraded to version 1.3.9-2
cupsys-common (version 1.3.7-1ubuntu3.3) will be upgraded to version 1.3.9-2
cupsys-driver-gutenprint (version 5.0.2-2ubuntu1) will be upgraded to version 5.2.0~rc1-0ubuntu1
findutils (version 4.2.32-1ubuntu2) will be upgraded to version 4.4.0-2ubuntu3
gconf2 (version 2.22.0-0ubuntu3) will be upgraded to version 2.24.0-0ubuntu1
gconf2-common (version 2.22.0-0ubuntu3) will be upgraded to version 2.24.0-0ubuntu1
gnome-applets (version 2.22.2-0ubuntu2) will be upgraded to version 2.24.1-0ubuntu1
gnome-applets-data (version 2.22.2-0ubuntu2) will be upgraded to version 2.24.1-0ubuntu1
gnome-control-center (version 1:2.22.1-0ubuntu4.1) will be upgraded to version 1:2.24.0.1-0ubuntu7
gnome-screensaver (version 2.22.2-0ubuntu1) will be upgraded to version 2.24.0-0ubuntu2
gnome-settings-daemon (version 2.22.1-0ubuntu2) will be upgraded to version 2.24.0-0ubuntu3
gtk2-engines-pixbuf (version 2.12.9-3ubuntu5) will be upgraded to version 2.14.4-0ubuntu1
hal-cups-utils (version 0.6.13+svn86-0ubuntu4) will be upgraded to version 0.6.17+git20080728-0ubuntu2
hpijs (version 2.8.2+2.8.2-0ubuntu8.1) will be upgraded to version 2.8.7-0ubuntu6
hplip (version 2.8.2-0ubuntu8.1) will be upgraded to version 2.8.7-0ubuntu6
hplip-data (version 2.8.2-0ubuntu8.1) will be upgraded to version 2.8.7-0ubuntu6
libasound2 (version 1.0.15-3ubuntu4) will be upgraded to version 1.0.17a-0ubuntu4
libc6 (version 2.7-10ubuntu4) will be upgraded to version 2.8~20080505-0ubuntu7
libc6-i686 (version 2.7-10ubuntu4) will be upgraded to version 2.8~20080505-0ubuntu7
libcairo2 (version 1.6.0-0ubuntu2) will be upgraded to version 1.8.0-0ubuntu1
libcupsimage2 (version 1.3.7-1ubuntu3.3) will be upgraded to version 1.3.9-2
libebook1.2-9 (version 2.22.3-0ubuntu3) will be upgraded to version 2.24.1-0ubuntu1
libeel2-2 (version 2.22.2-0ubuntu1) will be upgraded to version 2.24.1-0ubuntu1
libgconf2-4 (version 2.22.0-0ubuntu3) will be upgraded to version 2.24.0-0ubuntu1
libgcrypt11 (version 1.2.4-2ubuntu7) will be upgraded to version 1.4.1-1ubuntu1
libglib2.0-0 (version 2.16.6-0ubuntu1.1) will be upgraded to version 2.18.2-0ubuntu1
libgnome-window-settings1 (version 1:2.22.1-0ubuntu4.1) will be upgraded to version 1:2.24.0.1-0ubuntu7
libgnomecanvas2-0 (version 2.20.1.1-1) will be upgraded to version 2.20.1.1-1ubuntu2
libgnomecups1.0-1 (version 0.2.3-1ubuntu1) will be upgraded to version 0.2.3-2build1
libgnomekbd-common (version 2.22.0-1) will be upgraded to version 2.24.0-0ubuntu2
libgnomeprint2.2-0 (version 2.18.4-1) will be upgraded to version 2.18.5-1
libgnomeprint2.2-data (version 2.18.4-1) will be upgraded to version 2.18.5-1
libgs8 (version 8.61.dfsg.1-1ubuntu3.1) will be upgraded to version 8.63.dfsg.1-0ubuntu6
libgtk2.0-0 (version 2.12.9-3ubuntu5) will be upgraded to version 2.14.4-0ubuntu1
libgtkhtml2-0 (version 2.11.1-1) will be upgraded to version 2.11.1-2ubuntu1
libgtkhtml3.14-19 (version 3.18.3-0ubuntu2) will be upgraded to version 1:3.24.1-0ubuntu1
libgutenprint2 (version 5.0.2-2ubuntu1) will be upgraded to version 5.2.0~rc1-0ubuntu1
libgweather1 (version 2.22.3-0ubuntu2) will be upgraded to version 2.24.1-0ubuntu1
libpango1.0-0 (version 1.20.5-0ubuntu1) will be upgraded to version 1.22.1-0ubuntu1
libpango1.0-common (version 1.20.5-0ubuntu1) will be upgraded to version 1.22.1-0ubuntu1
libpixman-1-0 (version 0.10.0-0ubuntu1) will be upgraded to version 0.12.0-1
libpolkit-dbus2 (version 0.7-2ubuntu7) will be upgraded to version 0.9-1ubuntu3
libpolkit2 (version 0.7-2ubuntu7) will be upgraded to version 0.9-1ubuntu3
libpopt0 (version 1.10-3build1) will be upgraded to version 1.14-4
libselinux1 (version 2.0.55-0ubuntu4) will be upgraded to version 2.0.65-2
libsoup2.4-1 (version 2.4.1-1ubuntu1) will be upgraded to version 2.24.1-0ubuntu1
libsqlite3-0 (version 3.4.2-2) will be upgraded to version 3.5.9-3
libxi6 (version 2:1.1.3-1) will be upgraded to version 2:1.1.3-2build1
libxklavier12 (version 3.5-1) will be upgraded to version 3.7-1
nautilus (version 1:2.22.5.1-0ubuntu1) will be upgraded to version 1:2.24.1-0ubuntu1
nautilus-data (version 1:2.22.5.1-0ubuntu1) will be upgraded to version 1:2.24.1-0ubuntu1
nautilus-share (version 0.7.2-0ubuntu5.1) will be upgraded to version 0.7.2-0ubuntu7
python-cups (version 1.9.34-0ubuntu1) will be upgraded to version 1.9.41-0ubuntu1
splix (version 1.1.1-0ubuntu1) will be upgraded to version 2.0.0~rc2-0ubuntu2
cups (version 1.3.9-2) will be installed
cups-bsd (version 1.3.9-2) will be installed
cups-client (version 1.3.9-2) will be installed
cups-common (version 1.3.9-2) will be installed
cups-driver-gutenprint (version 5.2.0~rc1-0ubuntu1) will be installed
libcamel1.2-14 (version 2.24.1-0ubuntu1) will be installed
libcanberra-gtk0 (version 0.6-0ubuntu3) will be installed
libcanberra0 (version 0.6-0ubuntu3) will be installed
libcups2 (version 1.3.9-2) will be installed
libedataserver1.2-11 (version 2.24.1-0ubuntu1) will be installed
libgnome-desktop-2-7 (version 1:2.24.1-0ubuntu1) will be installed
libgnomekbd3 (version 2.24.0-0ubuntu2) will be installed
libgnomekbdui3 (version 2.24.0-0ubuntu2) will be installed
libgnutls26 (version 2.4.1-1build1) will be installed
libgucharmap7 (version 1:2.24.1-0ubuntu1) will be installed
libijs-0.35 (version 0.35-3) will be installed
libltdl7 (version 2.2.4-0ubuntu4) will be installed
libpoppler3 (version 0.8.7-1) will be installed
libxcb-render-util0 (version 0.2+git36-1) will be installed
libxcb-render0 (version 1.1-1.1) will be installed
python-cupshelpers (version 1.0.5+git20080819-0ubuntu6) will be installed
python-usb (version 0.4.1-4) will be installed
ubuntu-system-service (version 0.1.10) will be installed

```

I've tried some of the fixes suggested elsewhere, like changing the network interfaces file, but that didn't help.

Any idea what's up.

---

### Post by Linux_Shishya on 2009-03-27
Spam?

---

### Post by spcwingo on 2009-03-27
You probably hosed your install by mixing repos.  If it's not for Hardy, don't install it as it might trash your install (this is to include adding Intrepid, Jaunty, and the upcoming Karmic repos).

---

### Post by albinootje on 2009-03-27
> **Linux_Shishya said:**
> Next, I upgraded Nautilus through Synaptic by adding the Intrepid repos there.(Note: I'm running Hardy Heron)
Now I get the following error at login 

Looks like you messed up your installation. 

Do some reading about apt-pinning first :
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by Linux_Shishya on 2009-03-28
Thanks for the heads up guys. 

Guess I did mess up my installation. After trying quite a few things though I decided to reinstall Ubuntu Hardy. After reinstalling I updated Hardy again from the Intrepid disk I downloaded, this time all packages. But then I ran into the same problem I had with Intrepid, i.e. getting stuck at login due to the Intel driver bug. I was hoping that the driver won't be upgraded to the one in Intrepid but it was. But this time I wasn't getting the gnome error at startup (I uninstalled Compiz before login), so I guess I had to upgrade some other gnome packages when I upgraded Nautilus in my previous install.
Is the Intel driver update neccessary for Intrepid packages? How can I prevent it from updating? Or maybe install the older Intel i810 driver from Hardy in Intrepid? Is it possible to use holding in Synaptic to prevent the driver update? Basically I just want to upgrade to Gnome 2.26 in Hardy.

Apparently, from what I've read at the bug report pages, this particular bug is unlikely to be fixed in Jaunty. So I've no option but to experiment, or wait for the next release. 

Again, I'm a newbie to Linux, so please bear with me.

---

### Post by albinootje on 2009-03-28
> **Linux_Shishya said:**
>  Is the Intel driver update neccessary for Intrepid packages? How can I prevent it from updating? Or maybe install the older Intel i810 driver from Hardy in Intrepid? Is it possible to use holding in Synaptic to prevent the driver update? Basically I just want to upgrade to Gnome 2.26 in Hardy.


Please try the following :
1) Reinstall Ubuntu Hardy
2) Read the apt-pinning documentation properly!
3) Then try to install only Gimp and Nautilus from Intrepid with apt-pinning. 
YMMV, Good Luck!

---


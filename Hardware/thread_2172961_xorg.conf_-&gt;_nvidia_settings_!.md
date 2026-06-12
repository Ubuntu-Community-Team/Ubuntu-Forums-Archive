---
title: "xorg.conf -&gt; nvidia settings ?!?"
date: 2013-09-07
forum: Hardware
---

### Post by Coder88 on 2013-09-07
EDIT: SOLVED, sort of: I gave up on tweaking xorg and such-- even after buying a new graphics card (to be returned tomorrow). I just reinstalled ArtistX 12.10 ( based on Ubuntu 12.10) and wouldn't you know it-- my powerful nvidia graphics card was recognized and configured, Compiz was automagically installed, and without any messing around with xorg.conf or nvidia-settings I have full screen resolution with menus, laucher/taskbar, and Compiz. I just had to install the compiz fusion icon and now i have cool compiz effects like wobbly windows, etc. My nvidia graphics got all messed up when i made the fatal mistake of applying updates and upgrading to ubuntu 13.04, and I will not make those mistakes again.

Note that during the ArtistX 12.10 install I chose NOT to install updates, NOT to upgrade to the latest Ubuntu; I am convince that can just lead to headaches, problems. I am turning off updates; I will just wait periodically for a new ArtistX distro, and before any updates or upgrades plan to image my ArtistX disc using Clonezilla so I can get anything back if synaptic/updates/upgrades/versions mess up my system-- this is a huge concern as I have seen linux far far far less forgiving when uninstalling apps or installing updates, compared to Windows.

--------------
I am frustrated, trying to get my X desktop working with my nvidia GeForce card (GeForce GTX 260, dual dvi connectors/twinview). I have the driver and nvidia-settings installed, I can bring up the nvidia-settings, but saving the resulting xorg.conf does nothing to solve the problem. My issue is that the launcher/taskbar at the bottom of the screen is gone/missing even though I have my desktop icons for Home, Computer, Terminal (thank goodness I added that shortcut to the desktop!)-- until I "sudo nvidia-settings" and check the box for "[x] make this the primary display for the X screen", then the launcher/taskbar magically appears. I save the settings to /etc/X11/xorg.conf and reboot but nothing changes, same problem (no launcher/taskbar). 

I have come to a conclusion/theory that the xorg.conf file settings must need to be saved from nvidia-settings to some other location. but where?!? As I research xorg.conf it is the most confusion file on the planet because it seems it can and does exist in many locations
[http://manpages.ubuntu.com/manpages/quantal/en/man5/xorg.conf.5.html](http://manpages.ubuntu.com/manpages/quantal/en/man5/xorg.conf.5.html)
so how I am supposed ot know where I should save my nvidia-settings generated custom xorg.conf?

Where should I write my custom xorg.conf file???

At this point I am even willing to buy a different graphics video card at the local electronics store, as I wonder if this is an issue with my card having dual DVI, because as I said when I check the box for 'make this (Acer Monitor) the PRIMARY display' the taskbar launcher at the bottom of the screen magicallky appears. So should I just buy an nvidia/GeForce card with one DVI, one that is not twinview?

So frustrating to be so close to a functioning kick-**** linux system. But NOT having a bottom of the scren menu/launcher really is frustrating beyond belief.

---

### Post by carlwsnyder on 2013-09-07
Have you tried simply MOVING your display connection to the other connection?  You may have your display connected to the secondary DVI connection on your card, which can't be made primary without modifying the card.

---

### Post by Coder88 on 2013-09-07
> **carlwsnyder said:**
> Have you tried simply MOVING your display connection to the other connection?  You may have your display connected to the secondary DVI connection on your card, which can't be made primary without modifying the card.

Yes, I tried that yesterday-- and all that was displayed was a blank screen with my desktop wallpaper. Not even any desktop icons. No launcher/taskbar.

---

### Post by Coder88 on 2013-09-07
One thing I am studying now is 'man nvidia-settings' (i know, RTFM !) and what I find interesting is :
#nvidia-settings --config=CONFIGFILE    <--- CONFIGFILE is an xorg.conf file to have X use rather than the default ~/.nvidia-settings-rc (which i do not even see in ~)
#nividia-settings --load-config-only      <--- useful to load a config file and send it to X then exit nvidia-settings, so put in ~/xinitrc ??

So I am wondering if I should/could use nvidia-settings to create and write a .conf file then put it in ~/mynvidia.conf and then create/edit ~/xinitrc  (I do not even see xinitrc in my home directory, hmm)

(to put into ~/xinitrc)
nvidia-settings --config=mynvidia.conf
nividia-settings --load-config-only

---

### Post by Coder88 on 2013-09-07
So I give up on the whole nvidia issue. I took the nvidia card out of my PC and connected my monitor to the motherboard ATI video. Booted Ubuntu and it works like a charm-- 1920x1080 and my menubar/taskbar at the bottom of the screen is there as it should. I don't think linux is ready for prime time yet as regards that nvidia card. Maybe when I get a deep understanding of how X works I might brave putting the card back in. Or i might go out to the local electronics store and buy a more powerful ATI card.  Because one thing that is a sigh is I can not do Compiz without a proper driver/card. I tried Compiz after booting with the ATI video off the motherboard and it just will not go; the compiz fusion icon does not display, and if I try running "compiz --replace" from the command line I get all sorts of complains/errors. Sigh.

---

### Post by carlwsnyder on 2013-09-07
> **Coder88 said:**
> One thing I am studying now is 'man nvidia-settings' (i know, RTFM !) and what I find interesting is :
#nvidia-settings --config=CONFIGFILE    <--- CONFIGFILE is an xorg.conf file to have X use rather than the default ~/.nvidia-settings-rc (which i do not even see in ~)
#nividia-settings --load-config-only      <--- useful to load a config file and send it to X then exit nvidia-settings, so put in ~/xinitrc ??

So I am wondering if I should/could use nvidia-settings to create and write a .conf file then put it in ~/mynvidia.conf and then create/edit ~/xinitrc  (I do not even see xinitrc in my home directory, hmm)

(to put into ~/xinitrc)
nvidia-settings --config=mynvidia.conf
nividia-settings --load-config-onlyThe **.nvidia-settings-rc** file is in your home directory (/home/username/ ), and you would probably have to view hidden files to find it if it exists.  The proper name for xinitrc is actually the hidden file **.xinitrc** -- again in your home directory.  Remember, Linux files/folders beginning with a full stop (.) are hidden.

---


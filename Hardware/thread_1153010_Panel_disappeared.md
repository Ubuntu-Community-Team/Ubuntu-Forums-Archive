---
title: "Panel disappeared"
date: 2009-05-08
forum: Hardware
---

### Post by Saghaulor on 2009-05-08
The taskbar disappeared.

I've discovered it might have to do with me removing evolution, which in turn removed gnome-panel.

I reinstalled gnome-panel. When I ran gnome panel it started up as the classic configuration, ie, a top and bottom panel.

Being that this is the netbook remix, there is only supposed to be one panel and the netbook-launcher is supposed to integrate into the top panel.

I am having no luck restoring things back to the default settings. 

I tried . . 
```
sudo dkpg-reconfigure gnome-panel
sudo dkpg-reconfigure netbook-launcher
```

This did not work. I'd like to fix it rather than do another reinstall.

Your assistance is greatly appreciated.

---

### Post by Saghaulor on 2009-05-08
More info,When I switch the desktop back to classic mode, the panels are present.

However, the top panel is still missing from the UNR mode.

---

### Post by pjalegria on 2009-05-08
Do you have compiz enable? make sure you have 'Visual Effects' turned off in Preferences->Appearance.

---

### Post by Saghaulor on 2009-05-08
Compiz is disabled.

I want to say it has something to do with a Netbook Panel or something.

---

### Post by Saghaulor on 2009-05-08
Everything seems to be normal under a new user id, so apparently it's just some fritzd settings. No biggie. It would still be nice to know how to fix it.

---

### Post by markhepworth on 2009-05-22
I had the same darn thing - but this thread clued me into the problem, so thank you.

I was clearing out a couple of applications that I'd either decided to replace (evolution) or had downloaded and decided not to keep (vlc, googleearth). Below is the history from synaptic. Obviously, I didn't imagine that evolution would drag some really important stuff out with it, like gnome-panel, and unr itself. I've reinstalled evolution and the packages it took, and on a reboot my unr top panel returned to exactly how I'd left it.

```
Completely removed the following packages:
evolution-common
evolution-data-server-common
evolution-documentation-en
googleearth
googleearth-data
vlc
vlc-data
vlc-nox

Removed the following packages:
evolution
evolution-data-server
evolution-indicator
evolution-plugins
fast-user-switch-applet
gnome-applets
gnome-panel
indicator-applet
indicator-messages
language-support-en
language-support-translations-en
libedataserverui1.2-8
libvlc2
libvlccore0
ubuntu-netbook-remix

```Obviously the moral of the story is to check what synaptic is proposing to remove - but why does evolution drag these unrelated packages out with it?

Maybe the op needs to restore some of these extra packages, like ubuntu-netbook-remix

---

### Post by victorgreen on 2009-06-06
Thanks a lot for this info guys. I had suspected some sort of update was the problem. Bloody evolution is impossible to get rid of easily.

---

### Post by Ferrat on 2009-06-06
The reason Evolution drags them with is really a dist setup problem I think, probably when the image is made it's made from either a automatic generation or an image that installs/installed evolution early on and these packages becomes installed wih Evolution, other packages use these but do not depend on them so when you uninstall Evolution the system sees it as pure clean up or Evolution is configured in to these packages and for some reason the system sees them as "broken" without and wanting to remove them. 

not sure which but those two seem like the most likely reason, but I agree it's a retarded that it even wants to remove stuff like that for a simple mail client.

---


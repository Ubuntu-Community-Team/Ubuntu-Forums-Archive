---
title: "Transmission in daemon mode w/ webUI?"
date: 2008-11-17
forum: General Help
---

### Post by Bllz on 2008-11-17
Hello,

I've been looking for a means to run transmission in the background as a daemon and use only its webUI (clutch) as an interface.

I'd like to do this in order to set up a dedicated bittorrent server, but I also would like this server's interface to be cleaner and less complicated than torrentflux's.

So far I can get the backend running by installing transmission-cli, and then running the command "transmission-daemon"

I can't find the config file anywhere, nor do i know how to activate the webUI.

thanks in advance!

---

### Post by geirha on 2008-11-17
It should be enabled by default. After starting transmission-deamon, try opening [http://localhost:9091](http://localhost:9091)

---

### Post by Bllz on 2008-11-19
> **geirha said:**
> It should be enabled by default. After starting transmission-deamon, try opening [http://localhost:9091](http://localhost:9091)

Thanks a lot for the help!  Who knew it was that simple...

One last question, do you know the location of the config file for transmission-cli?

Thanks again,
Bllz

---

### Post by Bllz on 2008-11-19
> **Bllz said:**
> Thanks a lot for the help!  Who knew it was that simple...

One last question, do you know the location of the config file for transmission-cli?

Thanks again,
Bllz

I just realized that there is a button at the bottom left of the screen that accesses the preference menu, but this menu looks a lot simpler than the one provided in the normal GUI interface.

I need to specify a SOCKS proxy for my tracker connections.  How can I do this?

---

### Post by geirha on 2008-11-19
Haven't used the cli much, but I would guess it uses the same settings file as the gtk-client. ~/.config/transmission/settings.json.

---

### Post by Bllz on 2008-11-19
Hmmm... I checked in ~/.config and there's only a "transmission-daemon" directory.  Within that directory there are directories titled "blocklist" "resume" and "torrents" but I don't see anything in any of those directories that resmbles a config file.  The only thing I can think of is ~/.config/tracker ... but is that related to transmission?  There are two files in that directory:  "tracker.cfg" and "tracker-applet.cfg"

These, however, appear to be related to search indexing...

---


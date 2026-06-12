---
title: "installing MPlayer Plugin for Ff 1.5.0.1"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by WaterWalker on 2006-02-17
I've just used Automatix to upgrade from Ff 1.5 to Ff 1.5.0.1.
But now my Mplayer Plugin now longer functions!
I've already tried to reinstall it both via Automatix and via Synaptic.
But nothing works.
What should I do?

---

### Post by souteneur3190 on 2006-02-17
uhh that wasnt an upgrade...that was a downgrade..firefox is at v.1.6 when you download ubuntu

---

### Post by souteneur3190 on 2006-02-17
i would suggest deleting it via synaptic and reinstalling it via synaptic

---

### Post by skierkegaard on 2006-02-17
Breezy comes with Firefox 1.0.7

---

### Post by WaterWalker on 2006-02-17
-I have already downloaded (and installed) Ubuntu for more than a month.
-I'm very sure that the last version is 1.5???(maybe your a bit confused with Ff 1.0.6 or Ff1.0.7.)

---

### Post by WaterWalker on 2006-02-17
[QUOTE=souteneur3190]i would suggest deleting it via synaptic and reinstalling it via synaptic[/QUOTE]
didn't work:(

---

### Post by seidel on 2006-03-13
WaterWalker,

I have firefox 1.5.0.1 installed and finally got mplayer working. I didn't use Automatix to install firefox I installed it manually by following the wiki here

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

That installed firefox to /opt/firefox
and plugins would be located in /opt/firefox/plugins

I opened Synaptic and installed "mozilla-mplayer"
That installed the plugins to the original firefox directory in /usr/lib/mozilla-firefox/plugins

Now you want to cd into that directory and copy anything with filename mplayer to the /opt/firefox/plugins dir

```

cd /usr/lib/mozilla-firefox/plugins
sudo cp mplayerplug-in*.so /opt/firefox/plugins/
sudo cp mplayerplug-in*.xpt /opt/firefox/plugins/

```

Now close firefox and open it back up and test it out. Hope this helps/works for you.

---


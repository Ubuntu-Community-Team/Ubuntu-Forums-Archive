---
title: "Home directory /home/tux not ours"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by linuxhippy on 2009-10-31
I just upgraded from ubuntu 9.04 to 9.10.  It was very easy and the only thing now that's messed up is my sound card.  When I first installed 9.04 I had the same problem...the card kept getting muted.  I did this to fix the card and save the settings a couple months ago:

sudo alsa force-reload
sudo alsactl store

That worked but now the card is muted again.  sudo alsa force-reload works fine but after sudo alsactl store I get this:

Home directory /home/tux not ours

my user is named tux.

What needs to be done?

---

### Post by geoaraujo on 2011-12-02
> **linuxhippy said:**
> I just upgraded from ubuntu 9.04 to 9.10.  It was very easy and the only thing now that's messed up is my sound card.  When I first installed 9.04 I had the same problem...the card kept getting muted.  I did this to fix the card and save the settings a couple months ago:

sudo alsa force-reload
sudo alsactl store

That worked but now the card is muted again.  sudo alsa force-reload works fine but after sudo alsactl store I get this:

Home directory /home/tux not ours

my user is named tux.

What needs to be done?

Two years later, it still occurs, Kubuntu 11.10. :(

---

### Post by Jose Catre-Vandis on 2011-12-02
Are you in the audio group?

---

### Post by geoaraujo on 2011-12-02
> **Jose Catre-Vandis said:**
> Are you in the audio group?
How can I know? Single user, so I suppose yes.

---

### Post by Jose Catre-Vandis on 2011-12-05
In a terminal:

**groups**

this should show you if you are in the admin group

or to look at all the groups

**nano /etc/group**

---

### Post by geoaraujo on 2011-12-05
> **Jose Catre-Vandis said:**
> In a terminal:

**groups**

this should show you if you are in the admin group

or to look at all the groups

**nano /etc/group**

It seems that I'm not: [B]
$ groups
george adm dialout cdrom plugdev lpadmin admin sambashare vboxusers

[/B]I've added audio, and it seems that I was able to save alsamixer settings. Thanks for the tip.

---


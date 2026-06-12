---
title: "playlists lost after amarok upgrade"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by kalagz on 2009-04-05
Hello every1,
i'm newbie in this forum and i know some things about linux. I'm not sure if this is the right place to post this and i'm sory if it is wrong.

I used to have ubuntu 8.10 and i upgraded to 9.04. Before the upgrade i used Amarok 1.4 or something. There i had lots of playlists with hundrends of songs organized. The problem is that after the upgrade there were no playlists. Before i upgrade my system, i didn't thought that i had to save a backup.
Is there a way i can get back my playlists? Something different than creating them again plz:D.

And something more. One more problem is that it couldn't play anything and just telling me "audio media device (name of my card) does not work.Falling back to default" if i remember well. I searched a little about this and after installing 2 files about phonon from the Synaptic PM it worked fine. Is there something else i have to do?

Thanks for your time,
Giorgos

---

### Post by bertolo on 2009-04-05
playlists are where you left them. try searching in amarok default folder.

---

### Post by futileissue on 2009-05-01
The files are probably still on your computer, as they were mine.  For some reason amarok2 did not import them when we upgraded Ubuntu.

The "default" folder is this: /home/YOURHOMEFOLDER/.kde/share/apps/amarok/playlists/

Where YOURHOMEFOLDER is your username.  Note that ".kde" is a hidden folder, so if you're browsing in nautilus you'll need to press "Ctrl+h" in order to see it.

Any old playlists should be ".m3u" files in that folder.  I added mine back by drag and dropping them into the Amarok2 playlist and then saving it as a new playlist.

Anyway, hope that helps.

---

### Post by fermulator on 2009-05-03
Apparently it's not there for me. - /home/multimedia/.kde/share/apps/amarok ... no "playlist" or "Playlist" or ".playlist", etc. ...

GONE?

I never changed the default location back in Ubuntu 8.10 / Amarok 1.4.  Why would upgrading to A2 delete all playlists?  Bad.

---


---
title: "Netjuke and M3U problems"
date: 2004-12-31
forum: General Help
---

### Post by NewbieNik on 2004-12-31
I have a server running Apache2 and hosting Netjuke Version 1. The problem is that I cant listen to the music from the web-interface on Ubuntu as they stream as .m3u files. Can anyone recommend a player or codec to play these?
I havelooked on google and other searches, but they al seem to recommend MPlayer which I have installed and it cant play them....Help me please, it's no fun and I'm cold and I can hear the wolves...................

---

### Post by dare2dreamer on 2005-01-02
```
sudo apt-get install xmms
```

And let the penguin drown out the wolves once again. ;-)

---

### Post by NewbieNik on 2005-01-02
Do penguins quack???? Will have to google the answer.

Have installed xmms as well, but the juke box contains mp3 files (Play fine on Totem) and wma (Cant play on any media-player).
I know some of the payers can handle wma, butTotem seems to be the only one that can handle M3U playlists.
I have used realplayer in the past on my XP (Spit to the side) system, but inux version says its missing the necessary files and I can't find them to install.

Starting to rock gently in my seat while murmering passages from "The Albatross" 
I can hear the voices....
Don't be paranoid, they only speak to me!!!

---

### Post by dare2dreamer on 2005-01-02
an m3u playlist is little more than a text file referencing the location of the mp3 files you want to play.

xmms does support playlists of several formats, including m3u.

man xmms or check [http://xmms.org](http://xmms.org) for more info.

---


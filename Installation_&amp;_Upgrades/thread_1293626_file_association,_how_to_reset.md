---
title: "file association, how to reset?"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by attilab on 2009-10-17
I had a VLC installed, I was playing with the skins, didn't like the last one (PS3 skin) and could not load back the default skin so I uninstall all at the end.
now, I want to watch the movies in my email attachnment, but won't play because an other program is associated with it (but that one doesn't exist anymore). How to remove the file (any) association? best to put all back to default? thanks

---

### Post by bunorama on 2009-10-22
Might have a look at this:
~/.local/share/applications/mimeapps.list

Linux had blueray and DIVX set to open with clamav heh.
Not sure where to associate like 'all video types' with 'vlc'

In KDE it's system settings -> advanced -> file associations for individual types.  

I noticed that banshee was listed above vlc on several, so I just did apt-get remove banshee, fixed those real quick.  When I did the same with totem, it didn't remove totem tho.  

And then there's the clamav ones that had no other association.  If you could multi-select the file types and set all those to a specific app, it would be a lot better.  Anyway, that is where mimeapps.list came in handy.

Still not sure if it was a good idea doing it that way, and it is not complete. there's lost more mime types not listed in that file.

---


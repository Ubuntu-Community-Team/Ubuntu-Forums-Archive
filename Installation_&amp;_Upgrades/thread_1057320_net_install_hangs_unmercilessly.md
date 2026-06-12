---
title: "net install hangs unmercilessly"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by umpalumap1985 on 2009-02-01
hi everyone, i have recently acquired an old(er) computer with no cd drive.  i then went through all the procedures to get pxe boot going (flawlessly), and copied the contents of the alternate install cd to a folder ubuntu in my /srv/http (apache root).  now when i boot off the network, boot goes well, and the installer works to the point where i choose a mirror.  i enter my ip 192.168.0.3:*porthere*.  i made sure that this is the port that i have apache listening on, and also that the port is forwarded in my router config.  when asked the name of the directory, i enter /ubuntu/, and then it just hangs.  just sits there at a blue screen with no words on it.  i really would appreciate any help i can get on this matter, as i have been trying to get a net install going on this box for almost two days now, and am almost at wits' end.
thank you in advance.

so it turned out i just need to change permissions on my apache root, and chmod -R 777 /srv/http/ubuntu did the trick.  woohoo!

---


---
title: "New install question"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by Frentraken on 2009-07-07
I'm looking at switching over to ubuntu or a veriant on my desktop pc permenantly and setting it as a file server and media center likely running XBMC. Now I've been running XP on it forever now and all my drives are formatted NTFS I have over 300 gigs of media stored across them. So I was wondering is it fully required to change these over or can they be left the way they are for reading and writing to? Or would it be a bettery plan to slowly convert everything to ext3?

---

### Post by PureLoneWolf on 2009-07-07
Hi there

I did basically the same as you, I moved files around to free up my main 500gb drive and then dedicated that to Ubuntu (with separate /, home and swap partitions)

The rest of my drives are NTFS and with a little help from pysdm (sudo apt-get install pysdm) I was able to automount them all on startup.

XBMC is fantastic once you get used to it aswell...I wouldn't be without it now.

Sorry, rambling - Short answer...no, you don't have to worry about migrating, although you will need some space to partition for ubuntu...

Hope that helped

---

### Post by Frentraken on 2009-07-07
Thanks, ya I plan on formatting out my windows partition so I can install Ubuntu into it. I was just worried about reading and writing to ntfs partitions from Ubuntu dind't know how well it would work out.

---

### Post by Sef on 2009-07-07
Once Ubuntu is installed - Applications > Add/Remove > Show: All Available Applications > Search: NTFS > tic top box > apply changes > apply > close.

That will allow Ubuntu to read and write to NTFS.

---


---
title: "[SOLVED] Scalpel help"
date: 2008-07-20
forum: General Help
---

### Post by spoketire on 2008-07-20
I'm trying to do some file carving on a disk image file using Scalpel. I haven't been able to find a whole lot of information on this program, so I was wondering if anyone around here is very experienced with it and could clear up some of my confusion.

1. Does scalpel go through the whole image file to find files, and then save them once this process is complete, or does it save the files as it goes?  Edit: I've found out this answer  myself since posting (it saves them after scanning the entire image).  The other questions still stand though.

2. Is there information on other file formats that could be added to the scalpel.conf file? I have tried looking for this on the web without luck. I am particularly interested in .blend and .mus.  I think I could probably put these formats into the config file if I knew the header and footer info for them, but I haven't been able to find that either.

3. Does scalpel find the exact same formats as foremost? I know scalpel is based on foremost, but foremost.conf has stuff like wma and mp3 where scalpel.conf does not.  Can these entries just be copied from one config file to the other?

---

### Post by spoketire on 2008-08-09
I've been able to gradually figure most of these answers myself.

2. I've had to find pretty much everything myself with a hex editor. There's not much documentation on the internet, at least for the file formats I needed.

BLEND: header: BLENDER_v
           footer: ENDB

MUS: header: ENIGMA BINARY FILE (these spaces are 20 in hex)
footer: hex: 130006000000

3. Yes

Maybe that will help someone else someday.

---


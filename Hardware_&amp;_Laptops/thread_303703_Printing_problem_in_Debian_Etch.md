---
title: "Printing problem in Debian Etch"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by patrickfromspain on 2006-11-20
First: hi there!

Second: why I am asking about a problem in etch? I wouldn't know a better community to ask ;) Also, I think dapper/edgy and etch have some things in common. 

Third: If I offend someone posting this: sorry. I'm posting here and not in other OS talk cause here it will be seen by more people :-? 

After installing Etch, and its updates, I installed the printer, Canon IP3000, using the turboprint driver. It prints ok, but there's a little problem: I can't get it to print 2 sheets on one side.

After exploring a bit more, I can't even set the printer preferences in turboprint xtpconfig, the printer oversees them (if I set 300dpi grayscale, it won't do it, as in cups it is set to RGB and 600dpi). In localhost:631 I can set some options.. but thats not a solution I like, as there I can't set 2 pages per sheet on the same side (only double sided).

I don't know where to start looking at, as in ubuntu it works just fine. I had problems using dapper, but after compiling cups they went away; in edgy it works like a charm. In etch, compiling latest cups doesn't help.

Any ideas?

---

### Post by patrickfromspain on 2006-11-21
a little update... if I open xtpconfig as root user, and there set grayscale and draft quality, it works fine. However, still  no joy with the 2 pages per sheet feature; I've tried opening gpdf as root, but nothing.

---


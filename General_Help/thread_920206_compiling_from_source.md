---
title: "compiling from source"
date: 2008-09-15
forum: General Help
---

### Post by adult swim on 2008-09-15
im building vlc 0.9.2 from source.  this is the first time ive compiled and ran into some problems, well not really problems but inconveniences.  i keep on having to manually install packages that i already have except they are the -dev version to get ./configure to work.  is there a way to get all of the dependencies updated fast that i do not know about?

---

### Post by Vivaldi Gloria on 2008-09-15
> **adult swim said:**
> im building vlc 0.9.2 from source.  this is the first time ive compiled and ran into some problems, well not really problems but inconveniences.  i keep on having to manually install packages that i already have except they are the -dev version to get ./configure to work.  is there a way to get all of the dependencies updated fast that i do not know about?

I tried compiling vlc 0.9.2 on Hardy a week ago. I failed. I installed all dependencies. I don't remember the exact details but there is a circular dependency so I couldn't install two dependencies at the sime time. I also tried the deb file from [[COLOR="Sienna"]here[/COLOR]]("http://nightlies.videolan.org/") but it also fails.

I suggest you wait for intrepid, we are almost there.

---

### Post by adult swim on 2008-09-15
i finally got it to compile on intrepid.  for some reason it wouldnt recognize my libavutil-dev but i flagged that out of the ./configure and it worked.

---

### Post by Vivaldi Gloria on 2008-09-15
> **adult swim said:**
> i finally got it to compile on intrepid. 

I thought you had hardy. I guess even the deb file I linked works in intrepid. Anyway, have fun.

---


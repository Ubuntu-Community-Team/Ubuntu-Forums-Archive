---
title: "[SOLVED] Fix This"
date: 2008-09-18
forum: General Help
---

### Post by ManyBeers on 2008-09-18
[IMG][[IMG]http://img504.imageshack.us/img504/2475/screenshotbn5.th.png[/IMG]](http://img504.imageshack.us/my.php?image=screenshotbn5.png)[/IMG]

When I min imize Rhythmbox these black border lines always 
appear. Why? My Sony laptop's video card is an ATI Rage Mobility
M1(8 mbs ram) and as far as I know works perfectly. Is this a videocard 
problem? It does it on all Windows when minimizing.

---

### Post by -Zeus- on 2008-09-18
i think it's a video card problem.  You should be able to disable it in Appearance

---

### Post by ManyBeers on 2008-09-18
> **-Zeus- said:**
> i think it's a video card problem.  You should be able to disable it in Appearance
Disable what?

---

### Post by aragorn2909 on 2008-09-18
Old trick,

In a terminal
```
gconf-editor
```

navigate to

apps --> metacity --> general

and ensure "reduced_resources" is checked.  There are some trade-offs, but this should remove those black lines.

---

### Post by ManyBeers on 2008-09-18
> **aragorn2909 said:**
> Old trick,

In a terminal
```
gconf-editor
```

navigate to

apps --> metacity --> general

and ensure "reduced_resources" is checked.  There are some trade-offs, but this should remove those black lines.

Thanks Aragorn. It worked.

---

### Post by -Zeus- on 2008-09-18
> **ManyBeers said:**
> Disable what?

Yeah sorry, I have no idea what I was thinking, that sucked.  Thanks, Aragorn.

---

### Post by aragorn2909 on 2008-09-18
Glad it worked for you.  :)

---


---
title: "wget -r (only recursive from within a specific directory)"
date: 2008-08-09
forum: General Help
---

### Post by Th3Professor on 2008-08-09
It's been ages since I've used wget... though it looks like it could come in handy for one particular purpose... to recursively download everything contained within a specific directory. However, when invoking the recursive flag/option, it ends up downloading a lot more than what I asked for.

Example:

wget -r [http://site.com/directoryZ/](http://site.com/directoryZ/)

I only want to download recursively from "directoryZ" as a starting point.

It ended up doing this:
site.com/
./directoryA/
./directoryB/
etc.

How do I restrict recursive to only download all that is contained within one specific subdirectory?

Thank you!

---

### Post by PadreSol on 2008-08-09
-np is what you want to try

---

### Post by Th3Professor on 2008-08-09
d'oh!

...and I read that, too, in the man file! lol thx :)

---


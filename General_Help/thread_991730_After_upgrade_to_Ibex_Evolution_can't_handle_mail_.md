---
title: "After upgrade to Ibex: Evolution can't handle mail folder of older Evolution version"
date: 2008-11-24
forum: General Help
---

### Post by tbraun on 2008-11-24
Hello!

I have just done a manual upgrade from 7.10 to 8.10. I formatted my root partition, but left my /home partition untouched.

When I then started Evolution, I found to my surprise that it wasn't able to make sense of the already existing ~/.evolution folder. It doesn't seem to understand anything that's in there and pops up a wizard to guide me through a completely new install.

Any idea what I can do to make it understand the old Evolution folder?

Thank you very much...

---

### Post by jimbaker on 2008-12-13
I just did this:
1) Make a backup of my .evolution directory.
2) Use wizard to create a fake evolution account (just put in garbage)
3) Remove or rename the fake evolution account
4) Move your .evolution backup back to .evolution
-- I actually have my .evolution directory on a NFS share
-- So I create a symbolic link from .evolution to my network .evolution dir.

---


---
title: "Locate/Find Folder Names"
date: 2008-09-29
forum: General Help
---

### Post by blacksunseven on 2008-09-29
Hi, I want to use locate (or find, if I must) to find directories matching a name with or without spaces in it. I have search high and low for the best way to do this - and have some methods with find - but they take forever to complete (crashes kfind and catfish didn't last long either). I'm not looking to do anything complicated, I just want to be able to run something like:

locate -i PATTERN1\ PATTERN1/
or
locate -i PATTERN3_PATTERN4/

and only display folder names, not any contents. I was thinking this could be done by somehow grep piping anything with an extension on it or anything after the last forward slash so that it would not be displayed in the results.

Thanks for any help!

---

### Post by kpkeerthi on 2008-09-29
find /path/to/search/from -type d -iname 'PATTERN'

---

### Post by blacksunseven on 2008-09-29
> **kpkeerthi said:**
> find /path/to/search/from -type d -iname 'PATTERN'

This produces accurate results but is there no way to do this using locate? The above command and options works but takes about 2 minutes to complete. I don't think its possible to build a find database, thought that would be nice, but if anyone knows of a similar method using locate/slocate, I'd appreciate it.

Thanks, kpkeerthi, by the way.

---


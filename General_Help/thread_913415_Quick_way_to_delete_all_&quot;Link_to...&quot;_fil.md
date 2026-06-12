---
title: "Quick way to delete all &quot;Link to...&quot; files?"
date: 2008-09-07
forum: General Help
---

### Post by svivian on 2008-09-07
I want to remove all files with the type "Link to PNG image" but keep the normal PNG images (ie the ones being linked to). Is there a quick way to do this? I've got multiple files among several folders so it's not straightforward to delete them by hand.

---

### Post by sdennie on 2008-09-07
First, from the directory you have your pictures stored, run:

```

find . -type l -iname "*.png"

```

Make absolutely sure that it only lists the files that you are looking for.  Then, to delete those files, run:

```

find . -type l -iname "*.png" -delete

```

---


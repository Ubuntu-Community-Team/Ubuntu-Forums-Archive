---
title: "extract one file from a .dar backup"
date: 2008-07-15
forum: General Help
---

### Post by editrix on 2008-07-15
Background:

In Dapper, I created a huge .dar file of documents in my Windows partition, using Kdar, and burned it to CD.

Now, I'm on Hardy, and Kdar is no longer in the repositories.

I've discovered hubackup, but apparently there's a bug in it (what else is new?) so it won't restore.

Problem:

I just need to get a few files from that Windows backup. But the man page for DAR is impenetrable. Can someone please give me the command-line code for viewing what's in that .dar file, and then how to extract one file?

Alternative option:

If I install an older version of Kdar, will that conflict with anything?

---

### Post by tech0007 on 2008-07-15
to view the contents

dar -l [darfile]

to extract

dar -x [darfile]

---


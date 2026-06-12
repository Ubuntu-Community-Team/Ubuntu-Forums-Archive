---
title: "e2fsck error"
date: 2008-11-01
forum: General Help
---

### Post by sddfdds on 2008-11-01
I had my system lock up and crash a couple days ago, and it seems to have trashed the filesystem on my external hard drive a little bit.  I ran e2fsck and it did all kinds of assorted crap with re-allocating blocks and whatnot.  I re-ran it to make sure everything was cleaned up, and I get the following message several times over:

/dev/sdg1: Duplicate entry '.................................................' found.
     Marking /lost+found/#549377 (549377) to be rebuilt.

Theres a bunch of these, some have ..............mp3 in the quotes, or just ..........3, and some say Marking /a/folder/on/the/drive instead of lost+found.  I tried running with -p as well, but it still comes up with all the stuff.  What does it mean?

Edit: Also of note, when run without -f, e2fsck reports it as clean.  The duplicate entry stuff only appears when -f'ed.

---


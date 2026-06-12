---
title: "Update Manager Spurious Update File"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by bodhigreenman on 2009-06-23
I have just been checking my Update Manager, and one of the updates is this.

Update is called 'File' 'Determines file type using "magic" numbers'

Changes is;

Version 4.26-2ubuntu4: 

  * 220-magic-update-erlang.dpatch: Escape spaces in Erlang magic to avoid
    misidentifications, particularly PostScript files produced on Tuesdays
    (LP: #248619).

Description

Starting with version 4, the file command is not much more than a wrapper around the "magic" library.

I am reluctant to run updates on this system without checking, am I being over cautious?

---


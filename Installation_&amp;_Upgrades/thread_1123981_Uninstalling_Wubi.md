---
title: "Uninstalling Wubi"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by Muscovy on 2009-04-12
I need to remove wubi from my computer. I've removed it in the remove programs tool, and I've deleted all files I could find.
I'm told that there's some extra-hidden files or similar that I need to delete before it stops trying to boot a removed OS.
How can I find them?

---

### Post by ispyamoose on 2009-04-12
Which version of Ubuntu were you getting rid of?

8.10 is straight forward. Just run the uninstaller, and delete any of the remaining folders.

9.04 beta has a bug that says it doesn't have the permissions to remove Ubuntu, but it does it anyway. On that one you can just delete the Wubi and Ubuntu folders after running the uninstaller.


Be sure to check back with the boot.ini file to make sure that the Ubuntu line is removed, but be sure to "Check all boot paths" to ensure that your Microsoft OS will still boot.

---


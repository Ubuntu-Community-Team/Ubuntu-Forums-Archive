---
title: "wubi doesn't  work"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by RuralHunter on 2009-07-08
I downloaded ubuntu 9.04 desktop version and tried to install it without burning to CD. So I ran the wubi.exe in the disk. But somehow wubi.exe doesn't work with me.  When I select "boot now" or "boot later", it just does nothing and returns to the first welcome screen. If I choose "help me boot from cd", wubi just keeps copying files forever. I am totally confused what it is copying. I checked c:/ubuntu. One of the files in it keeps growing and it reaches more than 10G and fills up my c driver then the installer fails. I even copied wubi to another empty driver with nothing, but it just behaviors the same thing. It's very very strange where it copies so much data from. The last lines of the log shows this:
07-06 09:22 DEBUG  TaskList: ## Finished copy_installation_files
07-06 09:22 DEBUG  TaskList: ## Running get_iso...
07-06 09:22 DEBUG  TaskList: New task copy_file
07-06 09:22 DEBUG  TaskList: ### Running copy_file...

I tried the latest r134 but nothing is changed. Anyone can help?

---


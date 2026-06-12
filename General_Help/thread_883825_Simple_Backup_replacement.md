---
title: "Simple Backup replacement?"
date: 2008-08-08
forum: General Help
---

### Post by x1a4 on 2008-08-08
Hi,

I'm using Simple Backup right now, but it just doesn't work very well.  What other backup tool can I use?  Ideally, one that can work in the background (I want to backup automatically at night), do incremental backups, logarithmic purging and have FTP support (I'm backing up to a FTP account). 

Thank you.

---

### Post by Roger D on 2008-08-12
Hi

I'm right with you. Trying to use Simple Backup is really frustrating - it seems to have just the functionality the desktop user requires, but, as far as I can tell, it just doesn't work reliably. An absolutely fatal flaw in a piece of software performing such a crtical function. I have three basic problems:

1 There's no feedback on progress. What happens if you shutdown in the middle of a backup operation?

2 It doesn't always work. Running experiments with the manual backup option, and backup now, I get three different results.

(a) A backup file is created and I can do a restore
(b) What seems to be a  backup file is created, but when I attempt a restore I'm told there's no backup file
(c) No backup file is created. I've watched progress via top, and the configuration process seems to run briefly, followed by gzip, which runs for several minutes, then nothing seems to happen

3 When I create a second configuration setting, what happens to the first one? This seems an absolutely basic question, but try as I might, I can't find the answer any where.

Regettably I've come to the conclusion that Ubuntu just doesn't have a fail-safe GUI-based backup utility. I know there are users out there who claim to be happy with Simple Backup, but I seriously wonder whether they've actually used the program in anger, i.e. to do a major restore after a hard disk failure. My basic backup strategy is to collect all my important files into a single folder, which I copy onto an external hard disk on a regular basis. It's crude, time consuming, but I know it works.

Roger D

---


---
title: "Compare Local to FTP?"
date: 2008-07-23
forum: General Help
---

### Post by davidshq on 2008-07-23
Wondering if anyone can recommend a good application that allows a comparison of files on a local machine to those residing on an FTP account? I'm using Windows Vista on the workstation and Ubuntu Linux on the server. Thanks.
David.

---

### Post by cpetercarter on 2008-07-23
Most ftp programmes have a "synchronise these directories" functions. You highlight the directory in the "workstation" panel and the corresponding directory in the "remote server" panel, and the function will then list for you the files which are in one directory but not in the other, and files which are present in both but which are different in size. (NB the FTP programme does not do a bit by bit comparison). You are then given options to upload/download missing or changed files. Is this the sort of thing you are looking for?
I generally use the FireFTP extension in Firefox. The function can be accessed via Tools > Sync directories and subdirectories.

---

### Post by fragos on 2008-07-24
Unison is available for Windows and Linux. I've used a memory stick as the sharing media between XP and Ubuntu. You can also mount shared folder on Linux which originate on Windows. Unison will sync the two systems with the shared folders.

---


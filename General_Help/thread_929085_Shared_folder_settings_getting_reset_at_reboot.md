---
title: "Shared folder settings getting reset at reboot"
date: 2008-09-24
forum: General Help
---

### Post by Evleos on 2008-09-24
:confused:

Hi. I have collected all my unused hard drives into a file server, seeking to utilize all my computer parts. The plan is to put a shared folder onto every hard drive, so that I can store files from other computers (XP/Ubuntu).  

But I have encountered a weird problem; every time i reboot the computer, the shared-folder settings are removed on every folder but the my shared folder in my "home folder" (yes I'm a Linux noob).  

This is what I have done to the disks in question:
- formatted
- chown username diskxx
- created a folder in the new media
- enabled sharing of this folder

As long as I don't reboot my server, things work fine...


What am I doing wrong?

---

### Post by Evleos on 2008-09-25
Please? :)

---

### Post by marcopauloferreira on 2008-10-11
Try activating the option that allows others to write onto the folder you are trying to share.

It worked for me. I was having the same problem... Apparently it seems that Ubuntu doesn't keep the shared settings if a folder is shared as 'Read Only'!

Just keep in mind not to put any important files in the Shared Folder and it should work just fine!

:)

---


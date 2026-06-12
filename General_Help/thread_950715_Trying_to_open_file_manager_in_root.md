---
title: "Trying to open file manager in root"
date: 2008-10-17
forum: General Help
---

### Post by G-Dub on 2008-10-17
Hello, I am having difficulties copying files from DVD I burned on a windows machine. It's say I don't have permission. So I tried opening the root file manager by using this code:
```
kdesudo konqueror
```
This opened up konqueror in Root but it doesn't see and media attached and there is nothing in my home folder! How am i supposed to change the permission on this DVD?

---

### Post by crom.osec on 2008-10-17
1. Usually your optic drives (DVD) are mounted read-only so you can't change the permissions (except for the case when you re-write it).
2. If you are not able to see the DVD content you need to add proper rights to your user (I doubt that this is the case).
3. If you try to copy your DVD contents to disk, you can do it only in your own folders. You can change the ownership of a folder using from konsole:
 chown -R yourUserName:yourGroupName folderPath
For example if your user name is GDUB and you want to change the ownership of folder /aaaa you should (usually) use:
 chown -R GDUB:GDUB /aaaa
(-R specifies that you want to change the ownership recursively)

---


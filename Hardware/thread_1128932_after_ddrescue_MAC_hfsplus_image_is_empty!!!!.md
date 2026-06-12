---
title: "after ddrescue MAC hfsplus image is empty!!!!"
date: 2009-04-18
forum: Hardware
---

### Post by martine1212 on 2009-04-18
Hello everybody:

I have a failed 80GB MAC drive hfsplus partition. I tried ddrescue and it seems it read the whole drive and created a 80GB image with basically no problems.

Now when trying to mount the .img file I used

 sudo mount -o loop -t hfsplus path to MAC img file. path to mounting directory

It mounts but the mounted image shows nothing!!! the whole thing is empty.
No directories, no files...

Clicking on properties:
Contents: nothing

Does anybody have any advice???
The failed harddrive is connected with a USB adapter... I can see the users and everthing but not the files since I am not the user (user 501).

HELP, HELP

---


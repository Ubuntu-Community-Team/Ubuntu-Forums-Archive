---
title: "creating image from another pc and installing"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2009-09-17
probably the title of this isn't enough to explain what i mean.

lemme explain...
i have a 9.04 which i messed up when i did a manual fsck while having the drive mounted!!I don't want to reinstall it over again (rather wait for the new release and upgrade)However waiting for a CD will take long time after the release so i was thinking of the options that i have considering that i have a slow dial-up connection.

My friend though has a broadband connection (with ubuntu of course) so i thought why not get him to upgrade first and then take a back up of his system and install it on mine(kinda like back up and restore, except that the restore will be on a different PC) or else may be i can download the upgrade  to an tar file and directly install it after copying it.

i know there is some way but i dont know how to.so could someone help me with the command to back up (excluding probably the files that are system specific,else i could land up with my friend's personal docs and preferences and config)just the basic system and then replace  my existing 9.0 with the new one.

this is like we do in windows where the installation file can be copied over to another PC and installed.
i have come across this command to back up bu still need to verify the correct one.

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

---

### Post by gordintoronto on 2009-09-18
You want remastersys.

---


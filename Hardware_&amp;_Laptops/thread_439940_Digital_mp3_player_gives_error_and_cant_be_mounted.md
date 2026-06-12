---
title: "Digital mp3 player gives error and cant be mounted"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by nerubian on 2007-05-11
hi.i have a minton digital mp3 player.i am running Kubuntu 7.04.when i plugged mp3 player and get dmesg:

[ 4567.356369] sdb : READ CAPACITY failed.
[ 4567.356371] sdb : status=1, message=00, host=0, driver=08
[ 4567.356377] sd: Current: sense key: Hardware Error
[ 4567.356380] Additional sense: Logical unit failure
[ 4567.398332] sdb: test WP failed, assume Write Enabled
[ 4567.398341] sdb: assuming drive cache: write through

and when i enter "mkdosfs -I /devsdb" i get

mkdosfs 2.11 (12 Mar 2005)
mkdosfs: Attempting to create a too large file system

I also have a problem with my mp3 player.When i turned it on without plugging in, it says me "media error, REFORMAT AS FAT16"

Is it possible to mount this device on ubuntu and reformat it as fat16?gparted doesnt see mp3 player.also when i open gparted as SUDO, I cant have delete, format,resize privileges.is it because of Kubuntu?

I think my device has a problem and needs to be formatted.But ubuntu cant see device.any HELP?
Edit/Delete Message

---


---
title: "ntfs backup to external hdd through ubuntu"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by peedeeramone on 2007-06-15
allright i have a dead xp install, but it had a bunch of stuff i wanted to save, but i havent been able fix it. i didnt want to just delete it so i decided i want to just store it away on my new 500gb external hd. now im in ubuntu and im not sure whats the easiest way to go about doing this.

i just want to say again that the partition is corrupted, and i'm not sure if it will even work, so if you think i should just say forget the whole save the corpse thing, i guess i will.

now i have partimage, but i dont have the space to save the partition image... i want it to save it straight to the exhd if possible.

allright thanks for the input

---

### Post by DagMan on 2007-06-15
if you want to just save data, like files off of it, it will just be a question of wheather or not you can mount the partition in Ubuntu or if it's corrupted really really bad as in a failing disk or messed up MBR.  If you can mount it then you should be able to plug in your external drive and copy any data to the external drive but be warned that XP encrypts the contents of some folders unless the user did not have a password associated with the account so recovery of some things may be possible but the data would be unusable.  It was a Microsoft security feature.  You can't just reinstall Windows and expect it to use the same decryption key either... perhaps from the same install disk with the same username and password... not really sure, and I'm not clear on which files get encrypted.  I think it's the Documents and Settings which would include day to day work.

If you want to image the partition for later restoration of the OS then it's a differant thing and you would want to use partimage or something similar, but I've never used it to give any help.

Here is some info on mounting windows drives [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows)

External drives usually mount themselves automatically but if you have trouble they can be mounted manually as well.

---

### Post by peedeeramone on 2007-06-16
nah see i tried all that i mean im pretty sure the whole partition is botched, it wont mount and no checkdisk will fix it. its just that i really wanted to get some of the data off of it so i wanted to keep a copy, just not on my laptop that doesnt have an extremely large hard drive

i was just trying to basically image the partition but save it straight to the external hard drive

---


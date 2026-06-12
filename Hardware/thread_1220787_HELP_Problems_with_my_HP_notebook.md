---
title: "HELP: Problems with my HP notebook"
date: 2009-07-23
forum: Hardware
---

### Post by thegyurus on 2009-07-23
I have an HP Pavillion dv7 series notebook and just installed 32 bit version of ubuntu 9.04 using dualboot config with vista. The login prompt sound did not sound out as it should have instead it hung on the first note in a stuttered loop. I have eliminated that problem but have no sound whatsoever since then. If anyone has a solution to this problem please let me know. I am a beginner learning linux with a friend.

---

### Post by AzT3K on 2009-07-23
Hi there,

First of all you should go with amd64 version.  I have a dv7 laptop running that.  However that's beside the point and certainly not your problem... ;)

You need to add these lines to the end of your /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

type this in the terminal:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
``` 

and paste in the above options to the end of the file.

to make the changes active; restart or run

```
alsa reload
```

This worked for me and I found the solution here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424)

---

### Post by thegyurus on 2009-07-25
Hi there
Thanks for the tip unfortunately it did not work for me. I have tried everything to to avail. Looks like I may have to take laptop to a computer place. Do you know of any place in Perth Western Australia which deals with ubuntu ?

---


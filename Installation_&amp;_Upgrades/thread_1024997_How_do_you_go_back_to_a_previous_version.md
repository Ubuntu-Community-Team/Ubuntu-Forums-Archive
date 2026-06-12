---
title: "How do you go back to a previous version?"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by Sour Mash on 2008-12-29
IF I can't fix my upgrade (separate thread) is there a way to roll back to the old version? I upgraded from 8.04.1 to 8.10.

Thanks

---

### Post by Therion on 2008-12-29
That would require a fresh install.

---

### Post by Sour Mash on 2008-12-29
](*,) What a PITA, not the end of the world but you know what I mean :confused:

---

### Post by darkstaar on 2008-12-29
If you have your /home on a separate partition, it's easy and painless. I just completed such an operation on my own system this morning.

---

### Post by Sour Mash on 2008-12-29
as I don't know what /home is then I guess I don't :-)

I just did a full install and followed the defaults (I'm very new to Linux)

---

### Post by darkstaar on 2008-12-29
/home is where your users' data and settings are stored. It's somewhat analogous to the "My Documents" folder in Windows XP (but not exactly).

For example, if your username on your system is sourmash then your data would reside in /home/sourmash .

As your /home directory is likely on your main (only) linux partition and you don't have a lot of saved files, it might be easiest to simply back up those files that are important to you onto some external media and do a normal reinstallation of 8.04. Then you can restore your data once your system is up and running again under 8.04.

---

### Post by Sour Mash on 2008-12-30
Thanks for that - can you point me at a work through to set up /home in the way you suggest please. I can then reinstall and "protect" myself for the next crash :-)

There's nothing of any consequence on this machine, it was a Christmas present for my daughter but it's turned into a project!

---

### Post by Partyboi2 on 2008-12-30
Here is a howto move your /home folder to its own partition.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

As mentioned you can always do a backup of your files then do a clean install and create a new /home partition when installing.

---

### Post by Bill Roberts on 2009-05-07
> **darkstaar said:**
> If you have your /home on a separate partition, it's easy and painless. I just completed such an operation on my own system this morning.

What are the steps necessary?

Here are my partitions:
/dev/md0 /boot
/dev/md1 swap
/dev/md2 /
/dev/md3 /usr
/dev/md4 /var
/dev/md5 /tmp
/dev/md6 /home

They are all software RAID

---


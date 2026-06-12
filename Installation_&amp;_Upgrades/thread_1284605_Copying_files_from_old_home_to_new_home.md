---
title: "Copying files from old /home to new /home"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by rob2uk on 2009-10-06
Hi there,

I think I've done something *really* daft...

I left my LinuxMint 7 PC on while I was at work, and we had a power cut, which completely hosed my install and left me with a non-bootable system.

Luckily I had a seperate /home partition, which seemed unaffected when I booted using the Mint 7 livecd.

I tried re-installing Mint using Ubiquity, but due to a known bug ([https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/258603]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/258603")), I couldn't use the same login name as the original install, so I was forced to think up something else (ie - I added a 2 to the end of it ;) )

Once I had a bootable system I opened a terminal window, and used

```
gksu nautilus
```

to copy everything from the old user's home folder to the new user's home folder.

Now what I need to do is take ownership of every folder, subfolder and file in new user's home. I'm certain it can be done with a single chown command in the CLI, but it's bloody late in the evening and I don't want to risk having to do yet another re-install or possibly losing all of my files.

Any help would be very much appreciated :)

---

### Post by terazen on 2009-10-06
The -R option of chown goes recursively through a folder.  Is that what you mean?  ```
sudo chown -R username /home/username
```

---

### Post by rob2uk on 2009-10-06
Something like that...

Tried that command, but it says:

```
chown: cannot access `/home/rob2/.gvfs': Permission denied

```


EDIT: Ignore that, despite it throwing up an error message, I now seem to have ownership of everything.

Thanks :D

---


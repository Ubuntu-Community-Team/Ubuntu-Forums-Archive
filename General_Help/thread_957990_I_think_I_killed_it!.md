---
title: "I think I killed it!"
date: 2008-10-24
forum: General Help
---

### Post by lakotajames on 2008-10-24
I was trying to do this: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
I did not use a livecd, because i was going to move my /home to another harddrive.
i got to this line: find . -depth -print0 | cpio --null --sparse -pvd /new/
after a while, I decided that it was taking to long so I Crtl-Ced out of it.  I didn't think that I could be messing anything up, because I never messed with the partitions on the harddrive I am using now, and I thought that particular line only copied files, but didn't change the original.  After I stopped it, I tried to open firefox. nothing happened.  then i clicked it again, and it said it was already running.  so I did "killall firefox" and tried again, still nothing.  So i logged out.  I tried to log back in, and it gave me an error message (which i was too stupid to write down) and wouldn't let me log in. I tried the other users with the same results. So i rebooted in "recovery mode" and ran root terminal.  I looked to see if my home folder was gone, but it wasn't.  then i looked to see how much got copied before i stopped the command.  Only my home folder had been moved, and not all of it.  none of the other users folders had been touched.  so i tried to continue to boot (or whatever the menu option is).  It now brought up the log in screen, but it was in 800*600 resolution.  I logged in as me, and it alowed me to.  It is still in 800*600.  also, firefox does not work (I am using epiphany right now).  What do I do?

---

### Post by lakotajames on 2008-10-24
Ok, now firefox just started, but it isn't displaying my homepage (google reader).  It does have the name in the titlebar, though.  I googled a little and decided to try EnvtNG to configure the drivers because I remember having low resolution when I first installed, and then had to add restricted drivers.  It crashed, saying it couldnt install the drivers.  So I uninstalled them.  then update manager came up and said I had updates: the drivers and wine.  so now I am updating.

---

### Post by lakotajames on 2008-10-24
this is what happened:

E: /var/cache/apt/archives/wine_1.1.7~winehq0~ubuntu~8.04-0ubuntu1_i386.deb: failed in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/nvidia-new-kernel-source-envy_173.14.12+2.6.24.503-503.30_i386.deb: failed in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/nvidia-glx-new-envy_173.14.12+2.6.24.503-503.30_i386.deb: failed in buffer_write(fd) (10, ret=-1)

---

### Post by lakotajames on 2008-10-24
ok, now I just realized that nautilus says I have 0 bytes left of free space.  that must be why I can't install updates.  What did I do to fill up all the space?  the new partition I was planning on using for home is mounted at /newhome, and it has 0 bytes left also.

---


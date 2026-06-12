---
title: "Wanting to switch to Ubuntu"
date: 2008-08-22
forum: General Help
---

### Post by tendency2corrupt on 2008-08-22
Right now I'm currently using windows Vista, which runs horribly. I've been learning how to use linux from dual booting for about a year now. Windows keeps crashing on me over the littlest things & I've had it with reinstalling. I was thinking about installing a windows os inside of virtualbox from within Ubuntu. The reason I still want to use windows is for recording music, backing up dvds, & so I can set up a static IP address for torrents (unless someone can point me in the right direction on how to set one up in Ubuntu). Would the limitations of virtualbox keep me from doing such things?

---

### Post by ctswhole on 2008-08-22
I think you might run into some snags trying to do what you said inside a virtual machine.  I'm able to run Vista quite nicely through Virtualbox, but the graphics are limited.  Everything looks the same, but if I try to play mahjong I get warning messages about graphic card issues.

Now what I'm saying is not the do all, end all of virtual machines, but this has been my experience so far in that area.

---

### Post by tendency2corrupt on 2008-08-22
Well what I'm asking is, will the recording features on my dvd drives & the recording input still be functional. I haven't looked into dvd software in Ubuntu all that much, maybe there's something that I could use? As for recording, I need Windows for that.

---

### Post by ugm6hr on 2008-08-22
Not sure about the recording music issue - but backing up DVDs & static IP can be done from within Ubuntu.

Network Manager doesn't like static IP - but you can turn off "roaming" and set static IP.  Easy for a desktop, but a bit of a pain for laptops (which may need to roam).  If you need to roam - look into Wicd as an alternative.

---

### Post by tendency2corrupt on 2008-08-22
How would I go about turning off roaming & setting up a static IP address? Last time I tried following directions off some website, I ended up screwing up my internet connection.

---

### Post by ugm6hr on 2008-08-22
I'm on Xubuntu at the moment - so this is from memory.

Wired or Wireless?  If wired...


In System menu, look for the Network option.
Highlight wired network, and click properties.
Untick "roaming enabled"
Put in the relevant details in the various boxes.

All done.

---

### Post by tendency2corrupt on 2008-08-22
I'm going to give that a try here in a few minutes. :)
I appreciate the help.

---

### Post by ctswhole on 2008-08-22
To the best of my knowledge you can't burn a cd/dvd in a virtual machine.  At least not on Virtualbox.  I do know you can set up a shared folder between the host machine and virtual machine so it would be possible to transfer anything you made in a VM to the host and burn it from there.  There are several good burning programs to choose from in Ubuntu, I would recommend either Brasero or K3B

---


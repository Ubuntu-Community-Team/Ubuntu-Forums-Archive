---
title: "Cross-over wire connection"
date: 2010-03-17
forum: Hardware
---

### Post by Overthere on 2010-03-17
Hi to all :D,
I have connected my Xubuntu laptop to a Windows XP pc, but I don't know where to find the relative files..
Any ideas?

Thanks in advance,
Brian

---

### Post by Overthere on 2010-03-18
Ok, I admit I'm bumping.. but this thing is really bugging me.
Can Xubuntu and Windows XP "see" each other, either through wireless LAN modem or other approach?
I can "see" the XP computer from my Gigolo app, but it says "no host found." What do I need to do to enter?

Thanks to anyone and all,
Brian ;)

---

### Post by jrssystemsnet on 2010-03-18
You have to do more than just stick a crossover cable in between the machines.  You also need to statically address the interfaces on each machine so that they're on the same subnet; for example you might make the XP box 192.168.0.1 and the Ubuntu box 192.168.0.2, both with subnet mask 255.255.255.0.

You also need to be sharing the files you want to copy from one machine or the other; you might share a folder from the XP box and browse to it from the Ubuntu box, or you might set up Samba on the Ubuntu box and browse to it from the XP box.  Either way, you're going to have to actually set up SMB/CIFS sharing from one box or the other.  (Unless you choose to use FTP or some other service, in which case you'll have to set *that* up.)

I have no idea what "my Gigolo app" is, so I can't help you with that.

---

### Post by Overthere on 2010-03-19
Thanks much jrssystemsnet,
What you suggest makes sense, I'll have to do some bookwork to learn up on it all.
I have an application for Xubuntu called Gigolo, which indicates remote filesystems. It does tell me that there's another computer (even without the cross-over cable, using just wireless), but indicates that there are "no hosts found."
So I suppose that's where the problem is, I just need to learn where to enter on the system to connect it.
Any other thoughts of course much appreciated.

Ciao!
Brian

---

### Post by jrssystemsnet on 2010-03-19
If both machines are on the same wireless network, forget about the crossover cable - you don't need it.

I found a page describing "gigolo" - that won't particularly help you; it's more of a shortcut than an actual connection method.  Your real problem is that you have to make sure that your XP machine is sharing a folder (and allowing incoming CIFS (aka "network file sharing") connections in through its firewall).

Once that's done, you can connect to it either using "gigolo" or mount.cifs.

---

### Post by Overthere on 2010-03-19
Will do!
Thanks, jrssystemsnet!

Brian

---

### Post by norseman-has-a-laptop on 2010-03-19
i think im going to have to try this out it seems like it could be useful at some point when i might need it who knows it great to have more knowlege about this kinda stuff

---


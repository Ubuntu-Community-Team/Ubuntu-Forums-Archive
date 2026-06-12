---
title: "Rhythmbox and DAAP- unable to &quot;see&quot; iTunes libraries over network"
date: 2008-10-21
forum: General Help
---

### Post by the2ndgenesis on 2008-10-21
Hello everyone. I've got a quick question about Rhythmbox as it comes installed in Hardy... I didn't know where else to put this thread, so mods, please feel free to move it as you see fit.

I'm aware that with the upgrade to iTunes 7.x, Apple switched its sharing protocol to DAAP in order to "lock" users into iTunes, and as a result Rhythmbox was rendered unable to connect to iTunes users' libraries over a given network. I also know that a DAAP plugin was later written for Rhythmbox in order to compensate for/work around the transition.

I'm currently using the DAAP plugin, and I'm able to see all iTunes libraries on my home (school) network. The problem is, I'm not able to actually connect to them/"see" the content within each library. Clicking on a library brings up the message "retrieving songs from music share," but no songs are ever actually added to the window/made playable within Rhythmbox.

Is there something I've configured incorrectly that's causing this to happen? I thought that sharing would work out of the box with the DAAP plugin in place. If it matters, my default network is a Microsoft VPN, and I've tried connecting on other school networks with the same results.

Any help would be sincerely appreciated. Thanks a lot everyone.

---

### Post by the2ndgenesis on 2008-10-22
Shameless bump...

---

### Post by the2ndgenesis on 2008-10-25
Final bump before I let this thread sink into the black abyss.

Throw me a bone, guys...

---

### Post by ragtag on 2008-10-26
I would find this handy too, and have had the same problem with it at work. Though we're gradually moving all our machines to Linux there, so that will solve the problem for me. :)

From [this bug report]("https://bugs.launchpad.net/rhythmbox/+bug/62842") I found the following info posted recently by lamah:

> 
It is unlikely that anyone will ever find a way to read Itunes DAAP shares. The reason is that they now use public key encryption to ensure that the client connecting really is another ITunes v.7.0 client. To connect you would basically need to break their encryption which would be pretty difficult, if not impossible.

So we can just blame Apple I guess. :P

According to winehq.org, it's possible to run iTunes 8 in Wine if you must.

---


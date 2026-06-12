---
title: "apt-p2p upgrade to 9.04 is going awful"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by fourthirtysix on 2009-04-23
I'm using apt-p2p for the first time to try and upgrade to 9.04 and it is hanging up quite a bit. 

I've had to quit the update and restart several times when it stopped downloading for several minutes.

I have the port open on the firewall and the console screen says it's reachable, but the performance is miserable.

Is this just not a good way to update or am I doing something wrong?

---

### Post by yeats on 2009-04-23
I'm sure it's just load problems you're seeing.  The main servers are taking a huge hit right now, and I imagine that p2p is no different.  In other words - it's almost certainly NOT just you.

---

### Post by fourthirtysix on 2009-04-23
i thought apt-p2p and the bittorrent approach would alleviate that problem of the server backup, but i guess not.

---

### Post by yeats on 2009-04-23
It's a great idea, but it's not an "up-front" option.  The more users that do it though, the better it will get...

---

### Post by run4flat on 2009-04-24
I was in the same boat as you.  I was doing the normal upgrade and thought, "This would be so much better if I could just do it through torrents."  A bit of searching led to apt-p2p, but now that I've set it up it doesn't seem to be doing any good.  I've set up everything correctly and I've already downloaded some stuff p2p (software upgrades that preceded my system upgrade), but the system upgrade is downloading entirely from the main servers.  It seems like the few people who are using apt-p2p are sticking with 8.10, or waiting for somebody else to start the upgrade first.

Arghh!

---

### Post by fourthirtysix on 2009-04-24
Approximately 12 hours after starting the apt-p2p upgrade to 9.04, about 800 of the 1500 packages had been downloaded.  This is pretty poor performance in my opinion.

Ideally, using p2p should provide a substantial time-savings over the normal upgrade from mirrors provided there are enough people using it. As soon as any one peer gets the whole upgrade, the economies of scale should cause the p2p method to have a growing advantage.

Either there are not enough people using it, or the technology is just not delivering on its promise, I don't know which. Ultimately if I haven't finished in another 12 hours, I will probably revert to the old way and there will be one less person using apt-p2p.

It's a shame because I was very hopeful that p2p would alleviate the strain on the mirrors and provide better DL times. Oh well.

---

### Post by Artemis3 on 2009-04-24
Few people use apt-p2p. My first complain is lack of bandwidth control. If the package is not found it falls back to the normal direct method, using the mirror you left in sources.list.

Turns out the most efficient method is to get the ubuntu dvd (or alternate cd) via torrent, and then upgrade from that. Beware you need more than 2g free where /tmp is, it will tell you nothing and fails to do anything if you don't...

---

### Post by mathfeel on 2009-04-24
> **Artemis3 said:**
> Few people use apt-p2p. My first complain is lack of bandwidth control. If the package is not found it falls back to the normal direct method, using the mirror you left in sources.list.

Turns out the most efficient method is to get the ubuntu dvd (or alternate cd) via torrent, and then upgrade from that. Beware you need more than 2g free where /tmp is, it will tell you nothing and fails to do anything if you don't...
Is the 2g requirement still true even for regular, over-the-tubes upgrade?? Through observing my own usual usage, my /tmp never grow much more than 10mb, so I mounted it as 100mb tmpfs...

Back to original topic. Yeah, no improvement over p2p so I fell back to original method. Just by googling "ubuntu p2p upgrade" I can see a lot of posts (on /. and other) pointing back to the same HOWTO about using p2p upgrade. But at this point, it still feels very much like a hack (editing source.list etc). I think that's why most user still won't use it until it is a blessed and easy method.

---

### Post by tchalvakspam on 2009-04-24
I recommend harnessing bittorrent to download the alternate-install iso (took about 5 minutes today, with 130 seeders) and then either upgrade from the iso directly, or burn the iso to a cd and upgrade from that cd.

see: [https://help.ubuntu.com/community/JauntyUpgrades#AlternateUpgrade](https://help.ubuntu.com/community/JauntyUpgrades#AlternateUpgrade)
for a command line way to do it, though torrent>burn>reinsert cd and wait for popup notification should pretty much do it as well.


I guess the moral of the story is that apt-p2p is still beta for a reason.

Edit: Besides, then you can sidestep any breakage by booting the liveCD first anyway, so it's a win-win.

---

### Post by Wandering Wombat on 2009-04-24
Yep I used Bittorrent to download the alternate iso, no problems, maxed my connection :P

---


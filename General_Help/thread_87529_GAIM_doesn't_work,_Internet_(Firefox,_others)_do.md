---
title: "GAIM doesn't work, Internet (Firefox, others) do?"
date: 2005-11-08
forum: General Help
---

### Post by jeffdano on 2005-11-08
I'm experiencing a weirdness with GAIM where it will hang while other internet programs such as Firefox, Evolution, etc can access the internet. I did not change any settings on the system and my router firewall settings are the same. I haven't changed any port blocks or anything. I have a few accounts on GAIM and none of them want to connect (MSN, Yahoo!, AIM). Even tried uninstall and reinstall of GAIM, nothing is working. Any ideas ladies and gents?:???:

---

### Post by Elitist_Phoenix on 2005-11-08
Maybe try deleting your .gaim directory from your /home/(user) dir and starting from scratch, maybe one of the settings is stuffing it up

---

### Post by jeffdano on 2005-11-10
Tried the recommended course of action... didn't work. I ended up removing Ubuntu from my wife's laptop and installed a different distro just to prove my thoughts... GAIM worked 100% of the time on her new install and still did not work on mine. So it's definitely not a router issue or a system issue (as her's was not working at all up to that point). GAIM is just pooched in Ubuntu, no two ways to slice it at this point. Even aMSN won't work.

---

### Post by pickarooney on 2005-11-10
What way are you installing GAIM for Ubuntu?
It works like a dream for me.

---

### Post by jeffdano on 2005-11-11
Ok, after much gnashing of teeth I found the problem... two words...

Port Forwarding... MSN uses port 1863, which my router was not moving along properly, thus the issues. Thought I'd post this for future reference for other newbies such as myself.

---

### Post by joris.brus on 2005-11-12
I wish routers didn't automatically block every port. 
Why does every piece of software/hardware come witht a built in firewall these days?

I'm very angry

---

### Post by jeffdano on 2005-11-14
[QUOTE=joris.brus]I wish routers didn't automatically block every port. 
Why does every piece of software/hardware come witht a built in firewall these days?

I'm very angry[/QUOTE]

The painful irony on my router is that my changes don't stick. I end up having to redo every couple of days or so.

---


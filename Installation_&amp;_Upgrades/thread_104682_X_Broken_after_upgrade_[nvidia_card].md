---
title: "X Broken after upgrade [nvidia card]"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by keyshawn on 2005-12-16
hi, 

I upgraded from hoary to breezy. After the upgrade, X wouldn't start. BTW, I have a nvidia, MX 400. Anyways, I tried to follow the directions at the HOWTO install Nvidia drivers thread - [http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

Before I download the actual drivers, it said to install my kernel [2.6.12-9]'s  headers and restricted modules. 
So, I tried. And received an error message that says "unmet dependencies."



Sorry I sound bitter, but I had high expectations for breezy, and thus far, it's failed on two occasions [I had probs with pre-install as well]

regards,
keyshawn

---

### Post by thezerogroup on 2005-12-16
I had the same problem with X after the upgrade, I found it so much easier to do a fresh install from CD

---

### Post by jannol on 2005-12-16
try sudo apt-get install nvidia-glx-legacy

remove any nvida-glx drivers before, if you installed nvidia drivers by nvidia script please use the NVIDIA....sh --uninstall before you install these via apt.

I doubt it since it requires a bunch of files.

best of luck

---

### Post by keyshawn on 2005-12-16
[quote=jannol]try sudo apt-get install nvidia-glx-legacy

remove any nvida-glx drivers before, if you installed nvidia drivers by nvidia script please use the NVIDIA....sh --uninstall before you install these via apt.

I doubt it since it requires a bunch of files.

best of luck[/quote]

Yeah, I tried your legacy command and got a bunch of unmet dependencies. 
I don't know if I should force it or not....

If I do a fresh install, I'll lose my /home files right ? It's been 3 months since I've touched a linux box and I forget [and concerning of losing stuff on /home].

regards,
will.

---

### Post by jannol on 2005-12-16
About the dependecies, you should find out what you need, usually it helps a lot adding a few ubuntu universe/multiverse repos, there are quite many but generally those that contains ubuntu are ok. Also, it is never a good idea to add a lot repos from wherever, its best to keep them as near as ubuntu as possible.

About your /home, there are a lot of threads about backup and stuff but to be sure, simply burn a cd or dvd with your /home and then you can simply copy its files back into your new /home

I don't actually remember but I think theres options for that when installing, like mounting /home but not choosing format it and etc.I kinda got lazy a long time ago when saving all important stuff on my debian server which I DO backup once and a while. Debian is 190 days uptime, Ubuntu was a clean install last time when I didn't take notice of install options and my memory is like those 80's amigas...

---

### Post by keyshawn on 2005-12-16
Well, my repositories are set, I'm sure of that one...
[no backports, all ubuntu.com's, and marked breezy] 

I know I could just merely backup what I have, but I don't have a DVD drive installed on this yet, [yes, I Know they're cheap, but I just bought myself a nice $50 linksys router, and dont want to shell out any more cash on the compy]
and I have a bit on the drive. 
Ha, I just expected this upgrade to be very smooth [warty to hoary actually was !]. 

I'm still on the lookout to see how I can remedy this..

Regards,
will.

---

### Post by keyshawn on 2005-12-16
I might regret this, but I just issued:
```
apt-get -f upgrade
```

we'll see how this goes.

---


---
title: "Cannot get Flash player...."
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by mlinauer on 2009-08-27
I have used ubuntu for a few months now and I really really love it.  I recently reinstalled vista, I kind need it for my web pages, and after reinstalling wubi/ubuntu, I cannot figure out how to install flash.  Help me please.  I am disabled and need to play my stupid little Facebook games.....my fish are dying  ;)

---

### Post by zvacet on 2009-08-27
In terminal type 

```
gksudo gedit /etc/apt/sources.list
```

add this line 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

save and close.

```
sudo apt-get update
```

In synaptic find adobe-flashplugin and install it.

---

### Post by BackwardsDown on 2009-08-27
If you install ubuntu-restricted-extras with synaptic, you'll get flash but also a lot of other proprietary stuff like codecs and java. Saves a lot of trouble for many new Ubuntu users.

---

### Post by mlinauer on 2009-08-31
Thank you so much.  I know it has been a while since you posted this but thank you......of course it worked.



> **zvacet said:**
> In terminal type 

```
gksudo gedit /etc/apt/sources.list
```

add this line 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

save and close.

```
sudo apt-get update
```

In synaptic find adobe-flashplugin and install it.

---


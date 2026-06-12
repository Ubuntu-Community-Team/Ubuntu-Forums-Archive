---
title: "How to install musescore 0.9.5 in hardy??"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by zanox on 2009-10-05
Hi to all!! I'm using Ubuntu Hardy, and I'd like install Musescore 0.9.5 that's the new version not in repositories, anyone can help me?

[Link to download page]("http://www.musescore.org/en/download")

---

### Post by JoeBlow9878 on 2009-11-19
Hi zanox!

I don't know whether you found the solution to your problem or not, but here it is just in case you are still wondering.

Open Synaptic Package Manager and click Settings -> Repositories.  Now choose the "Other Software" Tab.  Click Add... Then copy and paste this APT line into the textbox : 

deb http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu hardy main
Then click Add Source.  Click close, and the Reload.
Search for musescore and Mark it for Upgrade.
Apply the changes, and there you go!

Hope that helps!

Joe

---

### Post by zanox on 2009-11-20
Thank you for your help! I don't remember how, but I did it! Do you know how to get pychess working on hardy? see this thread:

[http://ubuntuforums.org/showthread.php?t=1326298](http://ubuntuforums.org/showthread.php?t=1326298)

---

### Post by JoeBlow9878 on 2009-11-20
Hello again!

Unfortunately I have never installed pychess.  I just looked in the synaptic package manager, and it is in there in Ubuntu 9.10 and it is version 0.10 beta1-1.  The version on their site is beta2-1, I think.

Personally, I would consider filing a bug at the following address: [http://code.google.com/p/pychess/issues/list](http://code.google.com/p/pychess/issues/list) .  This software is still in beta so it could well be not functioning correctly yet on all ubuntu versions.  Give them as much information as you can (without being excessive).

I'm sorry I can't help you  with it.  Is there possibly another programme that will do a similar thing until they get it fixed?  Search Synaptic Package Manager for "Chess", and you'll find a lot of different options.  I don't know whether their good enough or not.  

Joe

---

### Post by zanox on 2009-11-20
I had no google account until the last tuesday.. but I have it now so I'll submit the issue.. thanks a lot!! bye!

---

### Post by JoeBlow9878 on 2009-11-20
You are very welcome!  Sorry I wasn't able to solve the issue, though.

Joe

---


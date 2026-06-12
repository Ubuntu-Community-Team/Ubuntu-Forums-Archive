---
title: "Installation hangs on second part during packages"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by yapsuper on 2005-12-11
Hi, I have an old compaq presario with 8 gb and 96 mb ram. After reading some forums it seems this fits the minimum requirements.

First I'd like to say thank you to any one who replies. Here goes, During the second part of the installation, when its installing server-x, it just hangs. I have no choice but the power down the computer after an hour. Can someone help me pls. If you need more info on my computer just ask. 

O yes, after reading a couple of threads that have problems like mine, I found that most experts want answers to these questions so here they are. I used a live cd and it worked just fine (except slowly but I think thats b/c it's running of a cd). I installed the install discs from Ubuntu's offical site. It is breezy badger. During my live cd session I even set up wireless which I was surprised that I didn't need a driver for my linksys pci adapter. 

Anyway... Please help me. Thank you.  Btw I've also posted the same thread in the beginner's forum. I hope posting the same thread twice is ok.

---

### Post by taurus on 2005-12-11
Did you create any swap space on your harddrive at all?  Although I haven't tried this but I think it's because of low RAM on your machine?  What if you pick "server" at the prompt instead of hitting the enter key and then try to install X later.  If you can install the server mode but chokes again when you try to install X, then it is for sure it's the RAM then...  Just something for you to consider or play with!

---

### Post by yapsuper on 2005-12-11
That's an interesting point, althought live cd worked for me and I even got red hat working on the comp. Perhaps your right though. How do I install X after installing the server? If I install the server and then X, it still won't be able to used as a personal computer because of the lack of applications. 

Not to sound rude, but is there another probability other than RAM?

---

### Post by taurus on 2005-12-12
I believe the command to install a desktop is 

sudo apt-get install ubuntu-desktop

And what do you mean by won't be able to use as a personal computer because of lack of applications?  Whatever you want to use, install it with apt-get or synaptic!  Even if you use desktop to install on your machine, you will find out real soon that you still need to install additional apps to get it up the way you want so apt-get or synaptic is your friend.

---


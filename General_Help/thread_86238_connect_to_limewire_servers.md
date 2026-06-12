---
title: "connect to limewire servers"
date: 2005-11-04
forum: General Help
---

### Post by eyebrowman92 on 2005-11-04
for some reason my limewire wasnt downloading any songs. i couldnt figure out. the songs woulkd just stay in queue. i finally got aMule, php client, which had an error box stating" You're not connected to a server!" im guessing this is also the situation with limwire. does anyone know what to do?

---

### Post by SickTwist on 2005-11-04
Are you behind a firewall? If so, the ports these programs use are probably blocked.

---

### Post by eyebrowman92 on 2005-11-04
yes thank you i had firestarter installed and i have removed it. when i removed it from synaptic afterwards i got the following error message"W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)" 


can you tell me what this means? and the limewire files still arent downloading. why not?


ive decided to reinstall firestarter and id just like to know what the error message is and what ports i have to open to let limewire download songs. thanks.

---

### Post by Cidere on 2005-11-04
That probably means that you don't have an internet connection. If you can go on the internet, then I reall don't know.

---

### Post by eyebrowman92 on 2005-11-04
i have an active internet connection. does anyone else know what it means?

---

### Post by endersshadow on 2005-11-04
Better question...why are you trying install from the Hoary repositories?

---

### Post by eyebrowman92 on 2005-11-04
i dont know...how do i install from the breezy repositories? i thought i upgraded.  how do i go about upgradeding them then?

---

### Post by eyebrowman92 on 2005-11-04
anyone?

---

### Post by Qrk on 2005-11-04
type:

sudo gedit /etc/apt/sources.list

change every word hoary to breezy

then type
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by endersshadow on 2005-11-04
Do the following in the Terminal:

```
cd /etc/apt
sudo cp sources.list sources.list.bak
sudo gedit sources.list
```

Then, a text file will pop up (magic), and just copy the following over what you have in it now:

```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```

Save it, and close it, then run this in the terminal again:

```
sudo apt-get update
sudo apt-get upgrade
```

And you're all set!

---

### Post by eyebrowman92 on 2005-11-04
ok now that thats solved what do i do about limeiwre? i removed firestarter and files stil wont download. any ideas?

---

### Post by eyebrowman92 on 2005-11-04
anyone...

---

### Post by SickTwist on 2005-11-04
Are you behind a router that has a firewall installed?

---

### Post by eyebrowman92 on 2005-11-04
i have a linksys router and it cant be behind a firewall because a few days ago limewire was working fine.

---

### Post by SickTwist on 2005-11-07
The linksys router might have a built-in firewall. Read the documentation for your particular router and it will tell you how to configure it. You will need to edit the port forward section to forward the ports that limewire uses from your router to your Linux box. It is easier to do this if the Linux box has a static IP.

---

### Post by eyebrowman92 on 2005-11-10
i found the problem. it was the firestarter program i was using. i couldt forward the ports because something i was doing wasnt right. i just got rid of it and it was solved. thanks.

---

### Post by bmxdude802 on 2006-01-08
[color=blue][size=2]Hey I am having some trouble with my limewire here. I have limewire ten the new version i am guessing. I had nortan antivirus 2003. And every since my pc got the new free symantec avtivirus coperated edition, my limewire would't work because of firewall. The thing is i dont now how to turn off firewall from symantec the free edition as people say. Can someone tell me a better free anti virus that will let me turn it off. Or can someone show me how to correctly connect to lime wire. (The bars won't fill up when i am trying to connect).[/color][/size]

---

### Post by bmxdude802 on 2006-01-08
[color=blue][size=2]Hey I think i found out the problem but still not sure. I don't think that free symantec has built in firewall, so what i did was i went to my connections and editited the firewalls from there. Then if anybody has this antivirus(symantec coperated edition) you might know that if you cilck the little logo on the bottom you get to make it disable any blocking so i did that also now pop ups come up though. If anybody noes if i am doing the right thing can you please tell me . Peace.

---

### Post by bmxdude802 on 2006-01-08
[color=blue][size=2]Hey I think i found out the problem but still not sure. I don't think that free symantec has built in firewall, so what i did was i went to my connections and editited the firewalls from there. Then if anybody has this antivirus(symantec coperated edition) you might know that if you cilck the little logo on the bottom you get to make it disable any blocking so i did that also now pop ups come up though. If anybody noes if i am doing the right thing can you please tell me . Peace. [/color][/size]

---


---
title: "My flash player won't work in youtube."
date: 2008-09-25
forum: General Help
---

### Post by gnarkilljboy on 2008-09-25
I installed a flash player (not sure which one). Most flash stuff will play, except for youtube videos. How do I fix this problem? 

*Yes, I am a noob to Ubuntu.

---

### Post by Forbees on 2008-09-25
it is my understanding that there are a few different flash players

when you first try to view a flash, b4 any player are installed, doesn't firefox give you like 3 players to chose from?

goto add/remove apps and type "firefox flash" in the search bar

it'll give you a few, i use macromedia (spell check) and everything seems to be fine

---

### Post by TeXtonyx on 2008-09-25
I just solved this problem about 10 minutes ago when I had no YouTube.
[http://packages.ubuntu.com/hardy/ubuntu-restricted-extras](http://packages.ubuntu.com/hardy/ubuntu-restricted-extras)
I installed all of them to be on the safe side. 
Also I added medibuntu
[https://help.ubuntu.com/community/Medibuntu#With%20the%20entire%20Medibuntu%20repository](https://help.ubuntu.com/community/Medibuntu#With%20the%20entire%20Medibuntu%20repository)

If you have Ubuntu 8.04 "Hardy Heron":

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Actually I did Medibuntu first and then ubuntu-restricted-extras
It was probably overkill, but YouTube worked after this.

---

### Post by tuxxy on 2008-09-25
The **ubuntu-restricted-extras** package does include Flash, to install flash on its own you would want the **flashplugin-nonfree** package

---

### Post by Twitch6000 on 2008-09-26
The simpliest way to get flash to work is by doing this -
doing to terminal and typing
sudo apt-get flashplugin-nonfree

Or going to add/remove and getting flash from there either way will work.

---

### Post by gnarkilljboy on 2008-09-26
Thanks everyone. What I did was re-install everything in the package manager, and it seems to be working fine now.

---


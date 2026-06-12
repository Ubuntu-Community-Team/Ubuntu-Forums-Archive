---
title: "OpenSSH Server Unable to Load keys (Intrepid)"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by omniuni on 2008-12-22
System: Ubuntu Intrepid Ibex

I've been attempting to install OpenSSH. Apparently, I have the wrong version of ssh-keygen installed. I don't know how this is possible. There is not a ssh-keygen package in the repository.

I first found this post: [http://ubuntuforums.org/showthread.php?t=64597&page=2](http://ubuntuforums.org/showthread.php?t=64597&page=2) which displays my exact error.

Then, I found this one in Google's cache: [http://74.125.95.132/search?q=cache:nE6iL0RFWsQJ:www.ubuntu-forums.com/showthread.php%3Ft%3D403082+ubuntu+ssh+%22illegal+option+--+f%22&hl=en&ct=clnk&cd=4&gl=us&client=firefox-a](http://74.125.95.132/search?q=cache:nE6iL0RFWsQJ:www.ubuntu-forums.com/showthread.php%3Ft%3D403082+ubuntu+ssh+%22illegal+option+--+f%22&hl=en&ct=clnk&cd=4&gl=us&client=firefox-a)

So... I really would like my SSH to work again. Any ideas anyone?

---

### Post by omniuni on 2008-12-22
Never mind. Sometimes the "Stupid" solution works. I ran the following command:

sudo rm /usr/local/bin/ssh-keygen
sudo apt-get --purge remove ssh openssh-server
sudo apt-get install ssh openssh-server

I'm back up and running. I hope that this helps anyone else who finds this odd problem.

---


---
title: "Use as server and desktop"
date: 2008-07-18
forum: General Help
---

### Post by mrappe on 2008-07-18
My machine is currently partitioned with dual Win Xp and Fedora (I use Grub bootloader to select which I want to use). One of the things that I like about Fedora is that it comes with all of the server and desktop programs. I want to be able to install both since I use one machine as a test server and development desktop. How would I do do that with Ubuntu if I replaced the Fedora since Ubuntu has seperate unstalls for server and desktop.

---

### Post by daleus on 2008-07-18
The Server version basically just doesn't install desktop packages, so you can either Install the Desktop version (normal ubuntu) and install the server packages you want (example, apache). 

...or install the server version and install ubuntu-desktop (harder way).

You may want to use the LTS release (8.04.1) in order to make sure your server has updates for time to come!

---

### Post by bodhi.zazen on 2008-07-18
You install Ubuntu and then add the server packages you need post install.

You could go the other way and install the server and then add a desktop. You can

sudo apt-get install ubuntu-desktop

to install the whole tamale, or just add a light weight window manager.

The server install is command line only and comes with a different "server" kernel that is optimized for server tasks. Of course you can compile your own kernel too.

---


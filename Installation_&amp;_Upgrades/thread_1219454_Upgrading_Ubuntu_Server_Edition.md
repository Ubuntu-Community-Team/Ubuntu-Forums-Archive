---
title: "Upgrading Ubuntu Server Edition"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by gjvblack on 2009-07-21
Hello!

Please excuse a noob, but how do you upgrade 8.10 to 9.4 (server edition)? I have the ISO file and burned it, now i have a bunch of files on my serve but i dont want to risk deleting them, how can i upgrade without it removing any of my web files?

thanks!

---

### Post by ibutho on 2009-07-21
Hi and welcome to the forum.

Over the years, I have just used "apt-get dist-upgrade" to upgrade my server from one Ubuntu version to another.

---

### Post by gjvblack on 2009-07-21
So once i input that in the terminal it will upgrade autmatically? Will i have to put the cd in the drive or will it download it instead?

---

### Post by wojox on 2009-07-21
Install update-manager-core if it is not already installed:

sudo apt-get install update-manager-core


Launch the upgrade tool:

sudo do-release-upgrade

Follow the on-screen instructions.

---

### Post by gjvblack on 2009-07-21
that seems to be working, thanks a lot man!

---


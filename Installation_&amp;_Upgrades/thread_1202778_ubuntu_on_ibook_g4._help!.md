---
title: "ubuntu on ibook g4. help!"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by k0mpresd on 2009-07-02
i want to at least boot a live on my ibook g4. maybe even partition the hdd and dual boot. i found this page [http://geeks.pirillo.com/profiles/blog/show?id=2300301%3ABlogPost%3A684123&page=1#comment-2300301_Comment_1688038](http://geeks.pirillo.com/profiles/blog/show?id=2300301%3ABlogPost%3A684123&page=1#comment-2300301_Comment_1688038), which made it seem fairly easy.

i downloaded ubuntu-8.04.1-desktop-powerpc.iso and burned it to cdrw.

the mac will boot from cd. i enter the live-nosplash-powerpc modprobe ide-core video=radeonfb:1024x768-24@60 command and it says loading kernel.

this is where the problems begin.

i get a LOT of errors dealing with hdc (??). and then finally i get a busybox shell.

i found this page: [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues), which says to enter modprobe ide-core at the busybox, if thats as far as it loads. but then i get an error complaining of no ide module found.

can anyone help? thanks. :)

---


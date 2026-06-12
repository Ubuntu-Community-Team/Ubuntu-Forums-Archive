---
title: "[SOLVED] How do I restore 2 services in the Boot Up Manager???"
date: 2008-11-01
forum: General Help
---

### Post by eotakos on 2008-11-01
I've installed keytouch with the source code from the keytouch webpage, because the version in the repositories had some serious bugs... 

I wanted to try something and I disabled the two services in the Boot Up Manager that initiated the keytouch, and instead of them being just unticked, they were disappeared. How do i bring them back? if it helps, i've checked the /etc/rc?.d folders, and i found both the scripts in all of them. I don't know how to get them started though.

thanks for your time

---

### Post by eotakos on 2008-12-17
replying the question i posed some months ago for others scanning this thread to see...

The boot up procedure goes like this: first it executes all links in the rcS.d directory that start with an "S". Then (if you haven't changed the default runlevel) it executes all links in the rc2.d directory starting with an "S".

if a link in these directories starts with a K, it won't be executed. So, if you make a change in the bum manager in order not to execute a script at startup, what it does is that it renames the file (link) in order to start with a K. if you want to bring back the script but it doesn't appear in the bum, all you have to do is to rename it in order to start with an S.

here is a nice link with info about the startup procedure and the boot up manager. 
[http://www.marzocca.net/linux/bumdocs.html#order](http://www.marzocca.net/linux/bumdocs.html#order)

---


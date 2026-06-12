---
title: "nTorrent over ssh"
date: 2008-08-06
forum: General Help
---

### Post by ktamm on 2008-08-06
I am wondering if anyone has been able to get nTorrent to work over ssh? I am able to connect to rtorrent when it is running locally on my machine, however when i try to connect to it via ssh and run nTorrent that way, nothing happens. A error box will show up, however there are no messages in it to help lead me to the next step.

I have tried using the ssh connection box in ntorrent itself and also have tried created a tunnel manually (ssh -L 5000:ipaddy:5000 user@ipaddy) then trying to connect ntorrent locally over the tunnel, however both result in the same empty error box.



Please help !!

---

### Post by ktamm on 2008-08-07
Bump.

---

### Post by tgrimley on 2008-10-27
Sorry, I came here with the same problem! :( The FAQ suggests that versions are probably wrong and to check the logs.. but there's no entry when it tries to connect and the blank message shows up!

Sub'd to this thread.

---

### Post by netbrain on 2009-01-24
this issue is very common, and usually has to do with the wrong xmlrpc-c version installed. Im guessing you have installed the packages in the ubuntu repository.

However you will most likely have to build rtorrent, libtorrent and xmlrpc-c from source in order to get the correct build.

Anyhoo this issue is described in better detail here:
[http://code.google.com/p/ntorrent/wiki/FAQ](http://code.google.com/p/ntorrent/wiki/FAQ)

also check out the quickstart guide, issues tab and public discussion group for more info on the subject.

---


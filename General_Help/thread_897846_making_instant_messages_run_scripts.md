---
title: "making instant messages run scripts"
date: 2008-08-22
forum: General Help
---

### Post by shortridge11 on 2008-08-22
i'm running 8.04 on my home file server, and i was wondering if it was possible to make it so that if i sent an instant message to an account that my server was signed onto, then it could run a script? or if something happened like someone tried logging onto my server then it could send me a message via aim, or if my motion sensor webcam was tripped it could send me a message.....etc?

any ideas would be great.

---

### Post by LateNiteTV on 2008-08-22
you can setup syslog to send you emails... but i dont know about the aim thing. ive never tried that one... but that would be pretty cool. i might to some experimenting. :D

---

### Post by Alaric on 2008-08-22
Check out naim instant messenger.  Download it with

sudo apt-get install naim

then run man naim for some more information.  From what I saw, it will run scripts from a file /home/(user)/.naimrc on startup if that file exists.  Good luck :)

---

### Post by shortridge11 on 2008-08-22
i'll try it out and let you know what happens =D

---

### Post by shortridge11 on 2008-08-25
alright- i got it running.  I used perl to make one, and it was really easy.  i just used the Net::OSCAR module and it pretty much ran itself.  Now my aim bot returns system information, can reboot my computer, start torrents, etc.  But for obvious security issues it only does to for my screenname. If anyone else tries talking to my bot it just says go away.  PM me if anyone else wants to expand on this!

---


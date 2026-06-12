---
title: "SSH Port Forwarding, help please :D"
date: 2005-11-22
forum: General Help
---

### Post by basse1989 on 2005-11-22
Hello everyone!

I need help with ssh port forwarding.
What I want to do is use Google Talk (based on jabber if you don't know), IRC and stuff like that behind the firewall at school on my laptop computer.
I'd also like to get World of Warcraft playable inside the same firewall (don't worry, I don't play during lessons :D )
I can use ssh to connect to my server at home so port 22 is open...

Can anyone help me with this please? :D

---

### Post by magicfab on 2005-11-22
Check this thread:
[http://www.ubuntuforums.org/showthread.php?t=91840&page=2](http://www.ubuntuforums.org/showthread.php?t=91840&page=2)

I would encourage you to write a brief how-to here if you get it working.

---

### Post by rcerreto on 2005-11-22
I was told about  a command like:

ssh -L xxxx:localhost:yyyy remotehost

where xxxx is the local port you're tunnelling into ssh, yyyy is the remote server port you're connecting to and remotehost is, well, the remote host :-)

I never tried myself though.
So I can't say whether it will work.
Worth a try anyway

---

### Post by albinoloverats on 2005-11-25
I have a desire to achieve very much the same thing - it would be nice to bypass my university firewall for online gaming, bit torrent, etc.

So far I have only been able to successfully tunnel Thunderbird (and Firefox) through one of the university's lesser known proxy servers using a simple shell script:

```
#!/bin/bash

mozilla-thunderbird &

ssh -X -D 8080 -q -p 22 *username*@*outgoing server*
```

which kinda works like so: **-D 8080** is the port on your local machine where you tell your computer to connect to (as a socks proxy); **-p 22** is the port the ssh server listens on the remote machine; finally ***username*@*outgoing server*** is my username on the server I'm connecting to.  Not that they're important here but **-X** and **-q** allow the use of remote applications which require an X-Window environment, and suppress errors and warnings (ie quiet).

I hope what I've said may be of some use, and if anyone else knows of a way I might be able to get Azureus working (as CD images take **along** time through HTTP or FTP) I would be grateful.

---


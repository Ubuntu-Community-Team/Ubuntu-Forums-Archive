---
title: "[SOLVED] Broadcast message to logged in users"
date: 2008-09-24
forum: General Help
---

### Post by Asham on 2008-09-24
Ello,

I login to a remote server and sometimes I need to reboot the server. Up to this point I've just entered the reboot command but now I am not the alone user on the server, so I got an angry phone call today from someone who apparently was doing something important when the server suddenly shutdown. Oopsie daisy!
:lolflag:


**My question is this: **

can I broadcast a message to the currently logged in users? 
```
"The server will be down for 15 minutes tomorrow at 2:00 PM due to maintenance. For more information, contact Adam at email@host, or phone: 555-000."
```

/Adam

---

### Post by 4partee on 2008-09-24
from man shutdown:

shutdown [OPTION]... TIME [MESSAGE]

---

### Post by Asham on 2008-09-24
Didn't think it would be the same command. Great, thank you.

If I would not want to reboot but still broadcast, I'd use wall (I just googled it) :)

---

### Post by scorp123 on 2008-09-24
You could also use the "wall" (= write to all) program before actually initiating the reboot, so people get an appropriate warning in advance.

Another thing you could do is to modify files such as e.g. /etc/motd  (motd = Message of the day). That's the file that gets per default displayed when users login via SSH. Normally it contains stuff such as "Ubuntu comes with no warranty ...." and so on, but you can of course also replace the content with your own messages so people get to see the message when they login. e.g. something like:

```
> ssh user@remote-system
Password: 

Linux some-hostname-here 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686

ATTENTION:

Due to some issues with our storage we will have to reboot this machine tonight!
Please make sure you safe your work by 21:00 tonight and logout! 
We will issue another warning message before the actual reboot.

Thank you for your understanding and cooperation,
your beloved super-user and God-like system administrator,

~ root # ~


PS: Yes, I promise to make backups before I mess with your files ;-)


remote-system:~ >
```

OK, above example is not 100% serious ;-)  ... But you see what I mean. You can edit the stuff in /etc/motd and the next time someone logs in they will get this message inside their terminal, so they're warned many hours in advance and can move their files away if they have to.

---

### Post by Asham on 2008-09-26
Thanks!

I can see how a custom MOTD could be useful. 
Some applications such as ls and htop use colors for some of the information. Naturally, of course, I have to ask if I can use colors in my MOTD or is it different when it comes to MOTDm which I presume is plain text?

---


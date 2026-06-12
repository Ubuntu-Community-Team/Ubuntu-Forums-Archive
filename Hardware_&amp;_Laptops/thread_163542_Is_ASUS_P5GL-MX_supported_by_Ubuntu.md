---
title: "Is ASUS P5GL-MX supported by Ubuntu?"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by mmarkvillanueva on 2006-04-21
I've installed Ubuntu 5.10 and Ubuntu Dapper Flight 5 in my PC but the sound doesn't
work at all. Aside from that, whenever I shutdown, the GNOME just disappears leaving a black screen with a blinking cursor at the upper left corner.

How do I fix this? :(

---

### Post by dermotti on 2006-04-21
hmmm, run **alsamixer** and make sure yoru sound card isnt muted....worth a shot

---

### Post by gere on 2006-04-21
I have the same problem with an Asus-board. Alsamixer isn't muted in my case. Any further ideas?

---

### Post by mmarkvillanueva on 2006-04-23
[QUOTE=gere]I have the same problem with an Asus-board. Alsamixer isn't muted in my case. Any further ideas?[/QUOTE]

yep. i've also tried running alsamixer. btw, are you experiencing shutdown problems with your board? in my case the screen turns black with a cursor blinking at the upper-left corner of the screen (as if X was shutdown and leaving a console) and it stucked there. i tried using halt in another terminal to shutdown, but the shutdown process didn't continue. i'm not sure though if GDM or something else is the problem

](*,)  any idea?

---

### Post by gere on 2006-04-23
I had some problems with the power off after the shutdown. After an Ubuntu update (Dapper beta) the shutdown process works perfectly (I also updated my BIOS with the latest version)

---

### Post by gere on 2006-04-25
Solved (my problem):
I added the user to the group audio and now the sound works perfectly on my system.

```
sudo adduser username audio
```

---

### Post by mmarkvillanueva on 2006-04-25
after using the command 'sudo adduser <username> audio'... it says that my username is already a member of audio

:( any ideas? i haven't tried updating (i have slow internet connection)... maybe i'll try it some other time

---


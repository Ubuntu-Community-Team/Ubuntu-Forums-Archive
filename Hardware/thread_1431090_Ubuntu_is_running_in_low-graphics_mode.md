---
title: "Ubuntu is running in low-graphics mode"
date: 2010-03-16
forum: Hardware
---

### Post by makak06 on 2010-03-16
Hey

I have set up a pc with some features like an FTP or LDAP etc...
Now i would like unplug my monitor because i don't need now.

But when i run my PC without monitor i have this message : 
[*****Ubuntu is running in low graphic mode*]("http://www.google.fr/url?sa=t&source=web&ct=res&cd=1&ved=0CAsQFjAA&url=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fid%3D296994&rct=j&q=ubuntu+is+running+in+low-graphics+mode&ei=imKfS5WAKsH34AaRkbXoDQ&usg=AFQjCNHb4M3NN6P8KoeBNaj2tuzwqNspqw&sig2=pEGqE85LlTu0_VKGHE5X7A")

And me i would like to use remote desktop connexion in order to administrate this PC. (no SSH) and in low graphics mode it's not possible !

How to solve this problem ? 

PS : Sorry for my english because i'm french

Thanks for your help

---

### Post by Fafler on 2010-03-16
What about running a stand alone VNC server instead of doing it on top of X? Install the package vnc4server and run it from /etc/rc.local with a command like su username -c "vnc4server"

---

### Post by makak06 on 2010-03-16
Thanks for the help !

It's the same problem ! My PC doesn't start and i don't have a graphic interface...

May do i have to plug my screen ?

---

### Post by Fafler on 2010-03-19
Well, how far does it get when booting? Are you able to ping it? If so, try disabling gdm and still do the vnc thing.

---

### Post by sam.reader on 2010-03-19
Is your PC latest enough
Put down your gig details here and we can narrow down to the proper reason.
You will need to meet the minimum recommended configuration to run any OS in good condition.
Not everything is XP which runs even on the least configuration.

---


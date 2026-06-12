---
title: "problem with cd-burner... help!"
date: 2005-01-08
forum: Hardware &amp; Laptops
---

### Post by legacy on 2005-01-08
hi guys, i need some help here... look im a newbie with linux...
well i have a atapi cd burner... its a sony one.... always had worked..
well i can recall that my cd burner was working fine when i had fedora core 2... but when i installed fedora core 3 it just didn't work... now i have got some other help... its k3b just to say...
ok first thing first the problem is that k3b just freazes at the slpash screen on "searching for device". now ive had my older bro who is more fluent with linux to look at it... the first think was that there was a problem with the kernal that comes with fedora core 3 that cdbruner options was set only on root permissions... am i coreect or not? ok so dat was updated... so yeah and on another computer we figured dats right...
da other thing is when we list device through cdrecord it does show my cd burner as present... so dats all good... but when i come to load k3b its crashes and from that it holds cdrecord and that cant find device no longer... so i dont know whats happening...
can some1 help?
and yes... still right now im using ubuntu, and i could say its still not working and was no working either when i tried on mandrake 10.1 and agnula...
so can some1 please help me here.  :D

---

### Post by wallijonn on 2005-01-08
I take it that you installed k3b in Ubuntu through SPM.

Open a Root Terminal and issue the command: k3b

Are your recorders seen?

---

### Post by legacy on 2005-01-08
nope.... it loads up... displays all dese stuff bout loading the icons and ect...
den da cursor just flashes while the splash screen has flashed...
and yeah i got k3b through synaptic...

---

### Post by legacy on 2005-01-08
sorri not flashed!!! crashed... im all over da place man

---

### Post by wallijonn on 2005-01-09
first things first, does Nautilus allow a burn? [COLOR=Blue]Go -> CD Creator[/COLOR] or Location: [COLOR=Blue]burn:///[/COLOR]

---


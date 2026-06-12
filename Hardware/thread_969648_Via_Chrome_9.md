---
title: "Via Chrome 9"
date: 2008-11-03
forum: Hardware
---

### Post by peterson_espacoporto on 2008-11-03
Hi there,

I've installed Mandriva 2009 on my father's laptop, as some sort of last attempt on linux. wubi-installed Ubuntu 8.04 worked, but it was hell slow.

Mandriva was working fine. I actually liked a lot Mandriva because of its control panel etc. But I'm REALLY disappointed. Loads of bugs, ridiculous things (no CUPS on standart installation, no gconf so it's impossible to activate totem plugins, etc) - and now internet is not working anymore. Suddenly I can't connect. More, I can't even access Windows Drive's files anymore. That's a disaster.

SO I though I could just apologize to my father and tell him I'd install a real good distribution, Ubuntu - or, perhaps, Kubuntu, since he was getting used to KDE4. But I found out Ubuntu simply can't get the resolution right. I can't explain properly, it's like Ubuntu thinks the screen is 4 times bigger than it really is - I can't see KDE Panel, for example. Well, I actually can't see it in Ubuntu 8.04 KDE4 Remix, because in Kubuntu 8.10 I can't even log in (same for Ubuntu 8.10 and 8.04, can't get in graphical mode through livecd, for use nor for installation only).

I found out Mandriva's using Openchrome and is getting it right. The graphics are nice there, just perfect, and there was no need for setting at all. Isn't Ubuntu using it also? Am I doing something wrong? What should I do? What can I do? =S

---

### Post by cariboo on 2008-11-03
Check the virtual screen size in /etc/X11/xorg.conf.
to do this press Alt-F2 and type:

```
gksu gedit /etc/X11/xorg.conf
```

and look for virtual somewhere in the file, I'm using Intrepid, and the xorg.conf file  is minimal.

Another thing you can try if you are using hardy is to press Alt-F2 and type:

```
sudo displayconfig-gtk
```

Set your resolution this way.

Jim

---

### Post by peterson_espacoporto on 2008-11-11
Unfortunately I can't do it. The computer completely freezes when it attemps to get to X. =/ No way to go to console.

But anyhow, Mandriva worked fine from that day on. Let's see.

On the meantime: why isn't Ubuntu shipped with Openchrome? If it is, why then it doesn't work properly?

---


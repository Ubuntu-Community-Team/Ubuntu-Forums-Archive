---
title: "Setting ktorrent as default..."
date: 2008-07-16
forum: General Help
---

### Post by k0nfa on 2008-07-16
Hey guys, you're probaly used to reading all those newbie posts. Here's just another one. I recently switched to Linux(ex-windows) and I'm stilling adapting =)

So here's the thing, I wan't to change my torrent program from Transmission to ktorrent as default, but the trouble is I can't find where the exact location is, unlike Transmission it can't be found in /usr/bin/... as kotrrent  file or something.

 Could you please help me out?

Tnx and cheers!

---

### Post by jake1017 on 2008-07-16
I use ktorrent and I can find it in /usr/bin it is a file called ktorrent. What version of ktorrent and KDE are you using? Also do you want to make it default in Firefox or something else?

---

### Post by k0nfa on 2008-07-16
Ktorrent is 3.0.1.
KDE 4.0.3

It should run in ubuntu right? But I just can't find a ktorrent in usr/bin :P

PS and yes, I wan't to make it as default in firefox.

---

### Post by jake1017 on 2008-07-16
Your version of ktorrent is using KDE4 which means the ktorrent executable is in /usr/lib/kde4/bin

Hope this helps:):):)

---

### Post by k0nfa on 2008-07-16
It worked, thanks

---

### Post by evets25 on 2008-07-16
In the future, you can locate a program's executable from commandline by using "whereis": 

```
whereis ktorrent
```

you can also use locate to find any files with ktorrent in their path:

```
locate ktorrent
```

Alternatively, you could use synaptic to get more info on the "ktorret" package, and in there you would find a list of files that the package installs. Cheers.

---


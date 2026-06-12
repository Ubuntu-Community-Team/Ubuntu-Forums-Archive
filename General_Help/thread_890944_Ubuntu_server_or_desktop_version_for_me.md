---
title: "Ubuntu server or desktop version for me?"
date: 2008-08-15
forum: General Help
---

### Post by _Horus_ on 2008-08-15
Hi everyone...
Can anyone recommend what exactly the best option is for my situation below (I am totally new to Linux):

I have a spare PC (called 'storage PC' from now on) that I want to hook up to my router (network) and leave on 24/7. I want to use it as a **media server** (so I can watch movies etc on PS3 without needing to turn my main PC on) and also as a kinda **backup/ storage** centre for music/vids/ photos etc that I have on my main PC and laptop (**both XP**)i.e. it would have the sum of info from PC and laptop together. Both the PC and laptop would have to be able to access it.

For staters, should I get **Ubuntu server or desktop version**?

---

### Post by jerome1232 on 2008-08-15
Well the only real difference between the two is the server version comes with a basic cli only install and has a kernel optimized for being a server.
You can install the gui onto the server version (I wouldn't uses to many resources for a server imho) if you wanted

---

### Post by _Horus_ on 2008-08-15
Thanks Jerome. I guess the server version is the one that I'll need. I'm gonna have to post in the server area of the forum coz I have no idea how, with no GUI, I would go about do anything with it. Would setup be done purely via a desktop that connects to the server or would I have to temporarily add a monitor and keyboard to it so that I can set it up the backup function and add Twonkymedia?

---

### Post by Ryadt on 2008-08-15
```
sudo apt-get update && sudo apt-get upgrade
``````
sudo apt-get install ubuntu-desktop
```will give you a GUI.

---

### Post by jerome1232 on 2008-08-15
For initial install of course you would hook up a monitor but during the install you can tell it to install an openssh server, then you can just ssh in from any other computer.

That way it doesnt' have to have a monitor and keyboard hooked up to do it

If you decide to go the gui route you can forward an X session using the -X option
(honestly most of you work is gunna be done vie web interface or command-line anyways but to each his own)

```
ssh -X <user>@<host>
```

---

### Post by _Horus_ on 2008-08-15
Thanks again Jerome.

Unfotunately I think nothing is gonna be easy for me coz I even had to look-up ssh just now:(

I've just downloaded the server version so I will give the install a go first and then see how it goes from there. I guess my next steps will be:
1)try to connect to it from my PC via the ssh protocol (gonna have to ask about that one later:o).
2)test writing to it from the PC (and reading from it)
3)see if I can backup my PC data to the server
4)try and install Twonkymedia on it and see if it can serve the PS3

Arghh, I think this is gonna take a long time.

If you think I'm going about it the wrong way i.e. there is a more efficient way of doing the above then I would welcome any recommendations.

Cheers:)

---

### Post by jerome1232 on 2008-08-15
Don't worry we all have to start learning somewhere, good luck with your project and welcome to the forums

---

### Post by _Horus_ on 2008-08-15
Thanks:)

---


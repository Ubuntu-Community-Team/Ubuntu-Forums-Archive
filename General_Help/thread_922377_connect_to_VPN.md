---
title: "connect to VPN"
date: 2008-09-17
forum: General Help
---

### Post by LoneWolfJack on 2008-09-17
Ok, I knew this was not going to be easy.

I need to connect to an FTP server through a VPN connection.

I clicked the connection applet thingy in my system tray and selected "VPN connections" and created a new VPN connection... first thing that puzzled me was that there's no place to enter username/password... needless to say, the whole thing doesn't work either.

Guess I'm fiddling with the wrong tools or something.

Can someone point me in the right direction please? The threads about VPN I found and the VPN help files are not helpful at all.

---

### Post by LowSky on 2008-09-17
go into sysnaptic package manager and looko for VPN tools, some goood one should pop up

---

### Post by LoneWolfJack on 2008-09-17
that's not exactly helpful because there is no tool that is called "pick this to get what you want". I really don't have the time to work through all the packages listed there just to get VPN working.

there has to be someone around here who can call the program I need by its name.

---

### Post by bodhi.zazen on 2008-09-17
> **LoneWolfJack said:**
> that's not exactly helpful because there is no tool that is called "pick this to get what you want". I really don't have the time to work through all the packages listed there just to get VPN working.

there has to be someone around here who can call the program I need by its name.

Well, can you give us more details ? How is the VPN set up ? Is the server windows or *nix ? What kind of router ? Cisco ?

---

### Post by EmanresuusernamE on 2008-09-17
If you're connecting to a Windows VPN, type in PPTP in the search function of Synaptic. There's one that specifically says:

"pptp-linux     1.7.0-2ubuntu2     Point-to-Point Tunneling Protocol (PPTP) Client"

---

### Post by LoneWolfJack on 2008-09-17
Ok, already have that installed... but I really don't know where to go from there... typed pptp <IP> on the shell and at least I was not getting any errors but it still didn't ask me for a password.

I never used VPN so I'm pretty much clueless on how this should work procedure-wise.

I think they're running *nix on a checkpoint firewall, but that's just guessing.

The VPN setup GUI of the standard ubuntu network manager actually looked kinda right... it was just missing fields for username and pass...

---

### Post by LoneWolfJack on 2008-09-18
anyone?

---


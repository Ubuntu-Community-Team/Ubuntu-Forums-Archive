---
title: "[SOLVED] Remote Desktop Theroy"
date: 2008-07-16
forum: General Help
---

### Post by CrusaderAD on 2008-07-16
I've been looking around for a solution to my remote desktop issue. What I'm trying to do is have multiple users access one server via remote desktop. Is it possible to have more than one person signed on and have control of their own sessions? If not in Ubuntu, how bout Windows?

---

### Post by PRMan on 2008-07-16
Windows Remote Desktop works the way you want by default, but really requires "Terminal Services" to be on if you want more than 2-3 users.  That requires a Windows Server OS.  VNC on Ubuntu does not do this out of the box, although I saw a hack to get each person to log in with VNC to a separate X session.

Search for "VNC X Session" on here.

---

### Post by CrusaderAD on 2008-07-16
I tried terminal services in windows... it's on, but it disconnects the first user when the second logs on.

---

### Post by Taxman415a on 2008-07-16
I'm not sure exactly what you're asking for, but it seems like LTSP [http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project)  does what you want.

It's built into edubuntu, which despite the name isn't just for education. It just makes this type of thing ridiculously easy. See [http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)

---

### Post by jimv on 2008-07-16
> **raptormanad said:**
> I tried terminal services in windows... it's on, but it disconnects the first user when the second logs on.

I think that only works in Windows Server 2003 and 2008.  It's not really Remote Desktop like in XP, it's called Terminal Services.

---

### Post by HermanAB on 2008-07-16
Win XP only allows one RDP connection.
Win2003 allows two (actually 3) RDP connections and more can be added if you license the terminal server function.
Alternatively, you can run VNC for additional users.
(Win2008 and Vista are similar to Win2003 and XP, just slower).

Linux allows as many users as you want through SSH.  VNC is really only meant for use by masochists, since SSH can do everything VNC does, only better.

Cheers,

Herman

---

### Post by jimv on 2008-07-16
> **HermanAB said:**
> Win XP only allows one RDP connection.
Win2003 allows two (actually 3) RDP connections and more can be added if you license the terminal server function.
Alternatively, you can run VNC for additional users.
(Win2008 and Vista are similar to Win2003 and XP, just slower).

Linux allows as many users as you want through SSH.  VNC is really only meant for use by masochists, since SSH can do everything VNC does, only better.

Cheers,

Herman

SSH can't control your mouse.  Which I need for hte box hooked to my TV.

---

### Post by CrusaderAD on 2008-07-16
I have Windows 2003 Server setup, with the license intalled. Still drops the first user when the next one logs on. I have the number of maximum users set to 5, still a no go. Windows is SUCH a pain when it comes to "licensing"... hence my Ubuntu Linux Conversion.

---

### Post by CrusaderAD on 2008-07-18
If anyone finds this post and is curious... you can have RealVNC and Remote desktop access a windows box with separate sessions. That's two! I'm sure it bogs down resources though.

---

### Post by robertsaron on 2008-09-21
Check out nomachine.com for linux. I use it to connect to my linux box at home from work. By default it can host up to two seperate sessions. There are other thing you can do I am sure to add more. 

Though I have not messed with it, to see if there is a way to add more. If you find out how let me know, you can even change the port from 22 to some thing else just like RDP. 

Also it uses SSH encryption, and supposed to pull sound across. As well as printing, I find this program to be a lot faster than RDP and VNC. VNC is good but can be slow on the refresh.

---


---
title: "[SOLVED] Help me set up a headless Hardy Server, please"
date: 2008-08-21
forum: General Help
---

### Post by william_hunter on 2008-08-21
All, I am setting up a webserver/game server that I need, for various reasons right now, to run headlessly in my upstairs store-room. I installed the OS last night, that was fun, installed the LAMP and set that up, no big deal there. Got the game server set up and running nicely. 

This is where I hit the wall. I run an Apple Airport Extreme, and have forwarded ports to the server for vnc and the game server, as well as webmin (which is not yet isntalled, but will be soon) in both the airport settings and in firestarter. I cannot reach the server via VNC to save my life.

Let me start by saying that I had this sort of setup running 2 days ago, when my main hard disk failed. I decided to upgrade and now I cannot recall how exactly it all worked out. I think the problem is with the Ubuntu firewall, because I have set the IP of the server to the exact same as it was before internally, and it was working 3 days ago, with no changes to the Airport firewall. 

I enabled Remote Desktop. I enabled automatic login. I am stuck. Help?

---

### Post by Peter09 on 2008-08-21
Firstly can you reach the server using ssh. You may need to install open-shh on the server first.

The command on the local machine will be

```
ssh -X username@servername xterm
```
This should open an xterm on the server.

I have found that (if you want a remote GUI) then FreeNX is the best solution. Find their website and download the packages. It is a simple and good solution. 

You should get ssh working first.

PC

---

### Post by william_hunter on 2008-08-21
Fixed. I had an invalid internal ip assigned. Simple things....-sigh-

---


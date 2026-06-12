---
title: "How to setup a VNC for helping someone"
date: 2008-09-19
forum: General Help
---

### Post by reflexion on 2008-09-19
Hi,

I am curently configuring my grand-fathers's first computer. Because he is an heavy traveller, I bought him a eee pc. He will be using it only for quick lookups on the net and sending/receiving emails. You see the type..

I decided to install ubuntu eee on his computer.


As he may have a few questions when using is computer, I would like to be able to access is computer whereever he is, so that I can see his desktop and tell him or do what he wants to do.

So what I am asking is: "Is there a way to set up a vnc connection with him, that whereever he is in the world, I can gain access to his computer (with simple security)"

thank you

---

### Post by howefield on 2008-09-19
Are you on Ubuntu as well ?

There is built in Remote Desktop your grandfather could run and Remote Desktop Viewer that you can run to connect.

---

### Post by reflexion on 2008-09-19
I have an unused ubuntu session on my home computer, which I will reactivate if needed.

But I am worried about routers blocking my access to his computer if he his outside my local network...


And also, I have never used the Remote Desktop application, so I do not know how it works.

---

### Post by howefield on 2008-09-19
> **reflexion said:**
> I have an unused ubuntu session on my home computer, which I will reactivate if needed.

Are you crazy  :lolflag:

> But I am worried about routers blocking my access to his computer if he his outside my local network...


And also, I have never used the Remote Desktop application, so I do not know how it works.

You can run a vnc viewer on your box just the same, but configuring routers might need to be done depending on where your grandfather is connecting from.

If it were a windows box, I'd recommend Teamviewer which blasts its way through routers, no probs, but I am not sure if it works on linux, or at least I know it works with Wine, but don't think it will connect to a linux box but I may well be wrong.

---

### Post by HermanAB on 2008-09-19
You need reverse VNC:
[http://www.uvnc.com/addons/singleclick.html](http://www.uvnc.com/addons/singleclick.html)
[http://www.vncscan.com/vs/oneclickVNC.htm](http://www.vncscan.com/vs/oneclickVNC.htm)

Cheers,

Herman

---

### Post by mbeach on 2008-09-19
you could also look into:
[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

You'd likely have to be running your VNC server in a listening mode, and have your router port (typically 5500) pointed to your machine, but it would give your grandfather the ability to click on something that says something like "GS Help" [grandson help].  As long as you are running a listening daemon, his screen would show up on your pc.  I've been using this in the Windows world for awhile using RealVNC.  I haven't set it up yet in the Ubuntu desktop.

---

### Post by reflexion on 2008-09-19
So if I understand right, I need to set-up MY router (at my home) so that when my grand father hits "GS HELP", it sends a command to ME and gets redirected to my computer?


And I would also be able to control his laptop??

thanks agains for the help

---

### Post by mbeach on 2008-09-19
correct.

---


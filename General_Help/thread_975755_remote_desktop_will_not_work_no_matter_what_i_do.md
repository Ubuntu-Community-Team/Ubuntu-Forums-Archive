---
title: "remote desktop will not work no matter what i do"
date: 2008-11-08
forum: General Help
---

### Post by tjwoosta on 2008-11-08
i have an old machine that is still running ubuntu 7.10  

im afraid if i try to upgrade to 8.04 it wont work anymore because the computer has only 256mb ram

and besides it runs perfectly with 7.10



anyway, i have tried many many times now to get this remote desktop setup and still it wont work

first i went to system-preferences-remote desktop and setup the remote desktop

i also gave it a password

then i tried connecting to it from a laptop that is running Ubuntu 8.10 
(applications-internet-remote deskto viewer)

that didnt work, no servers were listed, so i tried manually entering the server computers ip, that didnt work, so i tried just using laurie-desktop:0, that also didnt work

so, after this frustration, i installed tightvncserver on the old machine and followed this

> 
 Re: how to set up a vnc server?
Here is how I did it:
* Install tightvnc(with synaptic).
* Edit/check vnc.conf (I didn't change anything there)
* Run vncpasswd and type a password
* Run 'vncserver :1' (When you want to stop it run 'vncserver -kill :1')


then i installed xtightvncviewer on the new machine

i typed xtightvncviewer and a box came up that said "server"

so i typed the ip of the old computer but nothing happened



what the hell am i doing wrong?

why wont this remote desktop connect?


btw, both computers are connected to the same router via ethernet cables

also i have sucessfully used remote desktop on this same network before, but with different computers (also running ubuntu) and it worked no problem

and just incase my router was blocking ports, i have forwarded the vnc ports to the laptop   

do i also need to forward the same ports to the server machine?

is it even possible to forward the same ports to two different machines at the same time?

---


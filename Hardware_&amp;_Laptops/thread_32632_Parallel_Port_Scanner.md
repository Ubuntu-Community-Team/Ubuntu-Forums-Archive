---
title: "Parallel Port Scanner"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by Jellus on 2005-05-08
Hi all,

I discovered that to get my parallel port scanner recognised i have to do modprobe ppdev first ... 
I can only use Xsane as root for now by the way ... but there are ways to fix this i have read although i dont know how to do it yet ...
if anybody can help me here please do .. also i would like to put modprobe ppdev in a startup script or so ... can anybody tell me where i should do this ... and how ... 

greetings,

Jellus

---

### Post by ming0 on 2005-05-08
You should be able to go into the system menu and open up the users/groups manager. It should ask for your password, and then find your username and double click it. Choose the tab on the far right (groups or permissions or something) and put yourself into the scanner group. (you will need to log out and back in for this to take effect)
 
then use the following command: sudo gedit /etc/modules and add ppdev to the bottom of the list.
 
Sorry for being vague, but I happen to be in windows right now (video editing), so I can't be precise. If you run into trouble, or can't find something i've mentioned, just post here again, and I should be in Ubuntu by then :)

---

### Post by Jellus on 2005-05-09
Hi ming0,

I have done what you said ... lets see what happens ...
I am rebooting as i am typing now ... typing on another linux box :)
in case you are wondering ...
After rebooting ... doing
as root user sane-find-scanner -p .. i am able to find my mustek scanner ....
so it works ...
Thanx lots for helping me out with this ...

My next problem is getting it to work as a normal user ....

reading up on the matter ... i found out that there are two ways .. 
1) using libieee1284
2) using saned

It also says the first method, i.e. using libieee1284 is preferred ...

If anybody can help me out with this .. please do ..
It would help me a lot ...

Greetings,

Jellus

---

### Post by Jellus on 2005-05-11
Hi all

I will give it a try myself ... but please feel free to help me out if you know something on this subject

Greetings,

Jellus

---


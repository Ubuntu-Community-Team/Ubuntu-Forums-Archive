---
title: "Dell Inspiron 6000 - Firefox + wireless"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by sandip_s on 2006-09-21
Hi,

I just installed Ubuntu onto my laptop last night. Everything worked very well ie. sound, graphics, even my bluetooth drivers, etc. But when i started firefox, i noticed a problem. When i go to the ubuntu webiste as in this forum, it works fine for but when I try to go to other internet sites, eg [www.google.com](www.google.com). It loads for a few minutes and then tell me the server has timed out. 

I would be greatful if someone can kindly help me to resolve this.

Thanks,

- Sandip

---

### Post by xyz on 2006-09-21
> **sandip_s said:**
> Hi,

I just installed Ubuntu onto my laptop last night. Everything worked very well ie. sound, graphics, even my bluetooth drivers, etc. But when i started firefox, i noticed a problem. When i go to the ubuntu webiste as in this forum, it works fine for but when I try to go to other internet sites, eg [www.google.com](www.google.com). It loads for a few minutes and then tell me the server has timed out. 

I would be greatful if someone can kindly help me to resolve this.

Thanks,

- Sandip

Hi Sandip,
I've been battling with this the pas few days.
> It loads for a few minutes and then tell me the server has timed out. 
[http://www.ubuntuforums.org/showthread.php?t=260715](http://www.ubuntuforums.org/showthread.php?t=260715)

and found no other solution to get FF working but to restore my backuped system.
Note that absolutely no sites were available, even this one while Konqueror worked. I couldn't figure it out! :confused:

Toshiba Satellite A 40

---

### Post by sandip_s on 2006-09-21
my version of Ubunto doesnt have Konqueror. Is there any way I can get it and is this garenteed to work? It would be nice if i could get firefox to work some how... ??

---

### Post by xyz on 2006-09-21
> **sandip_s said:**
> my version of Ubunto doesnt have Konqueror. Is there any way I can get it and is this garenteed to work? It would be nice if i could get firefox to work some how... ??

Garanteed...I don't know about that but trying sure won't hurt!
1. Open Synaptic click on Search and type   knoqueror  in the dialogue box and OK. Then select konqueror and right-click on it to "Mark it for installation" ...or something similar- To remove (in case it's not guaranteed!), right click and "Mark for complete removal".

OR type in a console:
```
sudo aptitude install konqueror

and to remove

sudo aptitude remove konqueror
```

I'm not sure about that but can't it be found also in "Add/Remove"?

Let me know how it goes and if you can surf with konqueror. Good lick.

---

### Post by sandip_s on 2006-09-21
Thanks for that mate. I will try as soon as i get home tonight.

take care

---

### Post by xyz on 2006-09-21
> **sandip_s said:**
> Thanks for that mate. I will try as soon as i get home tonight.

take care
No problem...let us know how goes it! :D

---

### Post by xyz on 2006-09-21
Konqueror does show in Add/Remove!
However, you'll find the Epiphany browser in there. Just in case....hey you could browse with 15 different browsers at the same time!!!lol on 15 different work spaces!!
Just kidding...hope all works well for you.

---

### Post by sandip_s on 2006-09-21
hi tnx 4 that its working with Konqueror. has any body had the same problem and some how got it 2 work with firefox is well??? please let me know tnx

---

### Post by xyz on 2006-09-22
> **sandip_s said:**
> hi tnx 4 that its working with Konqueror. has any body had the same problem and some how got it 2 work with firefox is well??? please let me know tnx

To get FF back, among other things, I restored my system.
Now I have locked kernel updates.
Glad you can use Konqueror. It doesn't work very well in my box for some reason.

---

### Post by lH)4~mK0e on 2006-09-23
Is this through wireless? Or are you hardwired?  If you have entered your key incorrectly for an encrypted network you will only open cached pages.  It sounds like a problem with dns.  Open a terminal and do an:

```
nslookup google.com
```

If you get a Server: with an ip address then your dns is functioning.  Also, make sure you have your Default route defined if you are running both network cards.  If your wireless is the one you connect to for internet, make sure the Network Properties have "eth1" as your "Default gateway device."

The utility you use is:

```
sudo network-admin
```

I have the very same laptop and none of the problems.

---


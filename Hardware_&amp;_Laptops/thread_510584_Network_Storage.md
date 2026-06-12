---
title: "Network Storage"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by milpool on 2007-07-26
I am looking for a network storage solution that I will be able to use as my media "server", where i can throw all my music, movies and pictures on and be able to access from any system. I would like this to work with Ubuntu, OSX and Windows. It would also be awesome if I would be able to access the files while i am not on my home network, over the internet somehow. So I could still play my music on the go, yet not waste space. If anyone has any ideas for how I could do this, I would really like to here them. One forum post suggested a NSLU2. Does anyone have experience with this? does it perform the tasks I discussed above? any input would be greatly appreciated, thanks.

---

### Post by obrient on 2007-07-26
I have something setup here at my place like that. I have basically a machine with a mounted samba share so windows and Macs will see it. In this share I have all of my music. The machine that is doing this is a Ubunu box with Samba enabled and a static IP.

To do sharing music over the web I have a web server running and mount the samba share over my network and then use a php based app called Kplaylist. This allows me to login and stream my music without much trouble at all.

Hope this give you some ideas.

---


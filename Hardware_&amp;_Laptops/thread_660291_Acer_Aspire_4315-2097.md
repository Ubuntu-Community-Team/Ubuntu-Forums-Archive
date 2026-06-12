---
title: "Acer Aspire 4315-2097"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by thrust on 2008-01-06
This laptop has an atheros wireless card i think its an Atheros AG5007AG. after ubuntu 7.10 install everything seems to be working fine except the wireless card. when i launch the network manager only wired and modem connection show up. when i look in the restricted drivers manager it shows my wireless card. so it looks like that ubuntu recognizes it. i just have to get it working. did anybody else run into this problem before? do i have to use the ndiswrapper thing or what? i never had any problems with ubuntu and wireless before.  any help would be appreciated. 

thanks.

---

### Post by doubleij on 2008-01-08
Hi Thrust,

I am just getting my 4315 configured and I ran into exactly the same problem. This link appears to address the issue, although I haven't tried the solution yet myself. 

[http://ubuntuforums.org/showthread.php?t=636045&highlight=Acer+4315](http://ubuntuforums.org/showthread.php?t=636045&highlight=Acer+4315)

hope it works,

doubleij

---

### Post by doubleij on 2008-01-10
Hi,

Still wrestling with my Acer wireless card. The link I posted above didn't help me out. However, I found this one just a few minutes ago. It looks much more promising. Let me know how it goes for you.

[http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)

---

### Post by jimmyridge on 2008-03-13
guys you need the patched madwifi driver and u need to install it yourself each kernel upgrade

oh yeah fyi i dont think it works with x64 

heres what my searching brought 

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

if that isnt the right link for the patch i have a copy of what i use on my AcerAss-pire 4315

[http://home.fuse.net/sh0rt/](http://home.fuse.net/sh0rt/)

my tarball has been prepatched with aircrack injection and AR5007EG support also the patches i used are on the site if you want to do it yourself  aircrack has a great wiki for patching/installing wifi

i cracked open the bottom of my laptop and had a look see couldnt believe it but only one antenna cable was installed i need to hack me a new antenna cause they have two ports

---

### Post by scottro on 2008-03-14
For what it's worth, my own page on it.

[http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007)

---


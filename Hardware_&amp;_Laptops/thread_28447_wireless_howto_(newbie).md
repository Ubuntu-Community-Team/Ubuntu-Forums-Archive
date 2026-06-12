---
title: "wireless howto (newbie)"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by anando on 2005-04-20
Hi there

My Ubuntu installation (5.04) works pretty well out of the box - in particular it detects the wireless card and I am pretty happy with it. The only thing was the synaptics driver - I wanted to put that patch in so as to disable touch pad annoyances (like tapping) - so I compiled the kernel with the alps-synaptics patch as given in these posts ... [http://ubuntuforums.org/showthread.php?t=27851](http://ubuntuforums.org/showthread.php?t=27851)

Now the synaptics-driver works and I can disable the touch pad tapping and other things ... BUT _my wireless is no longer detected_. In fact there is no eth1 any more. [eth0 is there - but that is the regular cable thingie which I use to connect to my office LAN]. Previously (before the patch) when I went to System->Administration->Network  I could see eth1 as well as eth0. Now after I patched the kernel (above) I see only eth0  :| 

So - can someone please help ? I am really stuck !! 

Anando.

---

### Post by localzuk on 2005-04-20
Did you include support for wireless in your kernel when you compiled it? It sounds like you didn't. Have a look at it again and see.

---

### Post by anando on 2005-04-20
[QUOTE=localzuk]Did you include support for wireless in your kernel when you compiled it? It sounds like you didn't. Have a look at it again and see.[/QUOTE]

OK sorry to ask you this extremely dumb question - how do I compile the kernel with the wireless option ? 

Many thanks for your help,
Anando.

---

### Post by flipy on 2005-04-20
go to "device drivers", find "net" and "wireless". I'll make everything as modules, because it makes your bzImage smaller (and faster to load).

---


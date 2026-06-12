---
title: "Help with getting the most out of an atom-based Ubu server"
date: 2011-08-26
forum: Hardware
---

### Post by jrebelo on 2011-08-26
Hi guys, this is just a bit of a general query for tips or ideas you might have. Any help is appreciated.

I have recently wiped a little Acer D250 netbook (Atom N270, 1GB ram) and installed ubuntu server 11.04 on it. The primary purpose of the computer will be as an sshd server which I will connect to from work every day so I can resume my screen session with irc and rtorrent etc. The secondary use of the system is as a simple lamp server with apache, php and mysql for me to test scripts I develop occasionally (but only personal use and performance with that isn't a big deal). Additionally, the netbook will have a 500gb usb2 drive attached at all times which will be shared over my network (wired) using samba so that I can play videos off of the network share from my laptop.

The system is up and running and I've already got samba and my lamp stuff going. It's not as responsive as I'd like, but I'm not sure if it's strictly just the limitations of the hardware and as good as I'm going to get or if I am missing out on some optimizations which might make it perform with more snap.

Any suggestions on other things I might do to increase general responsiveness on this machine for doing my daily tasks?

FYI: I did a selective ubuntu server 11.04 install, only installing the openssh, lamp and samba components, so the entire system installed is only about 1GB. Apart from apache/mysql (which are basically always idle), the only software I'm normally using is irssi, rtorrent, elinks and vim.

---

### Post by Beacon11 on 2011-08-26
You really should be fine... when you say it's not as responsive as you'd like, what do you mean? Streaming takes basically zero processor unless you're transcoding-- I stream HD off a 1GHz ARM processor all the time. Is it the LAMP setup that seems slow? That same 1GHz ARM runs PHP just fine, although it's not cranking a lot of numbers. What are you hoping for?

---

### Post by jrebelo on 2011-08-26
Hi Beacon. Sorry I wasn't clearer. What I meant was the shell isn't very responsive. When I ssh into the system, after providing my password, there's a pretty solid 3 second delay before actually getting a prompt. Starting a new screen window has a noteable pause. Basically stuff that would normally happen instantly on a regular system takes time on this system. I know it's expected it won't be as snappy as a desktop box, but since I don't have a reference point to compare to, I don't know if this could be better or not, hence the look for any general tips I might just not know about. I imagine it's most likely behaving as expected, but as I said, I've nothing to compare to.

---


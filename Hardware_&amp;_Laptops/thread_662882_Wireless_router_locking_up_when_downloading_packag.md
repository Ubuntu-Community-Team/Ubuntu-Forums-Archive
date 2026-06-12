---
title: "Wireless router locking up when downloading packages"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by brakjoller on 2008-01-09
I have successfully enabled my Belkin wireless card on my old Dell Latitude CPx under Ubuntu 7.10. I can surf and everything. 

However, if I use the software manager to download new packages or if I need updates, after downloading for a few seconds, the download stops. It never starts again. What's more, my main computer, a tower, connected to the wireless router by cable, also lose its net connection, and I cannot even logon to the admin interface to the router anymore. So even if it has the LEDs on, and I think some are even blinking, it seems to be stuck. It's as if the download dialog does something nasty or something my router does not like.

I just installed 7.10 and don't remember having this problem under 7.04 which was installed previously, so it seems to be a combination of problems, but I have no idea on where to start looking for the reason.

Some facts:

Ubuntu 7.10, with the latest upgrades (if I use a normal network card with cable I can download all I want)
Dell Latitude CPx
Belkin Wireless G Notebook Network Card with HSM, model no F5D7011
Netgear Wireless Router WGT624
Using ndiswrapper to get the Belkin card to work
I use WAP for encryption but also tried without it

I'd be grateful for any hints on things to try.

Thanks!

---

### Post by hellofawedge on 2008-03-01
G'day brakjoller,

I've got exactly the same issue with the WGT624. My setup:

[LIST=1]
[*]Xubuntu 7.10
[*]AP=WGT624
[*]Dell Inspiron 8100 with the Netgear WG511T PCM wireless adapter
[/LIST]

All's well (browsing, email, etc...) until an ftp is attempted (i.e. Ubuntu update download primarily). The ftp will commence, but after a short time, any device attahced to the router loses net connectivity. If the router is recycled/reset, the ftp will recommence (once the wireless connection has re-established). Again, a short time later the ftp will cause the router to drop it's bundle.

I have found that running a ping session to the router during the ftp can sustain the ftp session for a little longer.

Nice to finally hear someone else is experiencing this, I've been scouring the net to find a similar occurence!! :roll:

---

### Post by brakjoller on 2008-03-01
> **hellofawedge said:**
> 

G'day brakjoller,

I've got exactly the same issue with the WGT624. My setup: 
...  
Nice to finally hear someone else is experiencing this, I've been scouring
the net to find a similar occurence!! :roll:



In a way it feels good that I am not alone :), but I would rather
solve my problem. My current workaround is to use a normal, wired,
network card, when fetching updates. Boring though :(

/Mathias

---


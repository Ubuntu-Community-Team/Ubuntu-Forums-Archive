---
title: "Toshiba Satellite M40 Networking"
date: 2006-05-03
forum: Hardware &amp; Laptops
---

### Post by Bonez56 on 2006-05-03
Hi all

I've recently aquired a Toshiba Satellite M40 notebook and i'm trying to install Ubuntu and get it all up and running.

During the setup phase, it tries to detect network via DHCP. I do have a DHCP server running, however it does not detect anything. I've tried multiple ethernet cables and ports on the switch, and nothing works.

After setup is complete, I still can not get any kind of networking to work.

The laptop has an Intel wireless card in it too, which i'm also having no luck with.

With this distribution (5.10) should I really have to install and compile my own drivers for a Marvel Yukon 10/100 network card, or an ip2200w wireless card?

Surely it has support...

Has anyone else sucesfully got this working straight out of the box?](*,)

---

### Post by cyangecko on 2006-05-03
Hi Bonez,

I had a similar problem installing Breezy on my Toshiba Satellite M100.  It also wouldn't recognize my networks (wired or wireless) during installation.  I did try an older PCMCIA ethernet card and it recognized that and installation went from there, though I had more issues other than DHCP connection further on in the installation process.  I ended up downloading the Dapper Beta and installing it.  With Dapper everything was recognized from the start and I can't say I've had a problem I couldn't fix with it so far, so perhaps that might be a solution for you as well.  Goodluck.

---


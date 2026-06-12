---
title: "Packages involved in PCMCIA hardware"
date: 2010-05-25
forum: Hardware
---

### Post by lunav on 2010-05-25
Hi everyone !

I installed ubuntu 9.04 on an old laptop to turn it into a server (N.B.: All "servers" version of ubuntu aren't working, but that's not the problem). After removing the gnome environment everything was working well but slowly and I had a lot of packages I didn't wanted.

So I grab a copy of the Ubuntu Minimal CD 10.04 and installed the very minimum system on my computer (no extra packages, nothing). It works great and boot real fast but I have one problem. Now my ethernet PCMCIA Card don't allow my computer to access to the internet. The leds of the card are glowing but ifconfig returns nothing but "**lo**".

I though installing the package _pcmciautils_ would fix the problem but it's not the case. So I'm asking you, what packages do I need to be installed in order to get my PCMCIA Ethernet Card to work ?

Thank you very much for your answers ! :)

---

### Post by Musicologynut85 on 2010-05-28
You might try getting the package "setserial." I've heard that works. You also might see if you need some type of "pcmcia-support" package or something like that.

So... yeah... good luck, I can't get my PCMCIA card working either. If I get a solution to my problem I'll link you to it and you can see if it works for you.

---


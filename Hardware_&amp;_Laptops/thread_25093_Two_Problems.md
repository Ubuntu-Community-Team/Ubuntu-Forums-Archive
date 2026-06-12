---
title: "Two Problems"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by Svip on 2005-04-09
I got two different problems, so the first is the most important for me.

1.
I have a DVD drive and a CD-RW drive. However, I had the DVD as primary before I installed Ubuntu, but there was problem with it reading the disc so it crashed through the installation, so I changed the primary and slave. However the wire was not long enough to fit both on where they were placed at that time. So the CD-RW was primary, and the DVD was not plugged in through the installation.

After the installation I took both out and fitted them both so the CD-RW kept being primary and the DVD was after that slave.

However, because of that I have been having some problems with the DVD drive meaning that only some times it will read and mount, at most orcasions it wont.

How do I fix that?

2.
A friend of mine has a scanner, however his computer is currently  and wont scan and such, so he wants to sell it to me for a fair price. But it's not a known trademark that has made it, I don't know if Medion is known for you people.

But also it is an USB-scanner, meaning that it comes through an USB plug.

Is there anyway I can install that?

3.
( not a problem, but a question )
I just got a new nVidia graphic card ( because my last one killed my computer ( yes, it was  ) ), and the graphics seem to work because I had installed the driver through apt-get, but I am wondering if I should re-get it. Or if it just fine.

Thanks in advance. :)

---

### Post by p!=f on 2005-04-09
[QUOTE=Svip]I got two different problems, so the first is the most important for me.

1.
I have a DVD drive and a CD-RW drive. However, I had the DVD as primary before I installed Ubuntu, but there was problem with it reading the disc so it crashed through the installation, so I changed the primary and slave. However the wire was not long enough to fit both on where they were placed at that time. So the CD-RW was primary, and the DVD was not plugged in through the installation.

After the installation I took both out and fitted them both so the CD-RW kept being primary and the DVD was after that slave.

However, because of that I have been having some problems with the DVD drive meaning that only some times it will read and mount, at most orcasions it wont.

How do I fix that?
[/quote]
Please be more descriptive when you say "some problems".
Broken DVD drive? Can you replace it with another one to see any difference?

[QUOTE=Svip]
2.
A friend of mine has a scanner, however his computer is currently messsed and wont scan and such, so he wants to sell it to me for a fair price. But it's not a known trademark that has made it, I don't know if Medion is known for you people.

But also it is an USB-scanner, meaning that it comes through an USB plug.

Is there anyway I can install that?
[/quote]
Please post the model number here.

[QUOTE=Svip]
3.
( not a problem, but a question )
I just got a new nVidia graphic card ( because my last one killed my computer ( yes, it was messsed ) ), and the graphics seem to work because I had installed the driver through apt-get, but I am wondering if I should re-get it. Or if it just fine.
[/QUOTE]
Switching the cards should be sufficient if you're running Hoary which has the latest nVidia drivers installed (7174 as of today). You need nvidia-glx, nvidia-kernel-common, linux-restricted-modules for your kernel version and your architecture and you should be safe. You might want to install nvidia-settings and nvclock-gtk for tweaking / overclocking your card.

And please, try to replace "messsed" with something more friendly next time. :)f

---

### Post by Svip on 2005-04-09
Well, sorry about the title, but I hoped people would look into it anyways.

For the scanner; it's MD 4394.

And the DVD drive ain't broken, it's just doesn't mount at all time, maybe it is broken however, but I guess I can live with it.

And sorry for the choice of words.

---


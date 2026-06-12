---
title: "Installed ATI Driver, Now I can't Get Into PC"
date: 2010-08-22
forum: Hardware
---

### Post by netsavy006 on 2010-08-22
I can't figure out how to fix my problem. I went to system > administration > hardware drivers, and it mentioned of a driver for my ati driver for my computer that would allow me to have 3d settings since I was told by an app I didn't have that, I decided to activate the driver. It installed it and told me I needed to reboot. But after that I couldn't get into my computer. I just see the Ubuntu name / logo and the 4 dots underneath with the purpleish background and it doen't progress further. And I don't know what to do. i'm using my cd's try mode right now to communicate all this. Please help me.

---

### Post by martin_legion on 2010-08-23
Have you tried booting in safe mode?
after doing so you can try this command to see if it helps:

sudo dpkg-reconfigure xserver-xorg

---

### Post by netsavy006 on 2010-08-23
I fixed this problem by reinstalling Ubuntu 10.04.

---

### Post by martin_legion on 2010-08-24
The good old Windows way :P

---

### Post by slooksterpsv on 2010-08-24
> **netsavy006 said:**
> I fixed this problem by reinstalling Ubuntu 10.04.

I know the issue is solved, but if you do run into the problem again, here's a few things to try:
Boot the computer then press CTRL+ALT+F2
Type in username - enter
type in password - enter (password won't appear)
Try running: aticonfig --initial -f - reboot after

Still not fixed, do the same as above but run:
sudo apt-get remove fglrx - enter
Have it remove it and reboot.

That should fix it. I ran into that issue with Maverick Alpha.

---

### Post by Chris1274 on 2010-08-24
I had the same issue, and used your fix too ;) 

Unless you're a gamer, those ATI cards are more trouble than they're worth. If it weren't soldered to my motherboard I'd just as soon pull the thing out and be done with it. The integrated gpu handles compiz just fine.

---


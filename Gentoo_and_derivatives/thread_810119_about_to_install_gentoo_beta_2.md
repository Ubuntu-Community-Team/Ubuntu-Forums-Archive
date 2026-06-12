---
title: "about to install gentoo beta 2"
date: 2008-05-28
forum: Gentoo and derivatives
---

### Post by myusername on 2008-05-28
anything i should know? i dont think my wireless is gonna work during the install :(

---

### Post by ghindo on 2008-05-28
Just know that you're going to be kicking back watching things compile for a while.

---

### Post by myusername on 2008-05-28
awesome </sarcasm> is it hard or just tedious?

---

### Post by ubersolid on 2008-05-28
It's not very difficult to install at all,just time consuming. I recommend following this guide:
[http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml](http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml)

I used that guide setting up my server at home.
Daniel Robbins has some stages too that I like to use:
[http://www.funtoo.org/linux/](http://www.funtoo.org/linux/)

Happy compiling!

---

### Post by Raven_Oscar on 2008-05-28
myusername
Well I'm going to try gentoo too. After brief reading of Gentoo Handbook I can say just one thing. It is going to be a little harder (but not to much) and a little bit longer than debian or ubuntu installation. The only thing I can recommend is to read [Handbook]("http://www.gentoo.org/doc/en/handbook/index.xml")   before installation.

---

### Post by regomodo on 2008-05-28
> **Raven_Oscar said:**
> myusername
Well I'm going to try gentoo too. After brief reading of Gentoo Handbook I can say just one thing. It is going to be a little harder (but not to much) and a little bit longer than debian or ubuntu installation. The only thing I can recommend is to read [Handbook]("http://www.gentoo.org/doc/en/handbook/index.xml")   before installation.

I think you are underestimating the time/difficulty required, or both. Don't give up after the first few failures is all i can say.

---

### Post by trimeta on 2008-05-28
If everything works fine, it's just long; for a first install, I'd recommend using genkernel, unless you have experience compiling kernels.

---

### Post by trigggl on 2008-05-29
If you're worried about stability, I'm running 2008 beta 2 on my IBM PowerPC and it's doing just fine.  Just do the minimal install you need to get it booting and then make sure you've got ccache installed and working.  I've got 3 identical boxes, so my installations are sped up some by distcc.  Once you've got all your chosen features set up like ccache and distcc(if you have more than one machine), then do your updates and continue the install.

I've experienced very few dependency problems and most of those were very easy to fix.

The main thing to keep in mind is that it's going to take a while and tie up the machine.  Once I get my machines to where I can ssh to them, I do the rest from my main PC.

---

### Post by LinuxGuy1234 on 2008-06-13
I have Gentoo. I followed the guide to install it. Here's what you do:
1. sudo mkdir /mnt/gentoo
2. mount /dev/<device> /mnt/gentoo; sudo wget -P /mnt/gentoo <URL to stage3>; cd /mnt/gentoo; tar xvjpf stage<TAB>; sudo chroot . bash
3. env-update; source /etc/profile
4. Review files and modify them.
5. emerge stuff needed.

---


---
title: "Building a Linux Box for DVR use, need help."
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by BinaryWarrior on 2006-10-12
I just recently found my very old PC and am converting it into a DVR for use with my Comcast cable :-# .  I need to know limitations on hard drive sizes :-k  in Ubuntu and other such knowledge.  Where should I look for this?

---

### Post by Jussi Kukkonen on 2006-10-12
Linux doesn't have hard drive or partition limitations (that would matter), but the BIOS of an old machine might...

DVR setup can be pretty tricky (depends on the software of course), and using older hardware doesn't make it any easier. Ubuntu as such shouldn't be a problem -- the problems will probably be general linux problems. That said, some DVR systems are easier to build on some distros because the guides are written for them, and Ubuntu mostly isn't included in those distros. Regardless, personally I like to use what I know, and that's why my VDR runs Ubuntu (using VDR packages for Debian)...

---

### Post by BinaryWarrior on 2006-10-12
What distro would you suggest?  I have not worked in Ubuntu much yet I have used Fedora Core 1 & 5 more than any other distro.  I would like to run Ubuntu simply because all of the great help this community gives.  So I guess my next question is where can I get the VDR packages?

---

### Post by BinaryWarrior on 2006-10-12
Would it be better to use Mubuntu?

---

### Post by Jussi Kukkonen on 2006-10-12
Like I said, the distro choice depends on two things:
A) use whatever you know
B) use whatever is most used with the software you choose

If your video recorder software is e.g. MythTV, the choice would be obvious: Fedora is used quite a lot and you know it already...  If you have chosen VDR (I have no idea if that's even usable where you live), then I'd say your choices are:
* LinVDR [http://linvdr.org/projects/linvdr/index.en.php](http://linvdr.org/projects/linvdr/index.en.php)
* Fedora (since you know it)
* Ubuntu (since the community is, as you say, nice)
Like I mentioned I chose Ubuntu, and I've been pretty happy with it. 

If you decide to use VDR and Ubuntu, I'd advice you to use up-to-date source packages from either
* Debian VDR Subversion: [http://pkg-vdr-dvb.alioth.debian.org/](http://pkg-vdr-dvb.alioth.debian.org/)
* e-tobi repository: [http://www.e-tobi.net/](http://www.e-tobi.net/)
Be prepared to compile other libraries from source too, if your harware won't play nice...

---

### Post by BinaryWarrior on 2006-10-13
Thx so much, you have been a great help.  When I originally looked up the the idea of a self made DVR I read an article about using MythTV, but I have not totally checked it out yet guess I will have some digging to do, especially since I have to find out what the computer actually has in it hardware wise.

---


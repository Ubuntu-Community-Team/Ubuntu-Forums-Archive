---
title: "Canon MP970 scanner"
date: 2008-07-15
forum: Hardware
---

### Post by tvds on 2008-07-15
Hi,

I have a Canon MP 970 scanner (network connected) which I like to use within Ubuntu.

I installed sane, but have no Idea how to config to be used with xsane or any other scan-program.

Has anyone a MP 970 (network connected) running on Ubuntu.

Thanxs

---

### Post by llagendijk on 2008-08-14
> **tvds said:**
> Hi,

I have a Canon MP 970 scanner (network connected) which I like to use within Ubuntu.

I installed sane, but have no Idea how to config to be used with xsane or any other scan-program.

Has anyone a MP 970 (network connected) running on Ubuntu.

Thanxs
well, not connected to Ubuntu, but to a Fedora 9 box. You will need a cvs copy of sane though. I have been working on it with the author of the pixma driver for Sane and we got it working. The Sane version that support the MP970 is however not formally released yet

---

### Post by tvds on 2008-08-15
So okay... I'll wait for the new version than. Thank you.

---

### Post by poslusny on 2009-01-31
Are there any news about driver for MP970 ?? :(

---

### Post by exXplode on 2009-10-03
I know, it's been a while, but just to point you to the solution in case anybody will find this thread via Google (just like me):

Just get the latest sane backends, compile them and install them and there you go...

so open a terminal and enter the following commands one after the other:
```

sudo aptitude install libusb-dev
git clone git://git.debian.org/sane/sane-backends.git
cd sane-backends
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install
```

now ```
scanimage -L
``` should show you your Scanner. And **xsane** should work too!

And remember to allow network communication to your printer if you use a firewall (port 8611 to 8614)!

in 9.10 karmic the sane backends are included in v.1.0.20 so then you will not need this anymore!

ressources: [http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)

---

### Post by Clean3d on 2009-10-05
Thanks, exXplode. I just tried your solution and got a good scan with no problems. :)

---

### Post by egyn on 2010-11-13
eXxplode,
have you managed to the get the printer running as well, not just only the scanner?

/egyn

---


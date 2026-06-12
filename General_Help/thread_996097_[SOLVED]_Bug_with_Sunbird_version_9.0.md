---
title: "[SOLVED] Bug with Sunbird version 9.0?"
date: 2008-11-28
forum: General Help
---

### Post by desconocido on 2008-11-28
Hi,

I had Sunbird 7 working (installed via Synaptic) but with the well known time/time zone bug. 

So I wanted to install version 9.0. Version 7 appears to be the latest available via ubuntu repositories, so I downloaded version 9 from
[http://www.mozilla.org/projects/calendar/sunbird/](http://www.mozilla.org/projects/calendar/sunbird/)
and followed the instructions at
[http://www.mozilla.org/projects/calendar/releases/sunbird0.9.html#install](http://www.mozilla.org/projects/calendar/releases/sunbird0.9.html#install)
using
sudo tar -xzvf sunbird-0.9.en-US.linux-i686.tar.gz
instead of their
tar -xzvf sunbird-0.8.en-US.linux-i686.tar.gz

So I try
bob@faustino:/usr/share/sunbird$  ./sunbird
and get:
./sunbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Is this something I have done wrong while following their installation instructions? Or is it a bug with version 9? Or do I have to wait until version 9 is in the repositories before I can use it? It would be nice to get an entry in the Applications panel at the top of the screen too - can't work out how to do this.

(As an aside, can I install unix programs in general or only ubuntu programs? I may have some problems with some concepts here.)

Thanks in advance.

Bob

---

### Post by rogue_ronin on 2008-12-07
Go here for a .DEB of Sunbird 0.9

[http://www.getdeb.net/app/Sunbird]("http://www.getdeb.net/app/Sunbird")

Good luck.

m a r

---

### Post by screeeeeemin on 2008-12-09
The deb package was the only way I could get Sunbird 0.9 installed. 

I not very experienced but I know how to find and read instructions. I spent way to long on this until I tried the deb package.

The Sunbird download page offers: sunbird-0.9.en-US.linux-i686.tar.gz
Doesn't "686" imply that it is for 64 bit?

For me, this issue is "SOLVED" and should be marked as such so other can benefit. Is that the posters job?

---

### Post by Vadi on 2008-12-09
screeeeeemin: i686 means 32bit. 64bit would be x86_64.

Sunbird really should consider a more user-friendly way of installing their program on Ubuntu like a .deb.

---

### Post by Reno II on 2008-12-10
> **rogue_ronin said:**
> Go here for a .DEB of Sunbird 0.9

[http://www.getdeb.net/app/Sunbird]("http://www.getdeb.net/app/Sunbird")

Good luck.

m a r


Thanks rogue_ronin!
It worked fine. Excellent package. Worked smoothly on 8.04 LTS 'Hardy'
Now, Sunbird 0.9 works perfect together with Google Calendar add on.

---

### Post by desconocido on 2009-01-01
Just noticed we are talking version 0.9 not 9.0. That makes quite a difference to my expectations of installability.

---

### Post by desconocido on 2009-01-01
I got some help with this from the Mozilla forum:

> Thanks, I installed libstdc++5 and sunbird 9 now works. (I had to completely remove sunbird 7 first though - partial remove with synaptic does not work.)

I suppose I was expecting synaptic to know which libraries sunbird needs, but I guess the fact that I was installing version 9 outside the approved/secure way of installing software left synaptic clueless.

I tried using Applications > Add/Remove Programs....
to add sunbird to the Applications menu but it insisted on trying to install version 7, so I gave up on that. Guess I have to wait until the new version of sunbird is available via synaptic.

I managed to make a panel icon for Sunbird, so that's half way there. 0.9 works OK for me now, so I think I will wait for 1.0 to be available before trying [http://www.getdeb.net/app/Sunbird](http://www.getdeb.net/app/Sunbird)

Thanks.

---


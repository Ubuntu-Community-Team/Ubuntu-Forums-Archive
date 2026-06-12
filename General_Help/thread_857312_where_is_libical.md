---
title: "where is libical?"
date: 2008-07-12
forum: General Help
---

### Post by MountainX on 2008-07-12
I installed libical0 using Synaptic. I'm using it for wxDatalinkUSB (for the Timex watch). However, wxDatalinkUSB cannot find libical. I can't find it either. Where is it? (I tried find...)

---

### Post by MountainX on 2008-07-12
Never mind. It was in /usr/share/libical

Now I just have to figure out why wxDataLinkUSB won't find it...

---

### Post by MountainX on 2008-07-12
Here's where I'm stuck:

I'm getting an error related to libical. I installed libical from the Ubuntu Hardy repos.

~/temp/wxDatalinkUSB-0.0.4$ ./configure
configure: error:
        *** libical library not found!
        Go to [http://www.citadel.org/doku.php/installation:start](http://www.citadel.org/doku.php/installation:start) for libical
        or to [http://wxdlusb.sourceforge.net/installation.htm](http://wxdlusb.sourceforge.net/installation.htm)
        for help installing wxDatalinkUSB.

        Did you make sure that /usr/ld.so.conf includes the libical path?
        Did you run ldconfig?

$ find -mount / -iname libical
/usr/share/libical
/usr/share/apps/libical

Contents of  /etc/ld.so.conf:
include /etc/ld.so.conf.d/*.conf
# for wxDatalinkUSB Timex watch 12jul2008
/usr/share/libical

I ran ldconfig. It simply returns with no message.
~/temp/wxDatalinkUSB-0.0.4$ sudo ldconfig
~/temp/wxDatalinkUSB-0.0.4$

Any suggestions? Thanks.

---

### Post by MountainX on 2008-07-12
I solved the libical error by installing libical-dev from the Hardy repos.

---


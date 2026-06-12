---
title: "Remote esound"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by Brent Dax on 2005-09-08
I have a laptop and a desktop.  The laptop is a fairly nice little Winbook (yes, I'm aware of the irony) with a Pentium D running Ubuntu (Hoary).  The desktop is a rather large AMD64 machine also running Hoary.

The desktop also has an Awesome Sound System(tm).  I sometimes use my laptop when I'm near my desktop, and as such would like to take advantage of this Awesome Sound System(tm) at times.  My research shows me that esound can run over a network, and I've even figured out how to start esd on my desktop with a port open to listen for connections.  What I haven't figured out is how to get sound into this--and do so in a way I can turn off, perhaps simply by clicking a button somewhere on my Gnome panel.

So, my questions:[list]
[*]Am I on the right track with esound?
[*]What should my next step be?
[*]Am I totally nuts for trying this?
[/list]

Thanks for your time.

---

### Post by astopy on 2006-05-18
Did you ever get this working?  I'm at exactly the same stage right now.

---

### Post by MaskedMarauder on 2006-11-14
It works pretty much as advertized.  I used to use xmms with amarok & castpodder to send the audio to the machine with a good output & speakers.

It stopped working in dapper.  For some reason the esdound plugins for the various tools no longer exist.  

I don't know why they dropped it.  It was the best thing since sliced bread.

---

### Post by Tex-Twil on 2008-04-02
Hello,
I'm trying to compile esound but I have the followinf error:

```

$ make
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c esddsp.c
gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c -fPIC -DPIC esddsp.c -o esddsp.lo
esddsp.c: In function 'open':
esddsp.c:172: error: 'RTLD_NEXT' undeclared (first use in this function)
esddsp.c:172: error: (Each undeclared identifier is reported only once
esddsp.c:172: error: for each function it appears in.)
esddsp.c: In function 'ioctl':
esddsp.c:373: error: 'RTLD_NEXT' undeclared (first use in this function)
esddsp.c: In function 'close':
esddsp.c:392: error: 'RTLD_NEXT' undeclared (first use in this function)
make: *** [esddsp.lo] Error 1


```

Any ideas ?

Tex

---

### Post by Tex-Twil on 2008-04-02
Forget my previous post I didn't realize that esound is in the ubuntu repos.

Anyway, now I have another problem. I don't know to which /dev/... file corresponds my sound card. The manual of esd says :

> 
Possible devices are:  /dev/dsp, /dev/dsp2, etc.

So I tried to run the server but it exists just afterwards:
```

~$ esd -d /dev/dsp -tcp -public -port 7777
- using device /dev/dsp
- accepting connections on port 7777
~$

```
I also tried with /dev/audio but the result is the same.

Thanks
Tex.

---


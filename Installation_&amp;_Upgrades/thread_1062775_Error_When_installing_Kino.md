---
title: "Error When installing Kino"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by Declanthedork on 2009-02-07
So, I was installing Kino from a Tarball. I got as far as ./configure and make, but when I do sudo make install, I get this output in terminal 

```
Making install in po
make[1]: Entering directory `/home/declan/Documents/Code/kino-1.0.0/po'
file=`echo da | sed 's,.*/,,'`.gmo \
	  && rm -f $file &&  -o $file da.po
/bin/sh: -o: not found
make[1]: *** [da.gmo] Error 127
make[1]: Leaving directory `/home/declan/Documents/Code/kino-1.0.0/po'
make: *** [install-recursive] Error 1
declan@declan-desktop:~/Documents/Code/kino-1.0.0$ sudo make install
Making install in po
make[1]: Entering directory `/home/declan/Documents/Code/kino-1.0.0/po'
file=`echo da | sed 's,.*/,,'`.gmo \
	  && rm -f $file &&  -o $file da.po
/bin/sh: -o: not found
make[1]: *** [da.gmo] Error 127
make[1]: Leaving directory `/home/declan/Documents/Code/kino-1.0.0/po'
make: *** [install-recursive] Error 1

```

Do you guys have any help about this? Maybe install a new plugin? Thank you very much

---

### Post by taurus on 2009-02-07
What's the output of this command from a terminal?

```
whereis sh
```

---

### Post by Declanthedork on 2009-02-07
a

---

### Post by Declanthedork on 2009-02-07
> **taurus said:**
> What's the output of this command from a terminal?

```
whereis sh
```
 
 Here's My output
```
sh: /bin/sh /bin/sh.distrib /usr/share/man/man1/sh.1.gz
```

---

### Post by taurus on 2009-02-07
```
ls -la /bin/sh
```

p.s.  I meant the /bin/sh which is basically pointing to /bin/dash.

---

### Post by Declanthedork on 2009-02-07
I did that one, but the output was way too long to post

---


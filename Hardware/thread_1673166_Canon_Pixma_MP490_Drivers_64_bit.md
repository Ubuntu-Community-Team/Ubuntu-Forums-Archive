---
title: "Canon Pixma MP490 Drivers 64 bit"
date: 2011-01-22
forum: Hardware
---

### Post by Sims12345 on 2011-01-22
Hi,

I have a Canon Pixman MP490 printer and I can't get it to print in Ubuntu 10.10 64 bit. I can scan using the built in scanning application but Ubuntu is unable to find any drivers for this particular printer. Any way to make it print?

Thanks :)

---

### Post by jcrc on 2011-01-22
check this:

[http://software.canon-europe.com/products/0010754.asp](http://software.canon-europe.com/products/0010754.asp)
[http://software.canon-europe.com/software/0037269.asp?model=](http://software.canon-europe.com/software/0037269.asp?model=)

don't know if this works, or if it works in 64bits.

---

### Post by Sims12345 on 2011-01-22
After I extracted it, it came with 2 i386 .deb files. I tried installing one of them and its said it was the wrong architecture...

---

### Post by Sims12345 on 2011-01-25
Bump?

---

### Post by deathbysushi on 2011-01-26
I have a Pixma MP560 running on Ubuntu 64-bit. Once you have the deb packages downloaded, run the following:

```
sudo dpkg -i --force-architecture <name of package>
```

This forces a 32bit package to work on a 64bit machine.

I believe you dpkg the common one first and then the printer specific one (that's what I remember doing). Should work perfectly after that!

---

### Post by Sims12345 on 2011-01-27
That worked! Thanks :)

---

### Post by Diametric on 2011-05-08
This forum kicks ***.  i was able to follow the directions from here and get it all hooked up.  My only question is:

why would canon have Linux drivers listed in other countries, but not in the US?  That really irked me.  

Thanks to those who responded!

---

### Post by davequig on 2011-07-04
When I try to dpkg these files i get:
bash: syntax error near unexpected token `newline'


What's going wrong?

---

### Post by j1234d2003 on 2012-01-13
This is bit older thread but Natty/Oneric Canon Printer drivers can be installed from [http://www.upubuntu.com/2011/12/how-to-install-canon-pixma-mp-canon-mx.html](http://www.upubuntu.com/2011/12/how-to-install-canon-pixma-mp-canon-mx.html)

---

### Post by mörgæs on 2012-01-13
Moved to the hardware forum.

---

### Post by dachrinne on 2012-02-13
This solves many of my problems!

---


---
title: "Emergency help!!!!!!!!!!!!!!!!!!!!!!!!!!!!"
date: 2008-11-23
forum: General Help
---

### Post by bandito40 on 2008-11-23
Hi,

I just wrote over my /etc/rcS.sh directory with a script file.  Does anyone know haw I can restore it?

Thanks


Bandito

[http://www.gaihsoa.com](http://www.gaihsoa.com)

---

### Post by AliTabuger7 on 2008-11-23
What version are you using?

I believe that it really makes a difference with all the /etc/rc* files.

---

### Post by oaxacamatt1 on 2008-11-23
Hey Bandito,
One of the first things I do if (no, I should say when I over-write stuff) is I pull out the Live CD.  I always keep that around.  I load up the Live Cd and that gives me access into the Linux file structure.  Then i poke around.  I look to see if Linux has kept a back up copy.  Look for your fiel name with a tilda at the end or .original, or whatever in the same directory.  Linux can be very good about making copies.  Then it is rather a simple process of copying (cp) the back up to the original file name.

Hope this help,
Matt

---

### Post by AliTabuger7 on 2008-11-23
we might be able to just copy and paste one of our versions of that file, depending on what exactly it is and what version you are using.

---

### Post by bandito40 on 2008-11-23
I would like to thank everyone for their support.  Turns out I had moved a file in the follwoing manor:

sudo mv ./compiz.sh /etc/rcS.sh

instead of 


sudo mv ./compiz.sh /etc/rcS.d/compiz.sh

So nothing was lost.  I got lucky, probably shouldn't be messing around in the system files first thing in the morning after a night of partying.  Could have been worse.

Thanks again to everyone,


Bandito

---


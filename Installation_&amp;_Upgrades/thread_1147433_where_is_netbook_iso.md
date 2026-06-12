---
title: "where is netbook iso"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by fminmexico on 2009-05-03
I have downloaded the Ubuntu 9.04 netbook remix twice from different sites, both times it was not an ISO file,but using a special burning program I burnt the file to DVD,both DVDs would not load.Where can I find the remix as an ISO file.
            fminmexico.

---

### Post by logos34 on 2009-05-03
you copy it to USB stick, not disc:

[https://wiki.ubuntu.com/UNR#The%20Easy%20(recommended)%20way](https://wiki.ubuntu.com/UNR#The%20Easy%20(recommended)%20way)

good luck

---

### Post by snowpine on 2009-05-03
Most netbooks don't have a CD drive, so NBR is distributed as a .img file you can "burn" to a USB thumb drive.

---

### Post by fminmexico on 2009-05-03
> **logos34 said:**
> you copy it to USB stick, not disc:

[https://wiki.ubuntu.com/UNR#The%20Easy%20(recommended)%20way](https://wiki.ubuntu.com/UNR#The%20Easy%20(recommended)%20way)

good luck

thank you
  fminmexico.

---

### Post by fminmexico on 2009-05-03
> **snowpine said:**
> Most netbooks don't have a CD drive, so NBR is distributed as a .img file you can "burn" to a USB thumb drive.

thank you
fminmexico

---

### Post by fminmexico on 2009-05-03
> **snowpine said:**
> Most netbooks don't have a CD drive, so NBR is distributed as a .img file you can "burn" to a USB thumb drive.

Did as you suggested to a 2gig USB when I try to load I get boot error.Wiped the USB reloaded the .img still get boot error.Any ideas.
                  fminmexico.

---

### Post by logos34 on 2009-05-03
did you try copying using the dd command method?  if not, try it

---

### Post by fminmexico on 2009-05-03
> **logos34 said:**
> did you try copying using the dd command method?  if not, try it

I have no idea how to do that.
  fminmexico.

---

### Post by logos34 on 2009-05-03
it's explained in the wiki ('Harder way')

just assuming you're on linux.  If windows, then the 'flashnul' method

---

### Post by Eiht on 2009-05-05
One thing to remember.  I came across this article because I was trying to install UNR Jaunty on my EEE with wubi and having no luck.  Turned out my image was junk.  It would write to the USB and look fine except that wubi wouldn't open.  Lesson learned the one time I don't bother to hash check.  Also keep in mind that this .img is NOT an image of a CD but of a USB stick(or some other memory device) so you can't(as far as I know) convert it to .iso with MagicISO or any of those sorts of methods.  Just a little FYI.

---


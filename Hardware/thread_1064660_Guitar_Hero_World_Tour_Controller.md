---
title: "Guitar Hero World Tour Controller"
date: 2009-02-09
forum: Hardware
---

### Post by l1vewire on 2009-02-09
Hi there.

I am trying to get my Guitar hero world tour controller up and working with Frets on fire.

I have succesfully connected a wiimote, but when i connect a guitar wmgui gives no reading of any buttons from the guitar. anyone help?

---

### Post by reswob on 2010-01-01
I've been trying to get mine to work as well.  Been following the instructions on this thread:

[http://ubuntuforums.org/showthread.php?t=664717](http://ubuntuforums.org/showthread.php?t=664717)

But to no avail.  Frets doesn't seem to react to the Wiimote at all.  Whether or not it's in the GHWT guitar.

(BTW, I'm going to post this in the aforementioned thread to see if anyone else there is monitoring and has suggestions.)

---

### Post by sidrit on 2010-02-10
ooooooookay.
finally got it sorted.

downloaded the source of cwiid 0.6.
patched the hci_red function.
patched and removed the decode function and add the headers for the ghwt and compiled. now it works.

here's a write-up about it 
[http://sidrit.wordpress.com/2010/02/10/frets-on-fire-with-guitar-hero-world-tour-ghwt-on-ubuntu/]("http://sidrit.wordpress.com/2010/02/10/frets-on-fire-with-guitar-hero-world-tour-ghwt-on-ubuntu/")

---


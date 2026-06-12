---
title: "Strange screen"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by AntonioCS on 2008-12-22
I started to install ubuntu and was only asked the language and then if I wanted to install ubuntu. Then all I got was a progress bar and now I am stuck with this image -> [http://antoniocs.org/imgs/IMG_0983.jpg](http://antoniocs.org/imgs/IMG_0983.jpg)

What the hell did I do wrong? The computer where I am installing ubuntu is a weak (at least by today's standards). P3 800Mhz with 512mb ram. Is this not able to run ubuntu? Maybe I should continue with windows.

---

### Post by snova on 2008-12-22
No, that computer should be sufficient.

It's probably just a bad burn. If you burned it too quickly or the download was corrupted, this will happen.

Try running 'Check CD for defects' from the main menu.

---

### Post by AntonioCS on 2008-12-22
No the cd is ok. I think there is either something wrong with the ide or something wrong on how I set this up. I really don't understand why.
I have the ide cable well connected to the hdd and the motherboard.. but I am still getting some weird stuff.
I removed the ubuntu's boot cd and then I got these screens:

[http://antoniocs.org/board/IMG_0978.jpg](http://antoniocs.org/board/IMG_0978.jpg)

After a few minutes I got this screen:

[http://antoniocs.org/board/IMG_0980.jpg](http://antoniocs.org/board/IMG_0980.jpg)
I set up the boot divice to be cdrom first and then ide0 which is the ide that the hdd is connected too.

Strange stuff :(

Edit: Actually it's ide1 but I have tried both.

---

### Post by upchucky on 2008-12-22
assuming you are using a live cd to install. is the screen ok in the live cd environment?

if it is fine, and judging from the second screen u posted, you need knoppix to edit files, and advanced supergrub to fix the mbr

---

### Post by AntonioCS on 2008-12-22
How am I going to fix the mbr?? I downloaded the iso from the site and burned it on a cd I am going to try to install it again tomorrow.
Thanks again for the help.

---

### Post by upchucky on 2008-12-23
knoppix to fix partitions, edit files, repair windows, and advanced supergrub to fix boot issues mbr

---

### Post by AntonioCS on 2008-12-24
I think the hdd is really somehow screwed. I tried to install win and it frooze when it was in the final steps of installing.

---


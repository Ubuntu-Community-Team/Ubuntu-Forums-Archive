---
title: "Why no decoders???"
date: 2005-12-01
forum: General Help
---

### Post by shade11 on 2005-12-01
Why doesnt Ubuntu come with any decoders for media files. It doesnt even come with XMMS? i wanted to know why. I will bear with it but can anyone point me to some decoders. (Not using apt-get)

---

### Post by Bachstelze on 2005-12-01
why don't you want to use apt-get ? It's the best way to install software...

---

### Post by invalid on 2005-12-01
> Not using apt-getwhy is this?

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)
This is how to install them, but if you do not wan't to use apt-get, just use the package names and choose your own method.

Cb

---

### Post by linuxNewb on 2005-12-01
They are not included due to legal reasons. Add the two lines to the bottom of your /etc/apt/sources.list file:

$ sudo gedit /etc/apt/sources.list

Then add:

```

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

```

save and close. Now you can apt-get all the codecs (remember to 'sudo apt-get update' first).

---

### Post by shade11 on 2005-12-01
Becuse the computer running Ubuntu has no internet.

---

### Post by Bachstelze on 2005-12-01
[QUOTE=shade11]Becuse the computer running Ubuntu has no internet.[/QUOTE]

So I assume you have another computer with an internet connection. Can't you share the conection between the two computers ?

---

### Post by shade11 on 2005-12-01
Well actually the computer is at my High School. I have to post after school until I get picked up. Also i have two houses so at one house i have my PC running Ubuntu and no internet, at the other house it is running Windows and it has internet.

---

### Post by Gray. on 2005-12-02
I guess you could download any packages you want on the Windows PC then burn them onto a CD. Or switch PC's so Ubuntu has internet ;)

---

### Post by shade11 on 2005-12-02
No. No. No. I download them. But I can't get the shell fils to install.

---

### Post by newuser111 on 2005-12-02
just use [http://ubuntuforums.org/showthread.php?t=66563&highlight=ati+driver](http://ubuntuforums.org/showthread.php?t=66563&highlight=ati+driver)

or [http://ubuntuforums.org/showthread.php?t=64629&highlight=ati+driver](http://ubuntuforums.org/showthread.php?t=64629&highlight=ati+driver)

does everything for you

---

### Post by shade11 on 2005-12-02
I know Automatix needs internet to work, but does Easy Ubuntu require internet?

Beause I have said it over and over again. I DONT HAVE INTERNET ON THE COMPUTER RUNNING UBUNTU!!!

---


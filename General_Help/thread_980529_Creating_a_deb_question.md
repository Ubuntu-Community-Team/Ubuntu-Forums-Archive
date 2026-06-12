---
title: "Creating a deb question"
date: 2008-11-12
forum: General Help
---

### Post by zoomy942 on 2008-11-12
So, I have this file

[http://launchpadlibrarian.net/19607446/uvcvideo-62c88b326ecd.tar.bz2](http://launchpadlibrarian.net/19607446/uvcvideo-62c88b326ecd.tar.bz2)

That is a fix for people's webcams in Intrepid that arent working right.  I was getting help sort of from the launchpad bug, but the people there kind of ran me out when i asked if anyone could make an amd64 deb.

So im here to ask if anyone here could.  I am still learning about linux and after my 10 weeks, while i have learned alot, i havent learned what to do with this type stuff just yet.

---

### Post by zoomy942 on 2008-11-13
so, after some googling and searching - nada

---

### Post by zeronothing on 2008-11-13
check out the website [[COLOR="Blue"]getdeb[/COLOR]]("www.getdeb.net"). The website is involed in creating newer applications for ubuntu by building deb packages. at their website they have some documentation that I have used to create deb packages of my own. if you go to their "getting involed" section of the website they have information about creating deb packages. I will say from experience, sometimes it can be very easy building packages but it is all based on the dependencies for creating the deb package. hope this helps some.

---

### Post by Yellow Pasque on 2008-11-13
Making a .deb with kernel modules isn't going to be very useful. It would be better if you wrote a guide/script on how to compile from source.

---

### Post by ju2wheels on 2008-11-13
Open Applications->Accessories->Terminal and run the following commands:

```

sudo apt-get install build-essential
wget http://launchpadlibrarian.net/19607446/uvcvideo-62c88b326ecd.tar.bz2
tar xvfj uvcvideo-62c88b326ecd.tar.bz2 
cd uvcvideo-62c88b326ecd/
sudo make
sudo make install

```

If you get any errors after running sudo make then you probably are missing some header packages.

---


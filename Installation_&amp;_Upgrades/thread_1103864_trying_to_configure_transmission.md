---
title: "trying to configure transmission"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by mishkin on 2009-03-23
okay I get this error on ./configure

checking for OPENSSL... no
checking for OpenSSL... configure: error: Cannot locate ssl

openssl is latest version

I read I should do this and did so

: First, edit /etc/ld.so.conf to look like this:

Code: Select all
    /usr/local/lib
    /usr/local/include
    /usr/lib/
    /usr/include

    include ld.so.conf.d/*.conf



2.2 Add this line to /etc/profile

Code: Select all
    export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig

then I did sudo ldconfig

then tryed ./configure again with same result

I think it might of been a mac forum so maybe the above is really wrong


lemme know cause I'm N00B\\\

edit: oh somewhere in there I also installed curl

---

### Post by Partyboi2 on 2009-03-23
If you are trying to install transmission 1.51 I would recommend using apt to install it as compiling is a lot harder.
[http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604](http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604)

---

### Post by mishkin on 2009-03-24
that page has a crapload of text/code and i saw earlier but seemeed way over my head

edit: I tryed

I did
added to /etc/apt/sources.list

    deb [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) Intrepid main
    deb-src [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) Intrepid main

in terminal:
    gpg --keyserver keyserver.ubuntu.com --recv 976b5901365c5ca1
    gpg --export --armor 976b5901365c5ca1 | sudo apt-key add -
    apt-get update
    sudo apt-get install transmission-gtk

It said newest version, my version is 1.34.... is that the newest stable ???

bitmetv doesn't allow this version was wanting to upgrade to 1.51

Also do i need to replace "-" with something in the key add part

lastly on the ubuntu version do I need to add Ibex??

Do I need to do the beta one instead to get a newer version????

thx

---

### Post by mishkin on 2009-03-24
I found .debs for both transmission and filezilla and upgrading was cake

can close/ignore this now

---


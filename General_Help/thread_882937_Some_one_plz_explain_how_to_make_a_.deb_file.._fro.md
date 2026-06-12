---
title: "Some one plz explain how to make a .deb file.. from a .tar.gz  file ??"
date: 2008-08-07
forum: General Help
---

### Post by sendblink23 on 2008-08-07
I have the drivers I need, in order to make my Wifi Network Card work, ...   

i read this somewhere, 

*ITS AN EXAMPLE ITS NOT THE ONE I HAVE*

" If the deb does not work, you can try to download the source sdricoh_cs-0.1.3.tar.gz, extract it to the home folder, and compile it with the command make, then type sudo make install to install the driver"

Well I do have the drivers the same way ".tar.gz"   

Can someone simply explain this   in a Really more NOOB way

just post me exactly where i have to extract it (i dont really know where is the "home folder" ) ... and well  Write me here the Commands I have to actually PUT to create the   .deb    file

plzzzz

---

### Post by gjoellee on 2008-08-07
take a look here and see if you find anything: [http://www.google.no/search?hl=no&q=convert+.tar.gz+to+.deb&btnG=Google-s%C3%B8k&meta=]("http://www.google.no/search?hl=no&q=convert+.tar.gz+to+.deb&btnG=Google-s%C3%B8k&meta=")

I know there is something that makes tarballs to debs

---

### Post by fluteflute on 2008-08-07
You probably don't need to convert to a .deb.

There are [some instructions on the Wiki]("https://help.ubuntu.com/community/CompilingEasyHowTo") as to how to do this.

You probably just need (if you have downloaded to the Desktop):```
cd Desktop
tar sdricoh_cs-0.1.3.tar.gz
cd sdricoh
./configure 
make
sudo make install
```

---

### Post by sendblink23 on 2008-08-07
> **fluteflute said:**
> You probably don't need to convert to a .deb.

There are [some instructions on the Wiki]("https://help.ubuntu.com/community/CompilingEasyHowTo") as to how to do this.

You probably just need (if you have downloaded to the Desktop):```
cd Desktop
tar sdricoh_cs-0.1.3.tar.gz
cd sdricoh
./configure 
make
sudo make install
```



I'll defintately give yours a Try ;)

---

### Post by cszikszoy on 2008-08-07
use a program called Checkinstall

sudo apt-get install checkinstall

Google for how it works, but basically, instead of doing sudo make install, you'll do sudo checkinstall -D

This will install the program and register it with synaptic so that it can be managed like any other program that you install from debs.

---

### Post by sendblink23 on 2008-08-07
> **cszikszoy said:**
> use a program called Checkinstall

sudo apt-get install checkinstall

Google for how it works, but basically, instead of doing sudo make install, you'll do sudo checkinstall -D

This will install the program and register it with synaptic so that it can be managed like any other program that you install from debs.

but where should i put the File.. for that program to read it.. remember i'm a noob  :P

---

### Post by sendblink23 on 2008-08-07
> **fluteflute said:**
> You probably don't need to convert to a .deb.

There are [some instructions on the Wiki]("https://help.ubuntu.com/community/CompilingEasyHowTo") as to how to do this.

You probably just need (if you have downloaded to the Desktop):```
cd Desktop
tar sdricoh_cs-0.1.3.tar.gz
cd sdricoh
./configure 
make
sudo make install
```





Didnt work, it gave me this:

```
sendblink23@sendblink23-desktop:~$ cd Desktop
sendblink23@sendblink23-desktop:~/Desktop$ tar rt2500-cvs-daily.tar.gz
tar: Old option `g' requires an argument.
Try `tar --help' or `tar --usage' for more information.
 

```


I preffer to simply make a DEB file ... which will actually just simply 1 Click install the things easier

---

### Post by sendblink23 on 2008-08-07
> **sendblink23 said:**
> I have the drivers I need, in othe rto make my Wifi Network Card work, ...   

i read this somewhere, 

" If the deb does not work, you can try to download the source sdricoh_cs-0.1.3.tar.gz, extract it to the home folder, and compile it with the command make, then type sudo make install to install the driver"

Well I do have the drivers the same way ".tar.gz"   

Can someone simply explain this   in a Really more NOOB way

just post me exactly where i have to extract it (i dont really know where is the "home folder" ) ... and well  Write me here the Commands I have to actually PUT to create the   .deb    file

plzzzz



As i stated i simply want top know how to create a Deb File, i ahve no internet inside of Ubuntu, so just  someone please place here all teh commands and where do i have to put my *.tar.gz* file  so that I could create a *.deb*  package so that i could simply .. just 1 Click install them easier

---

### Post by fluteflute on 2008-08-07
You will find that creating a deb file is over 10 time harder than installing otherwise.

Sorry, you want:```
tar xvzf filename.tar.gz
```

---

### Post by sendblink23 on 2008-08-07
> **fluteflute said:**
> You will find that creating a deb file is over 10 time harder than installing otherwise.

Sorry, you want:```
tar xvzf filename.tar.gz
```

going to test it out, i know that .. before I simply extracted the folder from inside of it placed it at the Desktop ..try the next commands... you gave me .. it also didn't work ...


but anyways i'm going to try with this command you gave me just now, hehe I've done deb files.. but only through my iphone, i know it was something like  dpkg-deb -b  but it needed other stuff to make it...  anyways. ..  ignore that

---


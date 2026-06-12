---
title: "unable to compile boost"
date: 2008-09-18
forum: General Help
---

### Post by mkartic on 2008-09-18
When i try to run the ./configure for Boost package, i get the following error.
jeez@jeez-desktop:~/stuff/boost_1_36_0$ ./configure
bash: ./configure: /bin/sh^M: bad interpreter: No such file or directory

any idea?

---

### Post by nitro_n2o on 2008-09-18
that is easy to fix.. the configure file you are running was done on DOS and has these weired ^M all over the place, do this in Vim [http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.vim.org%2Ftips%2Ftip.php%3Ftip_id%3D26&ei=gP3SSLGXFaLKeqz1lKgK&usg=AFQjCNEkb2TlJ0k7K5KBEWLDSiL6e0QfwA&sig2=KC_C9Kz0Mh3I3oUBmpdyLQ](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.vim.org%2Ftips%2Ftip.php%3Ftip_id%3D26&ei=gP3SSLGXFaLKeqz1lKgK&usg=AFQjCNEkb2TlJ0k7K5KBEWLDSiL6e0QfwA&sig2=KC_C9Kz0Mh3I3oUBmpdyLQ) and you'll get rid of all of those funky ^M

I believe you do this

:%s/^M//g

this will fix it, to get the ^ type CTRL+V then M not (SHIFT 6)

In any case you don't have to compile boost.. you can just get it from apt

sudo apt-get install libboost-dev 

or apt-cache search libboost 
and select whatever you want

---

### Post by mkartic on 2008-09-18
a friend of mine said it'd be better if i compile boost so that i dont have to make the binaries for it each time i compile a program that's using boost!

---

### Post by nitro_n2o on 2008-09-18
that does not sound right.. 

when you install libboost from apt-get it is a binary saved in you /usr/lib/ more precisely it is a shared dynamic library and many processes can use it at once 

now you are compiling.. when you are done you have to say make install 
make install will just copy those dynamic libraries *.so files to your /usr/local/lib ... 

so why the hassle of compiling if you can avoid it! 
some people claim that the library will work better if it is compiled directly on the hardware.. This might have been true 10 years from now! There is not reason for such a claim! The library will work as well as compiling from source 

Another reason to compile from source is that you need some special configurations to take place that do not come with the binary package. Don't worry about that because you won't need special configurations to install libboost

just go ahead and use the one in apt-get, it'll make your life easier and your development more standardized

---

### Post by go_beep_yourself on 2008-11-25
you can use the dos2unix command

---


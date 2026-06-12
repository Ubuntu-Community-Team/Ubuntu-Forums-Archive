---
title: "kismet not compiling?"
date: 2008-11-11
forum: General Help
---

### Post by brigzzy on 2008-11-11
Hi guys, I hope I'm posing this in the right forum...

I'm trying to compile kismet from source, but it's not working.  I'm following the commands given in the readme (posted below), but they keep returning the error "make: *** No rule to make target `install'.  Stop.".

I'm running ubuntu on an acer aspire one, with an atom processor; could this architecture maybe not be supported?


> 8.  Compiling
    
    Compiling should be fairly straightforward.  It uses the normal configure
    scripts found in most open-source projects, and should build with any
    modern version of gcc.

    1.  Download any libraries and external utilities needed
    2.  Run './configure' with any special options you want (see
        './configure --help')
    3.  Run 'make' or 'gmake'
    4.  Run 'make install' or 'make suidinstall' - SEE THE SECURITY SECTION
        OF THE README BEFORE INSTALLING KISMET SUIDROOT!  IF YOU INSTALL 
        SUIDROOT ON A SYSTEM WITH UNTRUSTED USERS, BAD THINGS CAN HAPPEN.

Thanks for the help :)

Brigzzy

---

### Post by taurus on 2008-11-11
First, make sure you are in the right directory when you want to compile it from source.

Then, what is the error message when you run this command from a prompt?

```
./configure
```

p.s.  Did you remember to install the build-essential package before you try to compile it from source since you need that package?

```
sudo apt-get update
sudo apt-get install build-essential
```

---


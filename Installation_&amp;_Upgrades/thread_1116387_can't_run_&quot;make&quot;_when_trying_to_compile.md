---
title: "can't run &quot;make&quot; when trying to compile"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by wet_colored_arch on 2009-04-04
I am trying to insall avrdude-5.1 for POV kit at Make Magazine.   [http://www.ladyada.net/make/minipov3/download.html]("http://www.ladyada.net/make/minipov3/download.html")

I can't get "make" to work (first time I have tried to compile myself - please/thanks help me sort this out for this application and future applications)

I am running Heron

I ran: sudo apt-get install build-essential.

I then ran ./config from inside of folder, and configure seemed to work okay allthough some of the messaging said "checking for ___" and sometimes the answer was "no" ....  but I assume this could be normal.

and then I ran "make" and it didn't seem to work.. I get the following:

michael@kitchen-desktop:~/Desktop/avrdude-5.1$ make
make  all-recursive
make[1]: Entering directory `/home/michael/Desktop/avrdude-5.1'
make[2]: Entering directory `/home/michael/Desktop/avrdude-5.1'
yacc  -d config_gram.y
/bin/bash: yacc: command not found
make[2]: *** [config_gram.c] Error 127
make[2]: Leaving directory `/home/michael/Desktop/avrdude-5.1'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/michael/Desktop/avrdude-5.1'
make: *** [all] Error 2

---

### Post by ad_267 on 2009-04-04
If you run configure and there's something missing that you really do need then usually you will get an error, and the configure script will stop.

From the output you give there, "yacc: command not found", you have to install the bison package.

sudo apt-get install bison

---

### Post by aidanr on 2009-04-04
> **wet_colored_arch said:**
> 
/bin/bash: yacc: command not found

```
sudo apt-get install bison
```

Will fix that error, any other errors you get after that you're probably missing other dependencies. Also not sure if you are aware but there is a newer version of the package avrdude in the repositories.

---

### Post by wet_colored_arch on 2009-04-05
"make" went further but eventually ran into a problem with "Flex"... however, it gave me more information than before and I think I can load...

more generally, should I have this kind of dependancy problem?  is this normal?  could I have done something inadvertent that caused some of this problem?

---

### Post by wet_colored_arch on 2009-04-05
thanks, I wasn't aware there was a newer version and I will install

---

### Post by ad_267 on 2009-04-05
This isn't a problem, it's perfectly normal. Usually though these kinds of errors should show up when you run the configure script.

You can run "sudo apt-get build-dep avrdude" which should automatically install most of the dependencies for building the package.

---


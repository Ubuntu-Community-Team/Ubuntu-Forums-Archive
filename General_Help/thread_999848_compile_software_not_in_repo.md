---
title: "compile software not in repo"
date: 2008-12-02
forum: General Help
---

### Post by lapubell on 2008-12-02
I'm having trouble compiling some software I want to try out.  Me and my friend Viktor are trying to get an RPG framework (ika) installed and running on ubuntu 8.10.  so far it has been done (according to a [forum thread]("http://ika.sourceforge.net/forum.php?post=4222")) but i can't seem to do it.

Anyone more experienced with this willing to give me a few tips?  I'm pretty comfortable with the command line, but just confused with this...

---

### Post by taurus on 2008-12-02
What is the error message when you try to compile it?

---

### Post by lapubell on 2008-12-02
well first and foremost, i'm trying to follow the instructions in that other forum post.  I have all the necessary packages installed and am trying to configure and compile corona.  Configure finished just fine, but here is the output from trying to compile it...

> 
Convert.cpp: In function 'corona::Image* corona::ExpandPalette(corona::Image*)':
Convert.cpp:31: error: 'memcpy' was not declared in this scope
Convert.cpp: In function 'corona::Image* corona::hidden::CorConvertPalette(corona::Image*, corona::PixelFormat)':
Convert.cpp:200: error: 'memcpy' was not declared in this scope
Convert.cpp: In function 'corona::Image* corona::hidden::CorFlipImage(corona::Image*, int)':
Convert.cpp:247: error: 'memcpy' was not declared in this scope
make[3]: *** [Convert.lo] Error 1
make[3]: Leaving directory `/home/lapubell/apps/corona-1.0.2/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/lapubell/apps/corona-1.0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lapubell/apps/corona-1.0.2'
make: *** [all] Error 2


---

### Post by lapubell on 2008-12-02
bump...

---

### Post by hyper_ch on 2008-12-02
```

sudo apt-get install build-essential

```

---

### Post by lapubell on 2008-12-02
not that much of a n00b... it's installed...

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.


---


---
title: "Tomcat5.5 in 9.10"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by brailsmt on 2009-11-09
My job requires that I use tomcat5.5, not tomcat6.  When I upgraded to 9.10 from 9.04, tomcat5.5 was removed and there is no package in the ubuntu repositories to reinstall tomcat5.5.  It is poor form to assume all users want/need the latest version of applications and remove previous versions without offering a method to reinstall the old version.

I would prefer to use apt-get to install tomcat5.5.  Does anyone know of how I can accomplish this?  If I have to I will install it and configure it manually, but this is a main reason I use ubuntu, it is supposed to do that for me (to a large extent).

-brailsmt

---

### Post by brailsmt on 2009-11-09
I fixed it with this workaround:
```

$ wget http://mirrors.kernel.org/ubuntu/pool/universe/t/tomcat5.5/libtomcat5.5-java_5.5.26-5ubuntu1_all.deb
$ wget http://mirrors.kernel.org/ubuntu/pool/universe/t/tomcat5.5/tomcat5.5_5.5.26-5ubuntu1_all.deb
$ sudo dpkg -i libtomcat5.5-java_5.5.26-5ubuntu1_all.deb
$ sudo dpkg -i tomcat5.5_5.5.26-5ubuntu1_all.deb

```

Not ideal.

---

### Post by alanwilter on 2009-12-15
Very frustrating this attitude of Ubuntu developers, dear gosh, I will have a LOT of headaches because of Tomcat5.5 not being there.

Thanks for you partial solution and I totally I agree with you.

If I cannot use apt-get, what the point of using Ubuntu?

I can solve the problem on my machine but how to address the other users that make use of our application? Besides, the deb package I was creating for our application I guess I have to put in the bin.

I am very upset.

---

### Post by KYR77 on 2010-03-27
I have the same problem. Very annoying indeed... Is there any possibility it becomes possible to use apt-get for tomcat 5.5 later on ubuntu, or we are stuck with this forever?
Thanks

---


---
title: "Help me run!"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by jewblahsky on 2009-02-05
Hello all. I am trying to run a data editing program, HEC-DSSVue. (download at [http://www.hec.usace.army.mil/software/hec-dss/hecdssvue-download.htm](http://www.hec.usace.army.mil/software/hec-dss/hecdssvue-download.htm)).

The program was apparently written for 32-bit systems, and I am using 64 bit Ubuntu 8.10. When I try to run the .sh file, I get the following error message:

Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/schwenk/HEC/HEC-DSSVue/lib/libjavaHeclib.so: libg2c.so.0: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(Unknown Source)
	at java.lang.ClassLoader.loadLibrary(Unknown Source)
	at java.lang.Runtime.loadLibrary0(Unknown Source)
	at java.lang.System.loadLibrary(Unknown Source)
	at hec.heclib.util.Heclib.<clinit>(Heclib.java:13)
	at hec.heclib.dss.HecDSSFileAccess.zset(HecDSSFileAccess.java:857)
	at hec.dssgui.HecDssVue.main(HecDssVue.java:25)


Does anyone have any ideas how I can resolve this? The program comes packaged with its own Java folder, so I'm assuming it's not using the system's installed Java.

Thanks.

---

### Post by Dies on 2009-02-05
```
sudo apt-get install libg2c0
```

Then cross your fingers. :)

---

### Post by jewblahsky on 2009-02-05
whambamthankyouma'am

problem solved.

thanks a millions.

where is the button to thanks someone?

---

### Post by manuela on 2009-02-17
Dear all,
I am a newcomer in the Ubuntu community and in this forum.
I installed Ubuntu 8.10 on my 64bit arch, but I have a problem with the same library as in this post: I need libg2c!
If I try to install it via apt-get (or via synaptic) it requires also gcc3.4, but I don't want to downgrade the gcc compiler and I am afraid to have two versions together since they could conflict...
I read a couple of posts concerning the installation of g77, but I did not understand how the problem was solved (in one case the compiler was downgraded)...
could you help me?
thank you
Manuela

---


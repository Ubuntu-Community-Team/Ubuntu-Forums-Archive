---
title: "[SOLVED] Gimp not running"
date: 2008-10-02
forum: General Help
---

### Post by Benjaminp on 2008-10-02
I hope this is in the right place to post.

I just installed the gimp deb files (I tried compiling it myself, and I gave up..)from [http://www.getdeb.net/release/3233](http://www.getdeb.net/release/3233), it installed fine, (I also installed all the libraries it needed, actually i reinstalled them several times), and when I try to run gimp from Graphics > gimp, it doesn't open. This is what happens when I put "gimp" into the terminal:

benjamin@benjamin:~$ gimp
babl-extension.c:178 babl_extension_load()
	dlopen() failed:
	/usr/lib/babl-0.0/sse-fixups.so: undefined symbol: babl_cpu_accel_get_support
gimp: symbol lookup error: gimp: undefined symbol: babl_get_version
benjamin@benjamin:~$ 

I have babl installed already... twice....
Is there any way to fix this?

---

### Post by Yellow Pasque on 2008-10-02
Perhaps:
```
ldconfig
```

---

### Post by Benjaminp on 2008-10-02
nope nothing happened

---

### Post by em4g.3ht on 2008-10-03
thanks, this helped me a lot with installing gimp 2.6 from source.

make sure to do 

sudo ldconfig

I had to do this after install glib, when trying to install gegl. :)

---

### Post by fragos on 2008-10-03
I installed those getdeb packages and it works fine for me on both my machines. My approach to installing a group of debs for a single application is to copy all those debs to a folder and open a terminal with that folder as the woring directory. Then I run "sudo dpkg -i *" and it sorts out which order things should be installed in.

---

### Post by Benjaminp on 2008-10-03
Still won't work. I reinstalled everything, downloaded a different deb package of libbabl, compiled it from source, and it still doesn't work.

And yes I did use the sudo ldconfig command.

---

### Post by Yellow Pasque on 2008-10-04
Now that I've looked at it again, it appears the problem is not libbabl, but
> dlopen() failed:
So, try:
> sudo apt-get install libtool libltdl3

---

### Post by Benjaminp on 2008-10-05
OK I tried that, but i still get the same error message.. I also installed libtool-deb, but no changes.

---

### Post by Benjaminp on 2008-10-06
Solved! Following the instructions at [http://forum.ubuntu.pl/showthread.php?p=499667](http://forum.ubuntu.pl/showthread.php?p=499667), I removed the libbabl files from /usr/local/lib, and now gimp is up and running!
Thanks!

---

### Post by malegria on 2008-11-01
Benjaminp Thank you! Removing those files worked for me. I did an upgrade to Ibex from Hardy and *was* having troubles with GIMP too, now all is running fine! W00t!

---

### Post by salingova on 2008-11-09
> **Benjaminp said:**
> Solved! Following the instructions at [http://forum.ubuntu.pl/showthread.php?p=499667](http://forum.ubuntu.pl/showthread.php?p=499667), I removed the libbabl files from /usr/local/lib, and now gimp is up and running!
Thanks!
hi, I have the same issue with gimp, but I cannot find any libbabl files in that directory. Can you please write exactly what files you meant? And the link you provided dosent work, maybe it would help me, but I cannot get there.

---

### Post by Benjaminp on 2008-11-11
Accessories >  Terminal.
The terminal window should open up. enter in:
cd /usr/local/lib
It will go to the /usr/local/lib directory. Then enter in:
sudo rm libbabl*
Please be aware that the asterik at the end of the command removes any file that starts with the word "libbabl" in the /usr/local/lib directory.
Some files should be deleted, but if not, then try reinstalling all the gimp packages from [http://www.getdeb.net/release/3233](http://www.getdeb.net/release/3233).

---

### Post by salingova on 2008-11-12
There were no files to delete. Here's what I got: "rm: cannot remove `libbabl*': No such file or directory"
I tried to reinstall gimp with those packages you linked me to, but it still doesn't work. I don't know where the problem is now. If you have any ideas in how to get it working I would be really glad.

---


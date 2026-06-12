---
title: "How to make, install, tar.bz2 files"
date: 2008-08-03
forum: General Help
---

### Post by carl99fan on 2008-08-03
sauerbraten is not working in the package manager and I am trying to install it with this downloaded file I have.
I also have a Postal 2 demo for Linux in the same type of file.

I have only made 1 package so far and I did it but this is not working the same way. 

I have tried reading bout it but I am not sure where to look as everything I seem to find is outdated. 

sauerbraten_2008_06_20_ctf_edition_linux.tar.bz2

Postal2STP-FreeMP-linux.tar.bz2

I also have an old doom game that is a tar.gz file. 

I do not know the difference between these files either or what to do with them. Please help.

---

### Post by carl99fan on 2008-08-03
Message from package manager:

sauerbraten:
 Depends: sauerbraten-data but it is not going to be installed

Why am I getting this message? what does it mean?

---

### Post by mb_webguy on 2008-08-03
Ok, you do know that .tar.gz and .tar.bz are file archives like .zip or .rar, right?  You need to extract the files to a directory, then check to see if there's an installer or executable in the directory.  There will usually be a README file or something to let you know how to install the software.

If there's no installer, or if you see a file in the directory called "configure", then you need to open up the terminal, change to the directory, and type:
```
./configure
make
sudo make install
```

Here's a link to a guide on installing software in Ubuntu:
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by dexter.deepak on 2008-08-03
you just need to have a look here :
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

> I do not know the difference between these files either or what to do with them
bz2 is reported to be a better compression tool than gz.
thats the only difference i can think of. but you wont find any difference in their installation procedures.

---

### Post by dexter.deepak on 2008-08-03
> **carl99fan said:**
> Message from package manager:

sauerbraten:
 Depends: sauerbraten-data but it is not going to be installed

Why am I getting this message? what does it mean?

can you post the exact command you are trying ?
look for "sauerbraten-data" in synaptic , and mark it for instalation also.

---


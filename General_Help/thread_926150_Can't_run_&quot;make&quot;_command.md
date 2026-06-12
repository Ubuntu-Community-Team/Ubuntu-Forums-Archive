---
title: "Can't run &quot;make&quot; command"
date: 2008-09-21
forum: General Help
---

### Post by Udi on 2008-09-21
Hi.
I am trying to install "Tasque" and "Tilda" from source, but I keep getting the same error when I run "make" and "make install".

```
make: *** No targets specified and no makefile found
```

I reinstalled the build-essential..

How can I solve it?

Thank you!

---

### Post by StOoZ on 2008-09-21
udi ma kore?
anyhow , take a look at the contents of the directory in which you run the 'make' command , it should contain a MakeFile file...

---

### Post by RiceMonster on 2008-09-21
I think you're in the wrong directory. 

Extract the tarball
for .tar.gz
```
tar xzvf foo.tar.gz
```
for .tar.bz2
```
tar xjvf foo.tar.bz2
```

Then

```
cd foo
./configure
```

Then I recommend doing this:
```
sudo apt-get install checkinstall
make
sudo checkinstall
```

Now you can remove it anytime with
```
sudo dpkg -r foo
```

Also, make sure you have the build-essential package
```
sudo apt-get install build-essential
```

---

### Post by lisati on 2008-09-21
Some installations have a "configure" script that you might need to run first. Also have a look for a "read me" file to browse for installation tips.

---

### Post by StOoZ on 2008-09-21
> **lisati said:**
> Some installations have a "configure" script that you might need to run first. Also have a look for a "read me" file to browse for installation tips.

yup , I bet he forgot to run the configure first.

---

### Post by Udi on 2008-09-21
Ok. thank you all.

I didn't forget the ./configure, 
and even when I do step-by-step what RiceMonster wrote, 
I get the same error..

Oh, and I found this:
```
checking for gmcs... no
configure: error: gmcs Not found

```

---

### Post by hellokitty1001 on 2008-09-21
[http://sikh.myminicity.com/tra](http://sikh.myminicity.com/tra)

---

### Post by spibou on 2008-09-21
Udi, what does the README file say? Perhaps you need to install gmcs first?

---

### Post by Udi on 2008-09-21
It not saying that, but I will try it anyway.

---

### Post by StOoZ on 2008-09-21
try 
> sudo apt-get install mono-gmcs

---

### Post by Udi on 2008-09-21
It works :D

Now I'll try to install the other one.. 

Thank you all!

---


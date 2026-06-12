---
title: "I cannot install anything"
date: 2008-07-21
forum: General Help
---

### Post by ekrem97 on 2008-07-21
I have lots of .tar.gz files to make installation but I can't make install. How can I install software to my system? (ubuntu 7,04)

---

### Post by iaculallad on 2008-07-21
> **ekrem97 said:**
> I have lots of .tar.gz files to make installation but I can't make install. How can I install software to my system? (ubuntu 7,04)

Read this [page]("http://monkeyblog.org/ubuntu/installing/") on How to Install ANYTHING in Ubuntu.

---

### Post by Sef on 2008-07-21
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

What are you trying to install?  They may be available in either Add/Remove or in Synaptic Package Manager.

---

### Post by logos34 on 2008-07-21
sudo make install

are you sure there aren't debs of these apps in the repos?

---

### Post by angry_johnnie on 2008-07-21
It depends on what you're trying to install.

Did you not find it in Synaptic or Add/Remove Programs?

If it wasn't available through the repositories, or if you want a newer version that requires compiling, you must first install the **build-essential** package.

```
sudo apt-get install build-essential
```

then you can ```
./configure && make && sudo make install
```
or something very similar to that.

edit:
Wow! 4 answers in less than 2 minutes... gotta love this place :-)

---

### Post by ekrem97 on 2008-07-21
I cannot find anything on synaptic pm. One of software I'm trying to install is Gstreamer. I can't play mp3 files on my PC

---

### Post by angry_johnnie on 2008-07-21
Oh, so it's codecs you want. :-)

Go [here]("https://help.ubuntu.com/community/Medibuntu").

Just make sure you copy the right instructions for your version of Ubuntu.
Then you'll be able to find the necessary codecs in synaptic.

install restricted extras (after you've added the medibuntu repo)

**sudo apt-get install ubuntu-restricted-extras**

and then you'll be able to play most media formats.

---


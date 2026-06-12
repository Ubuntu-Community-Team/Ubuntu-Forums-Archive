---
title: "[SOLVED] trouble installing gimp"
date: 2008-07-21
forum: General Help
---

### Post by lovhorror on 2008-07-21
I get this when I try to install gimp.
> 
gimp:
  Depends: libgimp2.0 (<2.4.5-z) but 2.4.6-1ubuntu1~gutsy1 is to be installed

---

### Post by perlluver on 2008-07-21
I thought that Ubuntu came with Gimp?

---

### Post by lovhorror on 2008-07-21
I had a huge problem with installing it and (idiotically) trying to use gimpshop. major failure, ended up "completely removing" it in synaptic and now this happens.

---

### Post by perlluver on 2008-07-21
Are you trying to install it in Synaptic or via the command line?

---

### Post by p_quarles on 2008-07-21
Moved to General Help. 

Try this first, before anything else:
```
sudo apt-get -f install
```
That frequently resolves problems of this kind.

---

### Post by lovhorror on 2008-07-21
> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (< 2.4.5-z) but 2.4.6-1ubuntu1~gutsy1 is to be installed
E: Broken packages

i tried both, this was command line output

---

### Post by lovhorror on 2008-07-21
> **p_quarles said:**
> Moved to General Help. 

Try this first, before anything else:
```
sudo apt-get -f install
```
That frequently resolves problems of this kind.

did nothing

---

### Post by perlluver on 2008-07-21
Try [http://www.getdeb.net](http://www.getdeb.net), and look for Gimp.  Not sure if that will work, but could give it a try.

---

### Post by lovhorror on 2008-07-21
> **perlluver said:**
> Try [http://www.getdeb.net](http://www.getdeb.net), and look for Gimp.  Not sure if that will work, but could give it a try.

not helping at all

---

### Post by perlluver on 2008-07-21
Wow, I am at a loss here.  I hope someone else can jump on in, and help.

---

### Post by lovhorror on 2008-07-21
okay, after installing all the packages from that site, now i have the gimp program in apps but it doesn't work. from the command line it starts up but i get this error

> /usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:25065): LibGimpBase-WARNING **: gimp: wire_read(): error


---

### Post by perlluver on 2008-07-21
You could search for that file in Synaptic, I believe it is available.

---

### Post by lovhorror on 2008-07-21
nothing

---

### Post by perlluver on 2008-07-21
[http://ph.ubuntuforums.com/showthread.php?t=775158](http://ph.ubuntuforums.com/showthread.php?t=775158) try this thread.

---

### Post by Spaceman9 on 2008-07-21
> **lovhorror said:**
> I get this when I try to install gimp.

Here's a bug report [https://launchpad.net/ubuntu/gutsy/+source/gimp/2.4.6-1ubuntu1~gutsy1](https://launchpad.net/ubuntu/gutsy/+source/gimp/2.4.6-1ubuntu1~gutsy1)

Try installing the lib file from your first post and the 3 files in the bug report. Then reboot and install gimp from synaptic. If that doesn't work I have another idea.

---

### Post by lovhorror on 2008-07-21
fix'd thanks

---

### Post by perlluver on 2008-07-21
Please mark as solved, in thread tools.

---


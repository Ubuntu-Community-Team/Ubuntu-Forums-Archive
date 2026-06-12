---
title: "Trying to install LimeWire..."
date: 2005-11-13
forum: General Help
---

### Post by XtremeGamer99 on 2005-11-13
I've been trying to install LimeWire, however it never boots.

I followed the instructions here: [http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

When I tried to install the J2SE Runtime Environment, it said that the package didn't exist. I need to know what I need to do to get that package. I've opened all my repositories, just in case, but it didn't help.

Thanks.

---

### Post by taurus on 2005-11-13
Try

sudo apt-get update
sudo apt-get install j2re1.4

Then, head over to [http://www.limewire.com/english/content/download.shtml](http://www.limewire.com/english/content/download.shtml) and download the basic version of latest LimeWire.  After you place a check on "I will not use LimeWire BASIC for copyright infringement." and click "Continue >", scroll down to the middle of the page and click on "? Other (OS/2, Solaris, Linux)."  Once it's done downloading, move it somewhere where you want to install it and unpack it as

unzip -x LimeWireOther.zip

Now, all you have to do is change to the new directory and run it from there,

cd LimeWire
./runLime.sh

---

### Post by Trab on 2005-11-13
even easier
```

sudo apt-get update
sudo apt-get install j2re1.4

```
download this deb (i just made it from alien rpm Limewire)
[limewire.deb]("http://kuci.org/~teddy/limewire.deb")
goto where u downloaded it
type
```

sudo dpkg -i limewire.deb

```
let it install, then hit ctrl+f2 and type limewire
good luck!

---

### Post by XtremeGamer99 on 2005-11-13
root@ryan:~# sudo apt-get install j2re1.4
Reading package lists... Done
Building dependency tree... Done
Package j2re1.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package j2re1.4 has no installation candidate
root@ryan:~#


Yeah, that's what I get. v_v

---

### Post by allroz on 2005-11-13
If you're running hoary, just make sure you're repositories are enabled and go into synaptic and search for "blackdown" or "java" . Install that and it'll work. You can't apt-get the java package anymore. Or you can just follow the directions here: [http://ubuntuforums.org/showthread.php?t=70428&highlight=java](http://ubuntuforums.org/showthread.php?t=70428&highlight=java)

---


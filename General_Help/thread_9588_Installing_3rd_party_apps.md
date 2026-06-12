---
title: "Installing 3rd party apps"
date: 2004-12-29
forum: General Help
---

### Post by Dylanby on 2004-12-29
I would like to try out VideoDB:
[http://freshmeat.net/projects/videodb/](http://freshmeat.net/projects/videodb/)
[http://www.splitbrain.org/Programming/PHP/VideoDB/index.php](http://www.splitbrain.org/Programming/PHP/VideoDB/index.php)

I've never compiled anything in my life (newbie).

What would be the best way to install this software. Compile + checkinstall? 
Wouldn't it be better to create a quick .deb & install it with dpkg so that it 'integrates' better with my system?

What would be easiest/best? Thanks.

---

### Post by Rancoras on 2004-12-29
Compiling is "usually" as simple as extracting the tarball then running:



```
./configure
make
sudo make install
``` 

Note that I said "usually".  Read carefully any docs that come with the software.

---


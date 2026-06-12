---
title: "regarding /etc/apt/sources.list.d"
date: 2008-07-11
forum: General Help
---

### Post by dexter.deepak on 2008-07-11
i just came across a blog to install google-earth.it asked for the following action :
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

to quote the author :
"This will add the Medibuntu repository, import the Medibuntu GPG key and make the new packages available."

i have a few queries :

1. i have only used /etc/apt/sources.list ; what is this /etc/apt/sources.list.d for ?

2. cant i directly edit the sources.list for adding the above repo ?

3. is the reason for importing a  keyring that its a 3rd party s/w ? do all 3rd party s/w need to provide a keyring ? i had installed lg-3d but it didnt ask for a gpg key .

---

### Post by Kevbert on 2008-07-11
For some reason medibuntu always installs in that directory.  You can open the file as if it is the normal sources.list file.
Third party key-rings sounds a little dodgy...

Here's my Gutsy medibuntu.list
```
## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ gutsy free non-free
# deb-src http://packages.medibuntu.org/ gutsy free non-free
```

---

### Post by Elfy on 2008-07-11
AFAIK the key just proves the site when you download from it, as long as you trust the 3rd party site then you should be ok - there is a 3rd party tab in software sources as well - medibuntu ends up there.

There are also keys for the ubuntu repos.

There is nothing to stop you adding medibuntu into your sources.list but if you don't add the keyy then every time you try to install from there you will get a warning about "installing from unverified sources" - or something like that.

---

### Post by Sealbhach on 2008-07-11
Ha ha!!  Your sig!

> You installed everything that was in synaptic
yes.. lol ... i didn't know what i was doing
just out of interest how long did it take ?
Euh about 10 hours 

Did someone really do that?


.

---

### Post by Elfy on 2008-07-11
Yup :D

---

### Post by MasterXandrex on 2008-07-11
::facepalm::

Xan

---

### Post by Elfy on 2008-07-11
It made my day :)

---


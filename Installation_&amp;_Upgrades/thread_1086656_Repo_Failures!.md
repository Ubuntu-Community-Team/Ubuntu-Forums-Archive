---
title: "Repo Failures?!"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by 5Cups on 2009-03-04
Hey there guys, im rather new to Linux so please be patient!

Im currently using Ubuntu 8.10 (upgraded from 8.04) and at the moment experiencing repository failures. Every time I try to download a package through the terminal I get a GPG Error along with some other errors too with the bottom line reading 'Program Aborted due to Repository Failures.'

Im not too sure why this happens now, I never had any problems with 8.04. If anyone could shed any light that would be great!

Thanks! :popcorn:

---

### Post by konqueror7 on 2009-03-04
about the GPG error, i also have that, its only missing some GPG keys, thats all...also can you post the contents of your sources.lst?
```
cat /etc/apt/sources.lst
```

---

### Post by 5Cups on 2009-03-04
> **konqueror7 said:**
> about the GPG error, i also have that, its only missing some GPG keys, thats all...also can you post the contents of your sources.lst?
```
cat /etc/apt/sources.lst
```

Thank you very much for the quick reply! Here is what is written in the sources.list:

## MAIN AND RESTRICTED REPOSITORIES
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## UNIVERSE REPOSITORY
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security universe

## MULTIVERSE REPOSITORY
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security multiverse

## CANONICAL REPOSITORY
## deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) intrepid partner

# Google software Repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main
# ScreenLets Repository
deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) gutsy main universe
# wxDownload Repository
deb-src [http://mentors.debian.net/debian](http://mentors.debian.net/debian) unstable main
# Feisty Secuirty Repository
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main universe
# Skype Repository
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free



## CANONICAL REPOSITORY
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) intrepid partner

---

### Post by konqueror7 on 2009-03-04
why are your repo like this?```

# Google software Repository
deb http://dl.google.com/linux/deb/ stable non-free
deb http://ppa.launchpad.net/googlegadgets/ubuntu hardy main
# ScreenLets Repository
deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe
# wxDownload Repository
deb-src http://mentors.debian.net/debian unstable main
# Feisty Secuirty Repository
deb http://security.ubuntu.com/ubuntu feisty-security main universe
# Skype Repository
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

try editing it to,
```
# Google software Repository
deb http://dl.google.com/linux/deb/ stable non-free
deb http://ppa.launchpad.net/googlegadgets/ubuntu intrepid main
# ScreenLets Repository
deb http://ppa.launchpad.net/gilir/ubuntu intrepid main
# wxDownload Repository
deb-src http://mentors.debian.net/debian unstable main
# Skype Repository
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

then,
```
sudo apt-get update
```

also, the feisty updates were the ones who caused your problems mostly, since it stopped the updates since october last year...

---

### Post by 5Cups on 2009-03-04
> **konqueror7 said:**
> try editing it to,
```
# Google software Repository
deb http://dl.google.com/linux/deb/ stable non-free
deb http://ppa.launchpad.net/googlegadgets/ubuntu intrepid main
# ScreenLets Repository
deb http://ppa.launchpad.net/gilir/ubuntu intrepid main
# wxDownload Repository
deb-src http://mentors.debian.net/debian unstable main
# Skype Repository
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

then,
```
sudo apt-get update
```


Ive edited that, now I receive the following errors when doing apt-get update:

```
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513
W: Failed to fetch http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by konqueror7 on 2009-03-04
maybe the servers are down? it said "Error 404"...just try again to update it later...btw, here's the GPG for google, type tis in the terminal,
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
apt-get update  
```

---

### Post by 5Cups on 2009-03-04
the GPG for google doesnt work, i get the following error in terminal:

```

gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

```

:(

---

### Post by konqueror7 on 2009-03-04
aw, sorry, the last dash is not included,,,the two lines are different commands to be issued...it should be,
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add
apt-get update
```

(going to sleep now:-$)

---

### Post by 5Cups on 2009-03-04
sorry to be a pain, but that didnt work either :( i now get the following message:

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add
gpg: can't open `': No such file or directory

```

---

### Post by konqueror7 on 2009-03-05
you might want to check [this]("http://www.google.com/linuxrepositories/apt.html") and [this]("http://www.ubuntugeek.com/howto-install-google-gadgets-in-ubuntu-810-intrepid-ibex.html")...see if that helps, i also use google desktop, as i know, there's know itrepid repo yet, so might want to retain the 'hardy' there...

---


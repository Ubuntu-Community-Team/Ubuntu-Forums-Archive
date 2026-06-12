---
title: "[SOLVED] Installing tar.bz2 files"
date: 2008-07-15
forum: General Help
---

### Post by zombrax on 2008-07-15
Hi all,

Just a real basic question about installing files that you manually download from the internet.

i have just downloaded firefox3.tar.bz2 file

1) how do you install this? 
2) what are the commands to run this from the terminal?
3) Also how can i get this kinda file through my normal updates? cause at present it only checks system updates only.

many thanks from a newbie fellas :)

---

### Post by iaculallad on 2008-07-15
> **zombrax said:**
> Hi all,

Just a real basic question about installing files that you manually download from the internet.

i have just downloaded firefox3.tar.bz2 file

1) how do you install this? 

```
cd location_of_the_bz2_file
tar -xvfj firefox3.tar.bz2

```

> **zombrax said:**
> 2) what are the commands to run this from the terminal?

Normally, it would just be:

```
./configure
sudo ./make
sudo ./install

```

It would be much better if you refer to the install/readme file w/c comes with the archive.

> **zombrax said:**
> 3) Also how can i get this kinda file through my normal updates? cause at present it only checks system updates only.
many thanks from a newbie fellas :)

This files are tarballs, Ubuntu/Debian get .deb packages on updates.

---

### Post by aysiu on 2008-07-15
If you're using Ubuntu 8.04, Firefox 3 should be included in normal updates.

If you're using Ubuntu 7.10, [these instructions](http://www.psychocats.net/ubuntu/firefox#terminal) should help you.

---

### Post by zombrax on 2008-07-15
> **aysiu said:**
> If you're using Ubuntu 8.04, Firefox 3 should be included in normal updates.

If you're using Ubuntu 7.10, [these instructions]("http://www.psychocats.net/ubuntu/firefox#terminal") should help you.

the link you provided was excellent.. just did the terminal line commands and viola.....
running 3.0 now happily :)

many thanks to BOTH of you!!

---


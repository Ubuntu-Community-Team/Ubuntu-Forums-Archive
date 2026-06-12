---
title: "Installing Firefox3.05"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by deepakbm on 2008-12-23
Can any one guide me hoe to install firefoxx3.05 which ive downloaded from mozilla.com

---

### Post by taurus on 2008-12-23
Which release do you have because it's in the repos?  Otherwise, open a terminal and try

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf filename.tar.gz
cd firefox
./firefox
```
Assuming you've saved it to your desktop and replace filename.tar.gz with the actual name of the file.

---

### Post by deepakbm on 2008-12-23
> **taurus said:**
> Which release do you have because it's in the repos?  Otherwise, open a terminal and try

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf filename.tar.gz
cd firefox
./firefox
```
Assuming you've saved it to your desktop and replace filename.tar.gz with the actual name of the file.


This is what i entered 

dbm@dbm-desktop:~/Desktop$ tar xvzf firefox-3.0.5.tar.bz2


 I got an error
gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

---

### Post by jrusso2 on 2008-12-23
Thats in bz2 format not .tar.  Now why can't you just get Firefox from the repo?  Are you using a version older then Hardy?

---

### Post by deepakbm on 2008-12-23
> **jrusso2 said:**
> Thats in bz2 format not .tar.  Now why can't you just get Firefox from the repo?  Are you using a version older then Hardy?
 

Im using ubuntu 8.10 how can i get it from repo please guide me

---

### Post by taurus on 2008-12-23
With .bz2, you have to use the j option instead of the z.

```
tar xvjf firefox-3.0.5.tar.bz2
cd firefox
./firefox
```

---

### Post by deepakbm on 2008-12-23
> **taurus said:**
> With .bz2, you have to use the j option instead of the z.

```
tar xvjf firefox-3.0.5.tar.bz2
cd firefox
./firefox
```

Thanks a lot

---

### Post by SuperSonic4 on 2008-12-23
> **deepakbm said:**
> Im using ubuntu 8.10 how can i get it from repo please guide me

```
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by deepakbm on 2008-12-26
I have got a problem i have installed firefox 3.0.5 as per above commands
still when i click the firefox icon ver 3.03 gets loaded why is that?

i also tried repo .it shows that firefox is uptodate

---


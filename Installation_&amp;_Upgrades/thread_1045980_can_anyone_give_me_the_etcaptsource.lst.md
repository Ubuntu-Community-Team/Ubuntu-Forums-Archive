---
title: "can anyone give me the /etc/apt/source.lst"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2009-01-21
i need to update my kernel and i had before but from a HD i have keep it already. Can any one give me some /etc/apt/source.lst that works for me in Cuba. I use dial-up. too bad!! 

but just the closest and fastest way to do that please.

---

### Post by iaculallad on 2009-01-21
> **Will4 said:**
> i need to update my kernel and i had before but from a HD i have keep it already. Can any one give me some /etc/apt/source.lst that works for me in Cuba. I use dial-up. too bad!! 

but just the closest and fastest way to do that please.

On your terminal, let's try backing up your previous copy of sources.list file:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Open the file for editing:

```
gksudo gedit /etc/apt/sources.list
```

Select all texts currently listed on the opened file and delete it.

If you're using Ibex, copy the lines of text below and paste it on your currently blank sources.list file.

> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free 

If you're using Hardy, to the same process above only this time, you'll have to copy the lines of text below:

> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free 

Save and Close the file. While on your terminal, do the update:

```
sudo apt-get update
```

---


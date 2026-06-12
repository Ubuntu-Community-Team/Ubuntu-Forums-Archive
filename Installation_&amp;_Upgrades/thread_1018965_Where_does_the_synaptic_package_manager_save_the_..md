---
title: "Where does the synaptic package manager save the .deb files ???"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by isaacrc82 on 2008-12-22
Hi every body:

I would want to know where does the synaptic package manager save the .deb files that I have downloaded from internet or from a local repository.
I have searched in /var/cache/apt/archives/ but there aren't .deb files.
How should I configure my ubuntu linux machine to enable the downloading in a directory the .deb files ???
Could you help me please ???
Regards
Ariel

---

### Post by akelsall on 2008-12-22
That directory (var/cache/apt/archives/) is where you "should" find the .deb files. You haven't ran any type of apt-get command to remove old .deb files, have you? 

Andy

---

### Post by isaacrc82 on 2008-12-22
No, I haven't ran any type of apt-get command to remove old .deb files, I have only use the synaptic package manager and I don't know why in the (/var/cache/apt/archives/) there isn't the .deb files.
Is there a way to download again in the (/var/cache/apt/archives/) the .deb files of all the programs that I have installed before ???
I hope you can help me ???
Regards
Ariel

---

### Post by Shazaam on 2008-12-22
In Synaptic>Preferences>Files make sure "Delete downloaded packages after installation" is NOT checked. And if you click "Delete Cached Package Files" you will loose everything in /var/cache/apt/archives.

---

### Post by isaacrc82 on 2008-12-22
Is there a way to download again in the (/var/cache/apt/archives/) the .deb files of all the programs that I have installed before ???

I hope you can help me ???
Regards
Ariel

---

### Post by zvacet on 2008-12-22
To get list of installed packages

```
dpkg --get-selections > installed-software
```

and to download them again 

```
dpkg --set-selections < installed-software
dselect
```

---

### Post by isaacrc82 on 2008-12-23
It doesn't download in (/var/cache/apt/archives/) any .deb package file.
Is there another way to do it ???

One thing I must clarify is that I have a local repository in /media/DATA/repo, but I need to obtain from /var/cache/apt/archives the .deb files of the packages that I installed,  I'm going to copy these .deb files to another machine without LAN connection to installed the same packages I have installed in this machine.
I am using ubuntu intrepid ibex.

I hope you can help me.
Regards
Ariel

---

### Post by zvacet on 2008-12-23
> It doesn't download in (/var/cache/apt/archives/) any .deb package file.

But it download them somewhere.Put all debs in one folder and name folder as you wish.Go inside that folder and then

```
sudo cp *deb /var/cache/apt/archives
```

From synaptic install **aptoncd** and make iso from your /var/cache/apt/archives.Burn iso to the cd/dvd and put in in second comp.More info about aptoncd you can find [here.]("http://aptoncd.sourceforge.net/")

---

### Post by isaacrc82 on 2008-12-23
> But it download them somewhere. Where ???
How do I search in all the file system for all the .deb files ???

Greetings
Ariel

---

### Post by jonlemur on 2009-01-11
Sorry if this is too late, but to search the entire filesystem for all .deb packages, you can use ```
sudo find / -name *.deb
```

---


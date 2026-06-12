---
title: "Broken Dependiencies"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by Defib on 2009-07-07
I was installing the package 'Reconstructor' today and I had a powersurge. Upon rebooting I was given this error:

Your system has broken dependencies. This application cannot continue until this is fixed. To fix it run 'sudo apt-get install -f'.

Here is the output of apt-get install -f

```
craig@craig-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  g++-4.3 libgd2-noxpm
Suggested packages:
  g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg libgd-tools
The following NEW packages will be installed:
  libgd2-noxpm
The following packages will be upgraded:
  g++-4.3
1 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 0B/4371kB of archives.
After this operation, 9785kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `g++-4.3' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

note: sudo apt-get install -f and sudo apt-get -f install are the same thing.


Any suggestions as what to do? I've already done these to no avail:
sudo dpkg configure g++-4.3
sudo dpkg-reconfigure -a
sudo apt-get clean
sudo apt-get update

---

### Post by washakie on 2009-07-07
try removing any reference to the packages from:

/var/cache/apt/archive

/etc/init.d/
/etc/rc2.d/

Make sure to back up the files! You can just simply cp them somewhere... but if all goes well, you won't need them again. Also, obviously you have to do this as root.

---

### Post by Defib on 2009-07-07
I'm not quite sure what you want me to do. I'm not a super newb but I need a bunch of guidance.

---

### Post by Soul-Sing on 2009-07-07
try: 
```
sudo dpkg --clean-avail
```
```
sudo apt-get update
```

---

### Post by washakie on 2009-07-07
> **Defib said:**
> I'm not quite sure what you want me to do. I'm not a super newb but I need a bunch of guidance.

Okay, I would do the following:

first:
```

sudo su
cd /var/cache/apt/archive
mkdir /opt/temp
mv g++* /opt/temp/.

```

Now try again, I think it would be best to use aptitude:
sudo aptitude -u

I'm thinking now the references to /etc/init.d are not probably as relevant in your case, as g++ isn't a service. I had the problem for cups, which is a service, so it wouldn't install until I removed the /etc/init.d/ scripts for cups.

---

### Post by Defib on 2009-07-07
> **leoquant said:**
> try: 
```
sudo dpkg --clean-avail
```
```
sudo apt-get update
```

```
craig@craig-desktop:~$ sudo dpkg --clean-avail
[sudo] password for craig: 
dpkg: unknown option --clean-avail
```


```
root@craig-desktop:/home/craig# cd /var/cache/apt/archive
bash: cd: /var/cache/apt/archive: No such file or directory

```


and aptitude didn't help at all....

---

### Post by washakie on 2009-07-07
> **Defib said:**
> 
```
root@craig-desktop:/home/craig# cd /var/cache/apt/archive
bash: cd: /var/cache/apt/archive: No such file or directory

```


and aptitude didn't help at all....


```

cd /var/cache/apt/archives

```

Look in there for any references to g++, move them to a backup location so that you force apt to redownload the package files... maybe there's a better way to do this, but this is what eventually worked for me.

---

### Post by Defib on 2009-07-07
So all that's doing is making apt redownload g++? I've already run through that using 'apt-get clean'. I was in the IRC before and someone said that the package ubuntu has is corrupted. And I can't download and install a .deb because synamptic has a hissy fit because of the broken package...


But I did what you suggested and it didn't work at all.

---

### Post by washakie on 2009-07-07
Sorry, that's all I've got...

---

### Post by Defib on 2009-07-09
If this helps anyone; [http://www.pastebin.org/769](http://www.pastebin.org/769)

---

### Post by Soul-Sing on 2009-07-09
navigate via ```
gksudo nautilus
``` to:
/var/lib/dpkg/info/g++-4.3 delete broken files, you can "search" them.

```
sudo apt-get install g++-4.3 --reinstall
```

```
sudo apt-get update
```

---

### Post by Defib on 2009-07-09
I couldn't navigate to /var/lib/dpkg/info/g++-4.3 

It doesn't exist.

---

### Post by Defib on 2009-07-09
Just kidding, I got it fixed! Thanks so much!

---

### Post by Soul-Sing on 2009-07-09
> **Defib said:**
> Just kidding, I got it fixed! Thanks so much!

?

---

### Post by Defib on 2009-07-09
I had to search for it and I found the two files that were messing everthing up. Deleted and did what you said!

---


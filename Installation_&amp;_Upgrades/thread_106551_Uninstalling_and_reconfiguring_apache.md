---
title: "Uninstalling and reconfiguring apache"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by harisund on 2005-12-20
Why is that even after I do 

apt-get --purge remove apache2
apt-get install apache2 

or even after
dpkg-reconfigure apache2

I still find that my /etc/apache2 folder is unchanged? I made a lot of experimental changes, and now want the default configuration back... how do I get that? 

Thanks !

---

### Post by Gandalf on 2005-12-20
well because /etc/apache2 folder is installed by apache2-common package and not apache2 package, so do 
```
sudo dpkg-reconfigure apache2-common
```

TIP: next time you can find out easly as i did now, do
```

sudo apt-get install apt-file
sudo apt-file update

```

and to find out in which package is the folder/file you do
```

apt-file search filename

OR

apt-file search /path/to/folder

```

---

### Post by harisund on 2005-12-20
I am amazed.. a million thanks.. 

Now that you brought it up, I think some switch in the dpkg command line option does the same thing.

Thanks again !

Hari

UPDATE: dpkg -S /etc/apache2 returns the same result.

---

### Post by Gandalf on 2005-12-21
you're welcome and Thanks for the tip :)

---


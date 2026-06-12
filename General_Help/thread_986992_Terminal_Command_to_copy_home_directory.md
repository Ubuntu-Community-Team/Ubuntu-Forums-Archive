---
title: "Terminal Command to copy home directory"
date: 2008-11-19
forum: General Help
---

### Post by Tobywuk on 2008-11-19
Hello, 

Im trying to copy 100% of my home directory (including .xxxx files and all subfolders) to an external drive. What command would I need to use?

I tried:  cp -arv /source /Destination   but terminal is not liking this format.

I want to copy all the files(including hidden), all the directory tree and im trying to get it in verbos mode so i can see whats going on throughout.

I am actually using my mac os x system for this but im sure its the same command as ubuntu.

thanks.

---

### Post by philinux on 2008-11-19
Last time I tried that I think I used a capital R.

---

### Post by eder.apt-get on 2008-11-19
Maybe you should tar your copy, in case your home is too big:
In the console type 
tar cf eder.apt-get_home.tar  /home/eder.apt-get >> In my case.

Using -R makes it act recursively.

to extract 
tar xf <new_dir_name>.tar

Here is more tips:[http://en.wikipedia.org/wiki/Cp_(Unix)]("http://en.wikipedia.org/wiki/Cp_%28Unix%29")

---

### Post by Tobywuk on 2008-11-19
the -R works but does that copy all the files (including hidden)?

Im just after the options i need for the cp command so all my files will be copied.


I dont want to compress the backup its <200gb from a laptop hard drive and the external drive is big enough. I have cp -R -V   going at the moment and it seems to be working but i just want to double check

---

### Post by cashmoney on 2008-11-19
rsynch is what you want to use.. but I always do

> Man rsynch first to get an idea on what options do what.

```
sudo rsync -avxP /home/ncash /mnt/sdb1/nate_home
```

---

### Post by Tobywuk on 2008-11-21
Thanks for all the replies. 

Rsync is exactly what im after, i have it all set up and working using an alias so back ups are made nice and easily to an encrypted external drive.

---


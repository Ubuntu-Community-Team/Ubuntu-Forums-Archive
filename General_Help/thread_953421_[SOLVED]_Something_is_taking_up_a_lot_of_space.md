---
title: "[SOLVED] Something is taking up a lot of space"
date: 2008-10-20
forum: General Help
---

### Post by pivot@pivpoint.no on 2008-10-20
I've had some trouble with my xubuntu 7.10 because of low disk space. I've checked my home dir, and thats not what's taking up the space. I've uninstalled a lot of programs too, and actually never had a lot of programs on it in the first place since its basicly a download- and fileserver.

Of couse, trash is empty and all that. Is there some place I should look for temporary files n such that might fill up the drive?

Right now, the OS, including a 5gb home dir takes up 69gb (which is almost 100% of my 10 000 rpm main disk).

I'm happy for any suggestions :)

---

### Post by geirha on 2008-10-20
In ubuntu you have Applications -> Accessories -> Disk Usage Analyzer. You might have that app in xubuntu too.

If you like the terminal though, try
```
sudo du -h -x --max-depth=1 /
```

---

### Post by /////// on 2008-10-20
sudo apt-get autoremove && sudo apt-get clean

---

### Post by Kevbert on 2008-10-20
Please take a look at [COLOR="Red"][this.]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")[/COLOR]

---

### Post by pivot@pivpoint.no on 2008-10-20
Tnx guys!
Used some of your suggestions and found some files within /var/backup that took up a lot of storage. Guess Simple Backup is the reason, and it was a man made fault - not a OS fault :)

---


---
title: "update manager problem"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by ToastyMallows on 2009-07-30
Ok so I have a little red X in my Panel and when I hover over it is says "Problem occured when checking for updates."

I saw another thread that told me to delete the file .gksu.lock from the home directory, I did that and it didn't help.

My output when running sudo apt-get update && sudo apt-get upgrade through the terminal is;

```
ross@ross-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Segmentation faulty tree... 50%
```

And then nothing else happens.  Does anyone else have this problem?  Can anyone else think of another solution or workaround?  Is this a bug?

---

### Post by Partyboi2 on 2009-07-31
Hi, try removing  the bin files in /var/cache/apt
```
sudo  rm /var/cache/apt/*.bin
```
Then run ```
sudo apt-get update
```
to regenerate the files and then finally try upgrading again.

---

### Post by ToastyMallows on 2009-07-31
> **Partyboi2 said:**
> Hi, try removing  the bin files in /var/cache/apt
```
sudo  rm /var/cache/apt/*.bin
```
Then run ```
sudo apt-get update
```
to regenerate the files and then finally try upgrading again.

That did the trick thank you so much.

---

### Post by slotto on 2009-12-23
Thanks!!!

---


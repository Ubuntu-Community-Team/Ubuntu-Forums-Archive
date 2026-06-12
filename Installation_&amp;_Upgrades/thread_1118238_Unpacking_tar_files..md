---
title: "Unpacking tar files."
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by CasPol on 2009-04-06
Hi there;

I have been using ubuntu for a while now, and keep having difficulty with unpacking and installing "tar files".

It would be great if someone could help me by giving a step - by step instruction on how to do this. I have read a lot , but find it all very confusing. How do I unpack a tar file after I have downloaded it ?

Thanks !!

---

### Post by Partyboi2 on 2009-04-06
If you wan the Gui way you can right click on the file and choose to extract it. Or you can open a terminal and change into the directory where the .tar file is with 'cd' then  for a tar.gz
```
tar xvzf packagename
``` or if you happen to have a tar.bz to unpack you can use
```
tar xvjf packagename
```So if you had a tar file called abc.tar.gz  on your Desktop you would
```
cd ~/Desktop
```then
```
tar xvzf abc.tar.gz
```

---

### Post by logos34 on 2009-04-06
for the installing part, there's these step-by-step howtos:

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---


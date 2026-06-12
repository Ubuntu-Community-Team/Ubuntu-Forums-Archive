---
title: "How do I install texlive 2008 from an iso file?"
date: 2008-11-09
forum: General Help
---

### Post by ali780 on 2008-11-09
Hello every body.
I have downloaded texlive 2008 and I mounted it on my laptop, But I dont know how can I install it. please somebody tell how can I do it?
I use Ubuntu 8.10 6 bit on my lapyop.
Thanks

---

### Post by bwhite82 on 2008-11-09
[http://www.tug.org/texlive/quickinstall.html](http://www.tug.org/texlive/quickinstall.html)

Looks like it has an install script, invoked from the command line. First CD to the downloaded directory, then:

> sudo ./install-tl

---

### Post by metricspace on 2009-09-01
Hi 

when i gave the command
> sudo install-tl

I got the following err.

> sudo: install-tl: command not found

I was inside the texlive directory when i gave the above command, Please assist need to install the distribution from the downloaded iso.

Regards,
metric

---

### Post by Vaphell on 2009-09-01
you have to use full path unless you want to run something that is somewhere in the system dirs (system will try to find your app there)

in your case sudo ./install-tl  (. = current dir)

---

### Post by eumetaxas on 2009-09-01
take a look at this post.
[http://ubuntuforums.org/showthread.php?t=1106025](http://ubuntuforums.org/showthread.php?t=1106025)

you may find some answers

---

### Post by metricspace on 2009-09-02
Thanks  for your responses, 

still am unable to execute the commad

My TeXLive directory is on my **Desktop** in a **tmp** folder , when I navigate inside texlive directory my command prompt looks like 
**~/Desktop/tmp/texlive2008**.

from there I key in the command ```
sudo ./install-tl
``` I also tried ```
sudo ~/Desktop/tmp/texlive2008 ./install-tl
```, the response was 

```
sudo: /home/arif/Desktop/tmp/texlive2008: command not found
```Thanks for the link, It also said to use the same command, the one which i have used, but am unable to execute it.

Please assist, 

Regards,
metric

---

### Post by XCan on 2009-09-02
Wouldn't your second command rather be
```
 sudo ~/Desktop/tmp/texlive2008/install-tl 
```
make sure you've enabled the executable flag on it.

Regardless, I think it would help us all if you can't get the above to work to post the output of ```
 ls -l ~/Desktop/tmp/texlive2008/ 
```

---

### Post by metricspace on 2009-09-04
Thanks for the reply 
```
sudo ~/Desktop/tmp/texlive2008/install-t 
```
now gave me the following reponse

 [http://pastebin.ubuntu.com/264873/](http://pastebin.ubuntu.com/264873/)

 andthe response for 
```
ls -l ~/Desktop/tmp/texlive2008/
```
was  this [http://pastebin.ubuntu.com/264874/](http://pastebin.ubuntu.com/264874/), 

Thank you once again for the help,
metric

---

### Post by XCan on 2009-09-04
Check the permission of ```
 ~/Desktop/tmp/texlive2008/tlpkg/installer/lzma/lzmadec.i386-linux 
```

does it exist? Is it executable (flag)?

---

### Post by metricspace on 2009-09-06
yes the file exist, executing 
```
ls -l ~/Desktop/tmp/texlive2008/tlpkg/installer/lzma/lzmadec.i386-linux

``` gives me 

**-rw-r--r-- 1 arif arif 10032 2008-05-21 04:48 /home/arif/Desktop/tmp/texlive2008/tlpkg/installer/lzma/lzmadec.i386-linux**

Please assist, 
metric

---

### Post by XCan on 2009-09-06
Try setting the executable flag on it ```
 chmod +x ~/Desktop/tmp/texlive2008/tlpkg/installer/lzma/lzmadec.i386-linux 
```

---

### Post by metricspace on 2009-09-06
Thank you so much, Texlive got installed on my Linux box. 
I tried installing kile from synaptic mgr, however it says dependencies need to be installed and the total download would be around 350MB. 

I don't know why still some tex-live files are shown in dependencies, and why 350 MB is to be still download, if kile is less than 2MB. 

I have a very less band width quota, hence i downloaded TexLive from some where else and installed it on my linux box. 

Thank you once again, any hint on the above queries is really appreciated.

Regards,
metric

---

